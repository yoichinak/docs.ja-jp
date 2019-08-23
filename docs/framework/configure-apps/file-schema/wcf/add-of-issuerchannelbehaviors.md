---
title: <add> の <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 325d6b8111115384b18547bd11ccec8a4a8af711
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920110"
---
# <a name="add-of-issuerchannelbehaviors"></a>\<issuerchannelbehaviors \<の > を追加し >

STS と通信するときに使用されるエンドポイントの動作を追加します。

> [!NOTE]
> いずれかのエンドポイント動作に[ \<clientCredentials >](clientcredentials.md)要素が含まれている場合は、例外がスローされます。

\<system.ServiceModel>\
\<動作 > \
endpointbehaviors セクション\<の動作 > \
\<clientCredentials>\
\<issuedToken > \
\<issuerChannelBehaviors > 要素 \
\<add>

## <a name="syntax"></a>構文

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a>属性および要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

|属性|説明|
|---------------|-----------------|
|issuerAddress|通信するためのセキュリティ トークン発行者の URI。|
|behaviorConfiguration|同じ構成ファイルに定義されたエンドポイントの動作の名前。|

### <a name="child-elements"></a>子要素

なし。

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)|指定されたサービストークンサービスと通信するときに使用される Windows Communication Foundation (WCF) クライアントエンドポイントの動作のコレクションを格納します。|

## <a name="remarks"></a>Remarks

`issuerAddress` には、クライアントの通信相手となるセキュリティ トークン サービスの URI が含まれます。 `behaviorConfiguration`セキュリティトークンサービスから発行済みトークンを取得するために Windows Communication Foundation (WCF) によって作成されたチャネルでアプリケーションが使用するエンドポイント動作を指します。

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [サービス ID と認証](../../../wcf/feature-details/service-identity-and-authentication.md)
- [セキュリティ動作](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [フェデレーションと発行済みトークン](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [サービスおよびクライアントのセキュリティ保護](../../../wcf/feature-details/securing-services-and-clients.md)
- [クライアントのセキュリティ保護](../../../wcf/securing-clients.md)
- [方法: フェデレーションクライアントを作成する](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [方法: ローカル発行者を構成する](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [フェデレーションと発行済みトークン](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](issuerchannelbehaviors-element.md)
