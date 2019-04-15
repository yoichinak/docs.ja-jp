---
ms.openlocfilehash: 5850e3359dab6503d5745a2266c7bf77780e5cc0
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760887"
---
### <a name="avoiding-endless-recursion-for-iworkflowinstancemanagementtransactedcancel-and-iworkflowinstancemanagementtransactedterminate"></a>IWorkflowInstanceManagement.TransactedCancel および IWorkflowInstanceManagement.TransactedTerminate の無限再帰の回避

|   |   |
|---|---|
|説明|<xref:System.ServiceModel.Activities.IWorkflowInstanceManagement.TransactedCancel%2A?displayProperty=nameWithType> または <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement.TransactedTerminate%2A?displayProperty=nameWithType> API を使用してワークフロー サービス インスタンスを取り消すか終了するとき、状況によっては、<code>Workflow</code> ランタイムが要求の処理の一部としてサービス インスタンスの永続化を試みるときの無限再帰のために、ワークフロー インスタンスでスタック オーバーフローが発生する可能性があります。 問題は、別のサービスに対する他の未処理 WCF 要求が完了するのをワークフロー インスタンスが待機している状態の場合に発生します。<code>TransactedCancel</code> および <code>TransactedTerminate</code> 操作は、ワークフロー サービス インスタンスのキューに登録される作業項目を作成します。 これらの作業項目は、<code>TransactedCancel/TransactedTerminate</code> 要求の処理の一部としては実行されません。 ワークフロー サービス インスタンスは他の未処理 WCF 要求が完了するのを待ってビジー状態であるため、作成された作業項目はキューに残ります。 <code>TransactedCancel/TransactedTerminate</code> 操作が完了して、クライアントに制御が返されます。 <code>TransactedCancel/TransactedTerminate</code> 操作に関連付けられているトランザクションは、コミットしようとした場合、ワークフロー サービス インスタンスの状態を永続化する必要があります。 しかし、インスタンスには未処理の <code>WCF</code> 要求があるため、ワークフロー ランタイムはワークフロー サービス インスタンスを永続化できず、無限再帰ループによってスタックがオーバーフローします。<code>TransactedCancel</code> と <code>TransactedTerminate</code> はメモリ内にのみ作業項目を作成するので、トランザクションが存在してもまったく影響ありません。 トランザクションのロールバックは作業項目を破棄しません。この問題に対処するため、.NET Framework 4.7.2 以降では、ワークフロー サービスの <code>web.config/app.config</code> に追加できる <code>AppSetting</code> が導入されています。これは、<code>TransactedCancel</code> および <code>TransactedTerminate</code> のトランザクションを無視するようにサービスに指示します。 これにより、トランザクションはワークフロー インスタンスの永続化を待たずにコミットできます。この機能の AppSetting の名前は <code>microsoft:WorkflowServices:IgnoreTransactionsForTransactedCancelAndTransactedTerminate</code> です。 値 <code>true</code> はトランザクションを無視することを示し、したがってスタック オーバーフローが回避されます。 この AppSetting の既定値は <code>false</code> なので、既存のワークフロー サービス インスタンスに影響はありません。|
|提案される解決策|AppFabric または別の <xref:System.ServiceModel.Activities.IWorkflowInstanceManagement> クライアントを使っていて、ワークフロー インスタンスを取り消すか終了しようとするとワークフロー サービス インスタンスでスタック オーバーフローが発生する場合は、ワークフロー サービスの web.config/app.config ファイルの <code>&lt;appSettings&gt;</code> セクションに以下を追加できます。<pre><code class="lang-xml">&lt;add key=&quot;microsoft:WorkflowServices:IgnoreTransactionsForTransactedCancelAndTransactedTerminate&quot; value=&quot;true&quot;/&gt;&#13;&#10;</code></pre>この問題が発生しない場合は、これを行う必要はありません。|
|スコープ|エッジ|
|Version|4.7.2|
|型|再ターゲット中|

