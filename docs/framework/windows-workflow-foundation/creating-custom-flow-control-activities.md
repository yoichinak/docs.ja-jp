---
title: カスタムのフロー制御アクティビティの作成
ms.date: 03/30/2017
ms.assetid: 27f409f6-2d1d-4cfb-9765-93eb2ad667d5
ms.openlocfilehash: 8e7d4caad197631509fe80a5b5a08eff4d228c1c
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989728"
---
# <a name="creating-custom-flow-control-activities"></a>カスタムのフロー制御アクティビティの作成
.NET Framework には、抽象プログラミング構造 ( <xref:System.Activities.Statements.Flowchart>など) または標準のプログラミングステートメント ( <xref:System.Activities.Statements.If>など) と同様に機能するさまざまなフロー制御アクティビティが含まれています。 このトピックでは、一般的では[ない ForEach](./samples/non-generic-foreach.md)のサンプルプロジェクトのアーキテクチャについて説明します。  
  
## <a name="creating-the-custom-class"></a>カスタム クラスの作成  
 非ジェネリックの ForEach クラスは子アクティビティをスケジュールする必要があるため、<xref:System.Activities.NativeActivity> から派生する必要があります。<xref:System.Workflow.Activities.CodeActivity> から派生したアクティビティにはこの機能がありません。  
  
```csharp  
public sealed class ForEach : NativeActivity  
{
}
```  
  
 カスタム クラスには、アクティビティによって使用されているデータを格納し、アクティビティの子アクティビティを実行する機能を提供するためのいくつかのメンバーが必要です。 そのメンバーには以下が含まれます。  
  
- `valueEnumerator`:項目のコレクションを<xref:System.Activities.Variable%601>反復処理<xref:System.Collections.IEnumerator>するために使用される型の非パブリック。 このメンバーは引数またはパブリック プロパティではなく、アクティビティで内部的に使用されるため、<xref:System.Activities.Variable%601> 型となり、このオブジェクトの発生元がアクティビティの外部にある場合に使用されます。  
  
- `OnChildComplete`:各子<xref:System.Activities.CompletionCallback>要素の実行が完了したときに実行されるパブリックプロパティ。 このメンバーは、アクティビティの異なるインスタンスごとに値が変わらないため、CLR プロパティとして定義されています。  
  
- `Values`:子アクティビティの反復処理に使用される入力のコレクション。 このメンバーは、データの発生元がアクティビティの外部にあり、アクティビティの実行中にコレクションの内容の変更が想定されないため、<xref:System.Activities.InArgument%601> 型です。 アクティビティの実行中に、アクティビティ (たとえば、追加または削除) のためにこのコレクションの内容を変更する機能が必要な場合、このメンバーは <xref:System.Activities.ActivityAction> として定義されます。この場合、メンバーはアクセスするたびに評価され、変更をアクティビティに反映できます。  
  
- `Body` :このメンバーは、 `Values`コレクション内の各項目に対して実行されるアクティビティを定義します。 このメンバーは、アクセスするたびに評価されるように <xref:System.Activities.ActivityAction> として定義されます。  
  
- `Execute`:このメソッドは`InternalExecute`、、 `OnForEachComplete`、および`GetStateAndExecute`非パブリックメンバーを使用して実行をスケジュールし、Body メンバーで定義されている子アクティビティの完了ハンドラーを割り当てます。  
  
- `CacheMetadata` :このメンバーは、アクティビティを実行するために必要な情報をランタイムに提供します。 既定では、アクティビティの `CacheMetadata` メソッドはランタイムにアクティビティのすべてのパブリック メンバーを通知しますが、このアクティビティは一部の機能にプライベート メンバーを使用するため、ランタイムにプライベート メンバーの存在を通知して認識されるようにする必要があります。 この場合、`CacheMetadata` 関数はオーバーライドされ、プライベートの `valueEnumerator` メンバーにアクセスできるようにします。 このメンバーはアクティビティの値の引数も作成し、実行時にアクティビティに渡すことができるようにします。
