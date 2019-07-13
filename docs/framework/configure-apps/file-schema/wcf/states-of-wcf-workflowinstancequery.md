---
title: <states> WCF の <workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: fad6f9c8871f79e4a1e26c893eed86ba168f6d01
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757951"
---
# <a name="states-of-wcf-workflowinstancequery"></a>\<状態 > WCF の\<workflowInstanceQuery >

追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクションを表します。  
  
追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
\<system.serviceModel> \<tracking>  
\<プロファイル >  
\<trackingProfile>  
\<ワークフロー >  
\<workflowInstanceQueries>  
\<workflowInstanceQuery>  
\<states>  
  
## <a name="syntax"></a>構文  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <workflowInstanceQueries>
          <workflowInstanceQuery>
            <states>
              <state name="Name" />
            </states>
          </workflowInstanceQuery>
        </workflowInstanceQueries>
      </workflow>
    </trackingProfile>
  </profiles>
</tracking>
```  
  
## <a name="attributes-and-elements"></a>属性と要素

以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  

なし。  
  
### <a name="child-elements"></a>子要素
  
|要素|説明|  
|-------------|-----------------|  
|[\<states>](state-of-wcf-workflowinstancequery.md)|追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancequery.md)|開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡するクエリ。|  
  
## <a name="remarks"></a>Remarks

返されたレコードは、このコレクションの状態でフィルター処理されます。  
  
次の表に、有効な状態の値を示します。  
  
|状態|説明|  
|-----------|-----------------|  
|Aborted|ワークフロー インスタンスは中止されました。|  
|完了|ワークフロー インスタンスは完了しました。|  
|Deleted|ワークフロー インスタンスは削除されました。|  
|Idle|ワークフロー インスタンスはアイドル状態です。|  
|Persisted|ワークフロー インスタンスは永続化されました。|  
|Resumed|ワークフロー インスタンスが再開されました。|  
|開始|ワークフロー インスタンスが開始されました。|  
|UnhandledException|ワークフロー インスタンスで未処理の例外が発生しました。|  
|アンロードされました|ワークフロー インスタンスはアンロードされました。|  
|Canceled|ワークフロー インスタンスは取り消されました。|  
|Suspended|ワークフロー インスタンスが中断されています。|  
|Terminated|ワークフロー インスタンスは終了しました。|  
|Unsuspended|ワークフロー インスタンスの中断が解除されました。|  
  
## <a name="example"></a>例

次の構成は、このクエリを使用して、`Started` インスタンス状態のワークフロー インスタンス レベルの追跡レコードを定期受信します。  
  
```xml  
<workflowInstanceQueries>
  <workflowInstanceQuery>
    <states>
      <state name="Started" />
    </states>
  </workflowInstanceQuery>
</workflowInstanceQueries>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Activities.Tracking.Configuration.WorkflowInstanceQueryElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [ワークフローの追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
