---
title: <faultPropagationQuery>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 4fb5c2b1-3dad-4eca-9c7f-3efb51899813
ms.openlocfilehash: f3e281ff8a9de9be41dd6ad9d01ab52798d8e89e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794551"
---
# <a name="faultpropagationquery"></a>\<faultPropagationQuery>

1 つのアクティビティ内で発生するエラーの処理を追跡するために使用するクエリを表します。  このイベントは、FaultHandler がエラーを処理するたびに発生します。 1 つのアクティビティ内で発生したエラーの処理は、このようなクエリを使用して追跡する必要があります。 追跡参加要素がエラー伝達レコードを定期受信するには、このクエリが必要です。

 追跡プロファイルのクエリの詳細については、次を参照してください。[追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)します。

\<system.serviceModel>\
\<追跡 > \
\<trackingProfile>\
\<workflow>\
\<faultPropagationQueries>\
\<faultPropagationQuery>

## <a name="syntax"></a>構文

```xml
<tracking>
  <trackingProfile name="Name">
    <workflow>
      <faultPropagationQueries>
        <faultPropagationQuery activityName="String"
                               faultHandlerActivityName="String" />
      </faultPropagationQueries>
    </workflow>
  </trackingProfile>
</tracking>
```

## <a name="attributes-and-elements"></a>属性および要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|activityName|エラーを伝達したエラー ハンドラー アクティビティの名前を指定する文字列。 既定値は * で、すべてのアクティビティについてエラー伝達レコードが返されることを示します。|
|faultHandlerActivityName|エラーの原因となったアクティビティの名前を指定する文字列。|

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[\<faultPropagationQueries>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/faultpropagationqueries.md)|1 つのアクティビティ内で発生するエラーの処理を追跡するために使用する、構成要素の一覧を表します。  このイベントは、FaultHandler がエラーを処理するたびに発生します。|

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Activities.Tracking.Configuration.FaultPropagationQueryElement?displayProperty=nameWithType>
- <xref:System.Activities.Tracking.FaultPropagationQuery?displayProperty=nameWithType>
- [ワークフローの追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)
- [追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
