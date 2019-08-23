---
title: <security> の <ws2007HttpBinding>
ms.date: 03/30/2017
ms.assetid: fdda0ff7-b462-4e26-af52-e87ddab71945
ms.openlocfilehash: a895df027bee7430e51e76c480136a49b6b2a0be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936574"
---
# <a name="security-of-ws2007httpbinding"></a>\<ws2007HttpBinding > の\<セキュリティ >
Ws2007HttpBinding > 要素で[ \<](ws2007httpbinding.md)使用されるセキュリティ設定を表します。  
  
 \<system.serviceModel>  
\<bindings>  
\<ws2007HttpBinding >  
\<binding>  
\<セキュリティ >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>
  <bindings>
    <ws2007HttpBinding>
      <binding name = "String">
        <security mode="None/Message/Transport/TransportWithMessageCredential">
          <transport>
          </transport>
          <message>
          </message>
        </security>
      </binding>
    </ws2007HttpBinding>
  </bindings>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`mode`|Optional. 適用するセキュリティの種類を指定します。 既定値は `Message` です。<br /><br /> この属性は <xref:System.ServiceModel.SecurityMode> 型です。|  
  
## <a name="mode-attribute"></a>Mode 属性  
  
|値|説明|  
|-----------|-----------------|  
|`None`|セキュリティを無効にします。|  
|`Transport`|セキュリティは、HTTPS を使用して確保されます。 サービスは、Secure Sockets Layer (SSL) 証明書を使用して構成する必要があります。 メッセージは、HTTPS およびサービスを使用して完全にセキュリティで保護され、サービスの SSL 証明書を使用するクライアントによって認証されます。 クライアント認証は、 [ \<トランスポート >](transport-of-ws2007httpbinding.md)要素`ClientCredentials`の属性によって制御されます。|  
|`Message`|セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。 既定では、SOAP 本文は暗号化および署名されます。 このモードは、サービス資格情報をクライアントの帯域外で使用可能にするかどうか、使用するアルゴリズム スイート、<xref:System.ServiceModel.Security.SecurityMessageProperty> によってメッセージ本文に適用する保護レベルなど、さまざまな機能を提供します。 クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。|  
|`TransportWithMessageCredential`|このモードでは、HTTPS は、整合性、機密性、およびサーバー認証を提供し、SOAP メッセージ セキュリティはクライアント認証を提供します。 既定では、クライアント認証はセッションごとに 1 回実行され、認証の結果はセッションの存続中にキャッシュされます。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<transport>](transport-of-ws2007httpbinding.md)|トランスポートのセキュリティ設定を定義します。 この要素は、<xref:System.ServiceModel.Configuration.HttpTransportSecurityElement> 型に対応しています。 これらの設定は、モードが Transport に設定されている場合のみ適用されます。|  
|[\<message>](message-of-ws2007httpbinding.md)|メッセージのセキュリティ設定を定義します。 この要素は、<xref:System.ServiceModel.Configuration.MessageSecurityOverHttpElement> 型に対応しています。 これらの設定は、モードが Transport に設定されている場合は適用されません。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ws2007HttpBinding >](ws2007httpbinding.md)|HTTP トランスポート アプリケーションのセキュリティで保護されたバインド。|  
  
## <a name="remarks"></a>Remarks  
 この要素は、WS-* 仕様を実装するサービスと相互運用するようにデザインされています。 このバインディングのトランスポート セキュリティは、SSL (Secure Sockets Layer) over HTTP または HTTPS です。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.WSHttpSecurity>
- <xref:System.ServiceModel.WSHttpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.WSHttpSecurityElement>
- <xref:System.ServiceModel.BasicHttpSecurity>
- [サービスおよびクライアントのセキュリティ保護](../../../wcf/feature-details/securing-services-and-clients.md)
- [バインディング](../../../wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
