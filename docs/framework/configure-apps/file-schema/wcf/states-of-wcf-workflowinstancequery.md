---
title: <states>WCF の<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: d17f7525-8035-4e9e-85a0-4cddae59f85d
ms.openlocfilehash: ef4ce4b6fa6e60ead10b196b10a7c1489e15ac25
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938977"
---
# <a name="states-of-wcf-workflowinstancequery"></a>\<WCF、 \<workflowinstancequery > の > 状態

追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクションを表します。  
  
追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。  
  
\<system.serviceModel> \<tracking>  
\<プロファイル >  
\<trackingProfile>  
\<ワークフロー >  
\<workflowInstanceQueries>  
\<workflowInstanceQuery >  
\<状態 >  
  
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
|[\<状態 >](state-of-wcf-workflowinstancequery.md)|追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<workflowInstanceQuery>](../windows-workflow-foundation/workflowinstancequery.md)|開始したイベントや完了したイベントなど、ワークフロー インスタンスのライフサイクルの変化を追跡するクエリ。|  
  
## <a name="remarks"></a>Remarks

返されたレコードは、このコレクションの状態でフィルター処理されます。  
  
次の表に、有効な状態の値を示します。  
  
|状態|説明|  
|-----------|-----------------|  
|Aborted|ワークフロー インスタンスは中止されました。|  
|完了|ワークフロー インスタンスは完了しました。|  
|Deleted|ワークフロー インスタンスは削除されました。|  
|アイドル|ワークフロー インスタンスはアイドル状態です。|  
|Persisted|ワークフロー インスタンスは永続化されました。|  
|Resumed|ワークフロー インスタンスが再開されました。|  
|Started|ワークフロー インスタンスが開始されました。|  
|UnhandledException|ワークフロー インスタンスで未処理の例外が発生しました。|  
|アンロードされました|ワークフロー インスタンスはアンロードされました。|  
|Canceled|ワークフロー インスタンスは取り消されました。|  
|中断|ワークフロー インスタンスが中断されています。|  
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
- [ワークフローの追跡とトレース](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)
