---
title: カスタムのフロー制御アクティビティの作成
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: f457e6f8cefd7183ca20cb449adf1ac15d7bde79
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647142"
---
# <a name="creating-custom-flow-control-activities"></a>カスタムのフロー制御アクティビティの作成
.NET Framework には、さまざまなプログラミング構造を抽象化するために同様に機能するフロー制御アクティビティが含まれています (など<xref:System.Activities.Statements.Flowchart>) または標準的なプログラミング ステートメント (など<xref:System.Activities.Statements.If>)。 このトピックでは、サンプル プロジェクトのいずれかのアーキテクチャを説明[非ジェネリックの ForEach](./samples/non-generic-foreach.md)します。  
  
## <a name="creating-the-custom-class"></a>カスタム クラスの作成  
 非ジェネリックの ForEach クラスは子アクティビティをスケジュールする必要があるため、<xref:System.Activities.NativeActivity> から派生する必要があります。<xref:System.Workflow.Activities.CodeActivity> から派生したアクティビティにはこの機能がありません。  
  
```  
public sealed class ForEach : NativeActivity  
    {  
```  
  
 カスタム クラスには、アクティビティによって使用されているデータを格納し、アクティビティの子アクティビティを実行する機能を提供するためのいくつかのメンバーが必要です。 そのメンバーには以下が含まれます。  
  
- `valueEnumerator`:非パブリック<xref:System.Activities.Variable%601>型の<xref:System.Collections.IEnumerator>項目のコレクションを反復処理するために使用します。 このメンバーは引数またはパブリック プロパティではなく、アクティビティで内部的に使用されるため、<xref:System.Activities.Variable%601> 型となり、このオブジェクトの発生元がアクティビティの外部にある場合に使用されます。  
  
- `OnChildComplete`:パブリック<xref:System.Activities.CompletionCallback>それぞれの子には、実行が完了したときに実行されるプロパティ。 このメンバーは、アクティビティの異なるインスタンスごとに値が変わらないため、CLR プロパティとして定義されています。  
  
- `Values`:子アクティビティのイテレーションのために使用される入力のコレクション。 このメンバーは、データの発生元がアクティビティの外部にあり、アクティビティの実行中にコレクションの内容の変更が想定されないため、<xref:System.Activities.InArgument%601> 型です。 アクティビティの実行中に、アクティビティ (たとえば、追加または削除) のためにこのコレクションの内容を変更する機能が必要な場合、このメンバーは <xref:System.Activities.ActivityAction> として定義されます。この場合、メンバーはアクセスするたびに評価され、変更をアクティビティに反映できます。  
  
- `Body`:このメンバーの各項目に対して実行されるアクティビティの定義、`Values`コレクション。 このメンバーは、アクセスするたびに評価されるように <xref:System.Activities.ActivityAction> として定義されます。  
  
- `Execute`:このメソッドを使用して、 `InternalExecute`、 `OnForEachComplete`、および`GetStateAndExecute`非パブリック メンバーが実行をスケジュールして、Body メンバーに定義された子アクティビティの完了ハンドラーを割り当てます。  
  
- `CacheMetadata`:このメンバーは、アクティビティの実行に必要な情報と、ランタイムを提供します。 既定では、アクティビティの `CacheMetadata` メソッドはランタイムにアクティビティのすべてのパブリック メンバーを通知しますが、このアクティビティは一部の機能にプライベート メンバーを使用するため、ランタイムにプライベート メンバーの存在を通知して認識されるようにする必要があります。 この場合、`CacheMetadata` 関数はオーバーライドされ、プライベートの `valueEnumerator` メンバーにアクセスできるようにします。 このメンバーはアクティビティの値の引数も作成し、実行時にアクティビティに渡すことができるようにします。
