---
title: <add> の <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: 5c9937cb6302a194228461f3e2e06ecdf4d43269
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57377756"
---
# <a name="add-of-issuerchannelbehaviors"></a>\<add> of \<issuerChannelBehaviors>

STS と通信するときに使用されるエンドポイントの動作を追加します。

> [!NOTE]
> エンドポイントの動作が含まれている場合、 [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)要素、例外がスローされます。

\<system.ServiceModel>\
\<behaviors>\
endpointBehaviors セクション\<動作 > \
\<clientCredentials>\
\<issuedToken>\
\<issuerChannelBehaviors > Element\
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
|[\<issuerChannelBehaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|指定されたサービス トークン サービスと通信するときに使用する Windows Communication Foundation (WCF) クライアント エンドポイントの動作のコレクションを含みます。|

## <a name="remarks"></a>Remarks

`issuerAddress` には、クライアントの通信相手となるセキュリティ トークン サービスの URI が含まれます。 `behaviorConfiguration` アプリケーションがセキュリティ トークン サービスから発行されたトークンを取得する Windows Communication Foundation (WCF) によって作成されたチャネルで使用するエンドポイントの動作を指します。

## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [サービス ID と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [クライアントのセキュリティ保護](../../../../../docs/framework/wcf/securing-clients.md)
- [方法: フェデレーション クライアントを作成します。](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [方法: ローカル発行者を構成します。](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)
- [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [\<issuerChannelBehaviors>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
