---
title: 例外
ms.date: 03/30/2017
ms.assetid: 065205cc-52dd-4f30-9578-b17d8d113136
ms.openlocfilehash: 64a8338133c265ee1b4c7acbd9b4d168318b66a5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61773634"
---
# <a name="exceptions"></a>例外
ワークフローは、<xref:System.Activities.Statements.TryCatch> アクティビティを使用して、ワークフローの実行中に発生した例外を処理することができます。 これらの例外は、処理することも可能ですが、<xref:System.Activities.Statements.Rethrow> アクティビティを使用して再スローすることもできます。 <xref:System.Activities.Statements.TryCatch.Finally%2A> セクションのアクティビティは、<xref:System.Activities.Statements.TryCatch.Try%2A> セクションまたは <xref:System.Activities.Statements.TryCatch.Catches%2A> セクションが完了したときに実行されます。 によってホストされるワークフローを<xref:System.Activities.WorkflowApplication>インスタンスを使用することも、<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>によって処理されない例外を処理するイベント ハンドラーを<xref:System.Activities.Statements.TryCatch>アクティビティ。  
  
## <a name="causes-of-exceptions"></a>例外の原因  
 ワークフローでは、例外は、次の方法で生成されます。  
  
- <xref:System.Activities.Statements.TransactionScope> でのトランザクションのタイムアウト  
  
- <xref:System.Activities.Statements.Throw> アクティビティを使用してワークフローからスローされた明示的な例外  
  
