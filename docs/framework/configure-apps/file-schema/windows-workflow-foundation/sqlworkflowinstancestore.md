---
title: <sqlWorkflowInstanceStore>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 8a4e4214-fc51-4f4d-b968-0427c37a9520
ms.openlocfilehash: 7a6f9fb5b2b98d2951343b5a529507b3fcd88dc8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947518"
---
# <a name="sqlworkflowinstancestore"></a>\<sqlWorkflowInstanceStore>
ワークフローサービスインスタンスの状態情報の SQL Server 2005 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>または SQL Server 2008 データベースへの永続化をサポートする機能を構成できるようにするサービス動作。 この機能の詳細については、「 [SQL Workflow Instance Store](../../../windows-workflow-foundation/sql-workflow-instance-store.md)」を参照してください。  
  
\<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<sqlWorkflowInstanceStore>  
  
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
|connectionString|基になる永続性データベースへの接続に使用される接続文字列を含む文字列。|  
|connectionStringName|データベースサーバーへの名前付き接続文字列を含む文字列。 名前付き接続文字列の例としては、"DefaultConnectionString" などがあります。|  
|hostLockRenewalPeriod|ホストがインスタンスのロックを更新するまでの時間を指定する Timespan 値。 指定した時間内にホストがロックを更新しない場合は、インスタンスのロックが解除され、他のホストがそのインスタンスを使用できるようになります。<br /><br /> ワークフローをアンロードすることは、同時に、永続化することも意味します。 この属性が0に設定されている場合は、ワークフローがアイドル状態になった直後にワークフローインスタンスが永続化され、アンロードされます。 この属性を TimeSpan に設定すると、アンロード操作が実質的に無効になります。 アイドル状態になったワークフロー インスタンスはアンロードされません。|  
|instanceCompletionAction|ワークフロー インスタンス完了後にワークフロー インスタンス データを永続化ストアに保持するか、またはその時点で削除するかを指定する値。 この値は、<xref:System.Activities.DurableInstancing.InstanceCompletionAction> 型です。<br /><br /> 列挙されるアクションは、インスタンスがその操作を完了したとき、永続化ストアからインスタンス データを削除するかどうかで構成されます。<br /><br /> 完了後にインスタンスを保持すると、永続性データベースが急速に増大して、データベースのパフォーマンスに影響します。 データベースのパフォーマンスがパフォーマンス要件を満たすレベルになるように、これらのレコードを定期的に削除するパージ ポリシーを構成する必要があります。|  
|instanceEncodingOption|インスタンス状態情報を永続化ストアに格納する前に、GZip アルゴリズムで圧縮するかどうかを指定する、省略可能な値。 この値は、<xref:System.Activities.DurableInstancing.InstanceEncodingOption> 型です。 このプロパティに指定できる値<xref:System.Activities.DurableInstancing.InstanceEncodingOption.None>はで、圧縮が指定さ<xref:System.Activities.DurableInstancing.InstanceEncodingOption.GZip>れていません。また、はインスタンスデータを圧縮し、gzip アルゴリズムを使用することを指定します。|  
|instanceLockedExceptionAction|現在、他のホストにロックされているインスタンスをホストがロックしようとしたときにスローされる例外への応答として発生するアクションを指定する値。 この値は、<xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction> 型です。<br /><br /> このフィールドに指定できるオプションは次のとおりです。None、Basic Retry、およびアグレッシブな再試行。 既定値は None です。 これら 3 つのオプションの説明を次に示します。<br /><br /> - なし。 サービス ホストはインスタンスをロックしようとせず、<xref:System.Runtime.DurableInstancing.InstanceLockedException> を呼び出し元に渡します。<br />-基本的な再試行。 サービス ホストは一定の再試行間隔でインスタンスのロックを再試行し、シーケンスの最後に例外を呼び出し元に渡します。<br />-積極的に再試行します。 サービス ホストは指数関数的に増加する遅延を使用してインスタンスのロックを再試行し、シーケンスの最後に <xref:System.Runtime.DurableInstancing.InstanceLockedException> を呼び出し元に渡します。|  
|runnableInstancesDetectionPeriod||  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<servicebehaviors の\<動作 > >](behavior-of-servicebehaviors-of-workflow.md)|動作の要素を指定します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>
- <xref:System.ServiceModel.Activities.Configuration.SqlWorkflowInstanceStoreElement>
- <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>
- [SQL Workflow Instance Store](../../../windows-workflow-foundation/sql-workflow-instance-store.md)
