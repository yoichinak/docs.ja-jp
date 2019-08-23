---
title: <state>WCF の<workflowInstanceQuery>
ms.date: 03/30/2017
ms.assetid: 40f21055-766c-4be9-86c4-d1d899007098
ms.openlocfilehash: 99387a8f60e96beb2ec7706d9abf4bb6ae84b868
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938208"
---
# <a name="state-of-wcf-workflowinstancequery"></a>\<WCF、 \<workflowinstancequery > の状態 >
追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクションを表します。  
  
 追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。  
  
\<system.serviceModel>  
\<追跡 >  
\<プロファイル >  
\<trackingProfile>  
\<ワークフロー >  
\<workflowInstanceQueries>  
\<workflowInstanceQuery >  
\<状態 >  
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

|属性|説明|  
|---------------|-----------------|  
|`name`|追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態を指定する文字列。|  
  
### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

|要素|説明|  
|-------------|-----------------|  
|[\<状態 >](states-of-wcf-workflowinstancequery.md)|追跡レコードが作成されたときの追跡ワークフロー インスタンスの定期受信済み状態のコレクション。|  
  
## <a name="remarks"></a>Remarks  

返されたレコードは、このコレクションの状態でフィルター処理されます。  
  
次の表で、使用可能な状態の値について説明します。
  
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
- <xref:System.ServiceModel.Activities.Tracking.Configuration.StateElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.WorkflowInstanceQuery?displayProperty=nameWithType>
- [ワークフローの追跡とトレース](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)