- アクティビティからスローされた [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 例外  
  
- ワークフローで使用されているライブラリ、コンポーネント、サービスなどの外部コードからスローされた例外  
  
## <a name="handling-exceptions"></a>例外処理  
 アクティビティからスローされた例外が処理されない場合、既定の動作では、ワークフロー インスタンスが終了します。 カスタムの <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> ハンドラーが存在する場合、このハンドラーで既定の動作をオーバーライドできます。 このハンドラーがあると、ワークフロー ホストの作成者は、カスタムのログ記録、ワークフローの中止、ワークフローのキャンセル、ワークフローの終了などの適切な処理を実行できます。  ワークフローが処理されない例外を発生する場合、<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> ハンドラーが呼び出されます。 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> から戻された 3 つの可能なアクションがあり、これによりワークフローの最終結果が決定されます。  
  
- **キャンセル**-キャンセルされたワークフロー インスタンスは分岐実行の正常な終了します。 キャンセルの動作をモデル化できます (たとえば、CancellationScope アクティビティを使用して)。 完了済みハンドラーはキャンセル プロセスが完了したときに呼び出されます。 取り消されたワーク フローはキャンセル状態にあります。  
  
- **終了**-終了したワークフロー インスタンスは再開または再起動することはできません。  これにより完了イベントがトリガーされ、中断されたという理由の例外を提供できます。 終了したハンドラーはキャンセル プロセスが終了したときに呼び出されます。 終了したワークフローは失敗状態です。  
  
- **中止**-永続的に構成されている場合にのみ、中止されたワークフロー インスタンスを再開できます。  永続化がない場合、ワークフローは再開できません。  ワークフローが中止したポイントで、最後の永続性ポイントが失われるため (メモリ内で)、どの作業も終了します。 中止されたワーク フローに対して、中止プロセスが完了したときの例外を使用して、中止されたハンドラーが呼び出されます。 しかし、キャンセルおよび終了と異なり、完了ハンドラーは呼び出されません。 中止されたワーク フローが中断状態にあります。  
  
 次の例では、例外をスローするワークフローを呼び出しています。 ワークフローで例外が処理されないため、<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> ハンドラーが呼び出されます。 例外に関する情報を提供するために <xref:System.Activities.WorkflowApplicationUnhandledExceptionEventArgs> が調査され、ワークフローは終了します。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#1](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#1)]  
  
### <a name="handling-exceptions-with-the-trycatch-activity"></a>TryCatch アクティビティでの例外処理  
 ワークフロー内部での例外処理は、<xref:System.Activities.Statements.TryCatch> アクティビティで実行されます。 <xref:System.Activities.Statements.TryCatch> アクティビティには、それぞれが特定の <xref:System.Activities.Statements.TryCatch.Catches%2A> 型に関連付けられている <xref:System.Activities.Statements.Catch> アクティビティの <xref:System.Exception> コレクションがあります。 <xref:System.Activities.Statements.TryCatch.Try%2A> アクティビティの <xref:System.Activities.Statements.TryCatch> セクションに含まれているアクティビティからスローされた例外が、<xref:System.Activities.Statements.Catch%601> コレクションの <xref:System.Activities.Statements.TryCatch.Catches%2A> アクティビティの例外に一致する場合、スローされた例外が処理されます。 例外が明示的に再スローされるか、新しい例外がスローされた場合、この例外は親アクティビティに渡されます。 次のコード例は、<xref:System.Activities.Statements.TryCatch> セクションで <xref:System.ApplicationException> アクティビティからスローされた <xref:System.Activities.Statements.TryCatch.Try%2A> を処理する <xref:System.Activities.Statements.Throw> アクティビティを示しています。 例外のメッセージが <xref:System.Activities.Statements.Catch%601> アクティビティによってコンソールに書き込まれた後、<xref:System.Activities.Statements.TryCatch.Finally%2A> セクションでメッセージがコンソールに書き込まれます。  
  
 [!code-csharp[CFX_WorkflowApplicationExample#33](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#33)]  
  
 <xref:System.Activities.Statements.TryCatch.Finally%2A> セクションのアクティビティは、<xref:System.Activities.Statements.TryCatch.Try%2A> セクションまたは <xref:System.Activities.Statements.TryCatch.Catches%2A> セクションが正常に完了したときに実行されます。 例外がスローされない場合 <xref:System.Activities.Statements.TryCatch.Try%2A> セクションは正常に完了し、例外がスローまたは再スローされない場合 <xref:System.Activities.Statements.TryCatch.Catches%2A> セクションは正常に完了します。 例外が <xref:System.Activities.Statements.TryCatch.Try%2A> の <xref:System.Activities.Statements.TryCatch> セクションでスローされ、<xref:System.Activities.Statements.Catch%601> セクションの <xref:System.Activities.Statements.TryCatch.Catches%2A> で処理されないか、または <xref:System.Activities.Statements.TryCatch.Catches%2A> から再スローされる場合、<xref:System.Activities.Statements.TryCatch.Finally%2A> のアクティビティは以下のいずれかが発生しない限り実行されません。  
  
- 高レベルの <xref:System.Activities.Statements.TryCatch> から再スローされるかにかかわらず、例外がワーク フローの高レベルの <xref:System.Activities.Statements.TryCatch> アクティビティによって取得されます。  
  
- 例外は高レベルの <xref:System.Activities.Statements.TryCatch> では扱われず、ワークフローのルートをエスケープし、ワーク フローが完了または中止ではなく取り消すように構成されます。 <xref:System.Activities.WorkflowApplication> を使用してホストされたワークフローは、<xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> を処理し <xref:System.Activities.UnhandledExceptionAction.Cancel> を返してこれを構成できます。 <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A> を処理する例は、このトピックで既に提供されています。 ワークフロー サービスは <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior> を使用し <xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionAction.Cancel> を指定してこれを構成できます。 構成の例については<xref:System.ServiceModel.Activities.Description.WorkflowUnhandledExceptionBehavior>を参照してください[ワークフロー サービス ホストの拡張機能](../wcf/feature-details/workflow-service-host-extensibility.md)します。  
  
## <a name="exception-handling-versus-compensation"></a>例外処理と補正の比較  
 例外処理は、アクティビティの実行中に発生するという点で補正と異なります。 補正が発生するのは、アクティビティが正常に完了した後です。 例外処理では、アクティビティが例外を生成した後でクリーン アップを実行できます。また、補正処理では、前に完了したアクティビティの正常に完了した作業を元に戻すことが可能です。 詳細については、次を参照してください。[補正](compensation.md)します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Activities.Statements.TryCatch>
- <xref:System.Activities.WorkflowApplication.OnUnhandledException%2A>
- <xref:System.Activities.Statements.CompensableActivity>
