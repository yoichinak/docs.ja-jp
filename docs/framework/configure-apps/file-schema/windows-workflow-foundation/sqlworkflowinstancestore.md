---
title: <sqlWorkflowInstanceStore>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: 56a44fdb62062903ca3ad00f8105a66ccab02cca
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151963"
---
# <a name="sqlworkflowinstancestore"></a>\<>
ワークフロー サービス インスタンスの状態情報の永続化を SQL Server 2005 または SQL Server 2008 データベースでサポートする <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 機能を構成するためのサービス動作。 この機能の詳細については、「 [SQL ワークフロー インスタンス ストア](../../../windows-workflow-foundation/sql-workflow-instance-store.md)」を参照してください。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<システム。サービスモデル>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<動作>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<サービス動作>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<動作>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sqlWorkflowInstanceStore connectionStringName="String"
                                hostLockRenewalPeriod="TimeSpan"
                                instanceCompletionAction="DeleteNothing/DeleteAll"
                                instanceEncodingAction="None/GZip"
                                instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"
                                runnableInstancesDetectionPeriod="TimeSpan" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|connectionString|基になる永続性データベースへの接続に使用する接続文字列を含む文字列。|  
|connectionStringName|データベース サーバーへの名前付き接続文字列を含む文字列。 名前付き接続文字列の例としては、"既定の接続文字列" があります。|  
|ホストロックリニューアル期間|ホストがインスタンスのロックを更新するまでの時間を指定する Timespan 値。 指定した時間内にホストがロックを更新しない場合は、インスタンスのロックが解除され、他のホストがそのインスタンスを使用できるようになります。<br /><br /> ワークフローをアンロードすることは、同時に、永続化することも意味します。 この属性をゼロに設定した場合は、ワークフローがアイドル状態になった直後に、ワークフロー インスタンスが永続化され、アンロードされます。 この属性を TimeSpan.MaxValue に設定すると、アンロード操作を事実上、無効にします。 アイドル状態になったワークフロー インスタンスはアンロードされません。|  
|instanceCompletionAction|ワークフロー インスタンス完了後にワークフロー インスタンス データを永続化ストアに保持するか、またはその時点で削除するかを指定する値。 この値は、<xref:System.Activities.DurableInstancing.InstanceCompletionAction> 型です。<br /><br /> 列挙されるアクションは、インスタンスがその操作を完了したとき、永続化ストアからインスタンス データを削除するかどうかで構成されます。<br /><br /> 完了後にインスタンスを保持すると、永続性データベースが急速に増大して、データベースのパフォーマンスに影響します。 データベースのパフォーマンスがパフォーマンス要件を満たすレベルになるように、これらのレコードを定期的に削除するパージ ポリシーを構成する必要があります。|  
|instanceEncodingOption|インスタンス状態情報を永続化ストアに格納する前に、GZip アルゴリズムで圧縮するかどうかを指定する、省略可能な値。 この値は、<xref:System.Activities.DurableInstancing.InstanceEncodingOption> 型です。 このプロパティの値としては<xref:System.Activities.DurableInstancing.InstanceEncodingOption.None>、圧縮を指定しない 、<xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip>インスタンス データを圧縮して gzip アルゴリズムを使用する 、 が考えられます。|  
|instanceLockedExceptionAction|現在、他のホストにロックされているインスタンスをホストがロックしようとしたときにスローされる例外への応答として発生するアクションを指定する値。 この値は、<xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> 型です。<br /><br /> このフィールドで使用できるオプションは、None、Basic Retry、および Aggressive Retry です。 既定値は None です。 これら 3 つのオプションの説明を次に示します。<br /><br /> - なし。 サービス ホストはインスタンスをロックしようとせず、<xref:System.Runtime.DurableInstancing.InstanceLockedException> を呼び出し元に渡します。<br />- 基本的な再試行。 サービス ホストは一定の再試行間隔でインスタンスのロックを再試行し、シーケンスの最後に例外を呼び出し元に渡します。<br />- アグレッシブな再試行 サービス ホストは指数関数的に増加する遅延を使用してインスタンスのロックを再試行し、シーケンスの最後に <xref:System.Runtime.DurableInstancing.InstanceLockedException> を呼び出し元に渡します。|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<サービスの\<動作>>](behavior-of-servicebehaviors-of-workflow.md)|動作の要素を指定します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>
- <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>
- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>
- [SQL Workflow Instance Store](../../../windows-workflow-foundation/sql-workflow-instance-store.md)
