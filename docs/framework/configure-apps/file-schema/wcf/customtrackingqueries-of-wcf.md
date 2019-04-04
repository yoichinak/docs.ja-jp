---
title: <customTrackingQueries> WCF の
ms.date: 03/30/2017
ms.assetid: 14cfe47e-9935-4120-84f1-8f38de8ca4c1
ms.openlocfilehash: 8b317cc289853902592e145e34b6e7bf5f84763b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/30/2019
ms.locfileid: "55282374"
---
# <a name="customtrackingqueries-of-wcf"></a>\<customTrackingQueries > の WCF

コード アクティビティで定義するイベントを追跡するために使用する、クエリのコレクションを表します。 追跡参加要素がカスタム追跡レコードを定期受信するには、このクエリが必要です。  
  
 追跡プロファイルのクエリの詳細については、[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)を参照してください。
  
\<system.serviceModel>  
\<追跡 >  
\<プロファイル >  
\<trackingProfile>  
\<ワークフロー >  
\<customTrackingQueries>  
  
## <a name="syntax"></a>構文  
  
```xml  
<tracking>
  <profiles>
    <trackingProfile name="Name">
      <workflow>
        <customTrackingQueries>
          <customTrackingQuery activityName="String"
                               name="String"/>
        </customTrackingQueries>
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
|[\<customTrackingQuery>](customtrackingquery-of-wcf.md)|コード アクティビティで定義するイベントを追跡するために使用するクエリ。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<workflow>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|`activityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Activities.Tracking.Configuration.CustomTrackingQueryElementCollection?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.CustomTrackingQuery?displayProperty=nameWithType>
- [ワークフローの追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
