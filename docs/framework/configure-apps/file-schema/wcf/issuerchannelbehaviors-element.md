---
title: <issuerChannelBehaviors> 要素
ms.date: 03/30/2017
ms.assetid: f7378673-8e9b-45b2-98d1-cf5dccdd8c40
ms.openlocfilehash: 7cbd50daa82b0ca937a1bba93786545898b03c8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760728"
---
# <a name="issuerchannelbehaviors-element"></a>\<issuerChannelBehaviors > 要素

指定されたサービス トークン サービスと通信するときに使用するには、Windows Communication Foundation (WCF) クライアント エンドポイントの動作 (構成で定義されている) のコレクションを含みます。 定義された動作は、いずれかを含めることはできません[ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)要素。

```xml
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior>
        <clientCredentials>
          <issuedToken>
            <issuerChannelBehaviors>
```

## <a name="syntax"></a>構文

```xml
<issuerChannelBehaviors>
  <add behaviorConfiguration="string"
       issuerAddress="string" />
</issuerChannelBehaviors>
```

## <a name="attributes-and-elements"></a>属性および要素

以降のセクションでは、属性、子要素、および親要素について説明します。

### <a name="attributes"></a>属性

なし。

### <a name="child-elements"></a>子要素

|要素|説明|
|-------------|-----------------|
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-issuerchannelbehaviors.md)|コレクションに動作を追加します。|

### <a name="parent-elements"></a>親要素

|要素|説明|
|-------------|-----------------|
|[\<issuedToken >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md)|サービスに対するクライアントの認証に使用されるカスタム トークンを指定します。|

## <a name="remarks"></a>Remarks

この要素を使用するのは、なんらかの動作 (`<clientCredentials>` 要素を含む動作以外) を使用してサービスと通信する必要がある場合です。 たとえば場合、 [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)動作要素を含める必要があります。

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
