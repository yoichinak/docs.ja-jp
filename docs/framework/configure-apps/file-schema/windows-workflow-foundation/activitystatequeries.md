---
title: <activityStateQueries>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: bdd3c8ae-a13f-4df1-9b3c-a9d6c4bb1b5f
ms.openlocfilehash: ad41c1afec0b46a404f8f24882587c1dfeb68a80
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267808"
---
# <a name="activitystatequeries"></a>\<activityStateQueries>
ワークフロー インスタンスを構成するアクティビティのライフサイクルの変化を追跡するために使用する、クエリのコレクションを表します。 たとえば、ワークフロー インスタンス内で、「電子メールの送信」アクティビティが完了するたびの追跡する可能性があります。 追跡参加要素がアクティビティ状態レコード オブジェクトを定期受信するには、このクエリが必要です。 定期受信可能な状態は ActivityStates で指定します。  
  
 追跡プロファイルのクエリの詳細については、[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)を参照してください。  
  
\<system.serviceModel>  
\<追跡 >  
\<trackingProfile>  
\<ワークフロー >  
\<activityStateQueries>  
  
## <a name="syntax"></a>構文  
  
```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <activityStateQueries>
        <activityStateQuery activityName="String" />
        <arguments>
          <argument name="String" />
        </arguments>
        <states>
          <state name="String" />
        </states>
        <variables>
         <variable name="String" />
        </variables>
      </activityStateQueries>
    </workflow>
  </trackingProfile>
</tracking>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<activityStateQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/activitystatequery.md)|1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリ。  このイベントは、FaultHandler がエラーを処理するたびに発生します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<workflow>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|識別される特定のワークフローのすべてのクエリを格納する構成要素、 **activityDefinitionId**プロパティ。|  
  
## <a name="see-also"></a>関連項目
- <xref:System.ServiceModel.Activities.Tracking.Configuration.ActivityStateQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.ActivityStateQuery?displayProperty=nameWithType>
- [ワークフローの追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
