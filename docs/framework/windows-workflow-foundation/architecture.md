---
title: Windows Workflow のアーキテクチャ
ms.date: 03/30/2017
ms.assetid: 1d4c6495-d64a-46d0-896a-3a01fac90aa9
ms.openlocfilehash: 5d6e1ead9184bfb61eb466389671ca2e74264ae3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723743"
---
# <a name="windows-workflow-architecture"></a>Windows Workflow のアーキテクチャ
Windows Workflow Foundation (WF) では、対話型の実行時間の長いアプリケーションを開発するための抽象化レベルを上げます。 作業単位はアクティビティとしてカプセル化されます。 アクティビティが実行される環境には、フロー制御、例外処理、エラー伝達、状態データの永続化、動作中のワークフローのメモリへの読み込みやアンロード、追跡、トランザクション フローに対応する機能が備わっています。  
  
## <a name="activity-architecture"></a>アクティビティのアーキテクチャ  
 アクティビティは、<xref:System.Activities.Activity>、<xref:System.Activities.CodeActivity>、<xref:System.Activities.AsyncCodeActivity>、または <xref:System.Activities.NativeActivity> から派生する CLR 型として開発されたり、値 <xref:System.Activities.Activity%601>、<xref:System.Activities.CodeActivity%601>、<xref:System.Activities.AsyncCodeActivity%601>、または <xref:System.Activities.NativeActivity%601> を返す CLR 型の変化形として開発されます。 <xref:System.Activities.Activity> から派生するアクティビティを開発すると、ユーザーは既存のアクティビティを組み合わせてワークフロー環境で実行される作業単位をすばやく作成できます。 一方、<xref:System.Activities.CodeActivity> では、主にアクティビティ引数にアクセスするために <xref:System.Activities.CodeActivityContext> を使用してマネージ コードで作成される実行ロジックが有効になります。 <xref:System.Activities.AsyncCodeActivity> は、非同期タスクを実装するために使用できること以外の点で <xref:System.Activities.CodeActivity> に似ています。 <xref:System.Activities.NativeActivity> から派生するアクティビティを開発すると、<xref:System.Activities.NativeActivityContext> を通じてランタイムにアクセスし、子のスケジュール設定、ブックマーク作成、非同期の作業の呼び出し、トランザクションの登録などの機能を使用できます。  
  
 <xref:System.Activities.Activity> から派生するアクティビティの作成は宣言型です。また、これらのアクティビティは XAML で作成できます。 次の例では、`Prompt` というアクティビティが、実行の本体用に他のアクティビティを使用して作成されます。  
  
```xml  
<Activity x:Class='Prompt'  
  xmlns:x='http://schemas.microsoft.com/winfx/2006/xaml'  
    xmlns:z='http://schemas.microsoft.com/netfx/2008/xaml/schema'  
xmlns:my='clr-namespace:XAMLActivityDefinition;assembly=XAMLActivityDefinition'  
xmlns:s="clr-namespace:System;assembly=mscorlib"  
xmlns="http://schemas.microsoft.com/2009/workflow">  
<z:SchemaType.Members>  
    <z:SchemaType.SchemaProperty Name='Text' Type=' InArgument(s:String)' />  
  <z:SchemaType.SchemaProperty Name='Response' Type='OutArgument(s:String)' />  
</z:SchemaType.Members>  
  <Sequence>  
    <my:WriteLine Text='[Text]' />  
    <my:ReadLine BookmarkName='r1' Result='[Response]' />  
  </Sequence>  
</Activity>  
```  
  
## <a name="activity-context"></a>アクティビティ コンテキスト  
 <xref:System.Activities.ActivityContext> は、アクティビティ作成者のワークフロー ランタイムへのインターフェイスであり、ランタイムのさまざまな機能にアクセスできます。 次の例では、ブックマーク (データをアクティビティに渡してホストが再開できる、実行の継続点をアクティビティが登録できる方法) を作成する実行コンテキストを使用するアクティビティが定義されています。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#15](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#15)]  
  
## <a name="activity-life-cycle"></a>アクティビティ ライフ サイクル  
 アクティビティのインスタンスは <xref:System.Activities.ActivityInstanceState.Executing> 状態で開始します。 例外が検出された場合を除き、すべての子アクティビティが実行を終了し、他の保留中の作業 (<xref:System.Activities.Bookmark> オブジェクトなど) が完了するまでこの状態が維持されてから、<xref:System.Activities.ActivityInstanceState.Closed> 状態に移行します。 アクティビティ インスタンスの親は子にキャンセルを要求できます。子がキャンセル可能な場合、子は <xref:System.Activities.ActivityInstanceState.Canceled> 状態で完了します。 実行中に例外がスローされた場合は、ランタイムはアクティビティを <xref:System.Activities.ActivityInstanceState.Faulted> 状態にし、アクティビティの親チェーンの上方向へ例外を伝達します。 アクティビティの 3 つの完了状態を次に示します。  
  
-   **終了。** アクティビティが作業を完了し、終了しました。  
  
-   **取り消されました。** アクティビティが適切に作業を破棄し、終了します。 この状態に移行した場合、作業は明示的にロール バックされません。  
  
-   **エラーが発生しました。** アクティビティは、エラーが発生しましたおり、作業を完了せずに終了しました。  
  
 アクティビティは、永続化またはアンロードされても <xref:System.Activities.ActivityInstanceState.Executing> 状態を維持します。
