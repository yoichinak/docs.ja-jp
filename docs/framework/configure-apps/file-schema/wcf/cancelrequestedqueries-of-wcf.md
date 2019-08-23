---
title: <cancelRequestedQueries>WCF の
ms.date: 03/30/2017
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
ms.openlocfilehash: 0f04fc928358c96ca3112422f1a6ccd039269e47
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926246"
---
# <a name="cancelrequestedqueries-of-wcf"></a>\<WCF の cancelRequestedQueries >
親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する、クエリのコレクションを表します。 追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。  
  
追跡プロファイルのクエリの詳細については、「[追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)」を参照してください。  
  
\<system.serviceModel>  
\<追跡 >  
\<プロファイル > \<trackingprofile >  
\<ワークフロー >  
\<cancelRequestedQueries>  
  
## <a name="syntax"></a>構文  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <cancelRequestQueries>
          <cancelRequestQuery activityName="String"
                              childActivityName="String" />
        </cancelRequestQueries>
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
|[\<cancelRequestedQuery>](cancelrequestedquery-of-wcf.md)|親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用するクエリ。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<workflow>](../windows-workflow-foundation/workflow.md)|<xref:System.ServiceModel.Activities.Tracking.Configuration.ProfileWorkflowElement.ActivityDefinitionId> プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Activities.Tracking.CancelRequestedQuery>
- [ワークフローの追跡とトレース](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追跡プロファイル](../../../windows-workflow-foundation/tracking-profiles.md)
