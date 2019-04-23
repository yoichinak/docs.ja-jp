---
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: b627105dc4aae49557b0a6684569719622e13f08
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59180597"
---
# <a name="peerauthentication"></a>\<peerAuthentication>
ピア ノードで使用されるピア証明書の認証設定を指定します。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<serviceCredentials>  
\<ピア >  
\<peerAuthentication>  
  
## <a name="syntax"></a>構文  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`certificateValidationMode`|省略可能な列挙体です。 資格情報の検証に使用される 3 つのモードのいずれかを指定します。 この属性は <xref:System.ServiceModel.Security.X509CertificateValidationMode> 型です。 `Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。|  
|`customCertificateValidatorType`|省略可能な文字列。 ユーザー設定タイプの検証に使用されるタイプおよびアセンブリを指定します。 `certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。 この属性は <xref:System.IdentityModel.Selectors.X509CertificateValidator> 型です。 Windows Communication Foundation (WCF) は、既定のピア信頼されたユーザー ストアに対してピア証明書を検証する証明書検証を提供します。 証明書が有効なルートまでつながっていることを検証します。 カスタム検証を実装して別の動作を指定したり、この属性を使用してカスタム検証を指定することができます。|  
|`revocationMode`|省略可能な列挙体です。 証明書失効モードを指定します。 この属性は <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 型です。 システムは、ピア証明書を失効証明書リストで検索して、それが失効していないことを検証します。 このチェックは、オンラインで、またはキャッシュされた失効リストをチェックする方法で実行されます。 失効チェックは、この属性を NoCheck に設定することにより無効にできます。|  
|`trustedStoreLocation`|省略可能な列挙体です。 WCF セキュリティ システムによってピア証明書を検証する信頼されたストアの場所を指定します。 この属性は <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 型です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<peer>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|ピア ノードの現在の資格情報を指定します。|  
  
## <a name="remarks"></a>Remarks  
 `<authentication>` 要素は、<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> クラスに対応します。 この要素は、メッシュ内の近隣ノード間の認証時に呼び出される検証コントロールを指定します。 新しいピアが近隣ノードとの接続を確立しようとするとき、自身の資格情報を応答側のピアに渡します。 リモート パーティの資格情報を検証するために、応答側の検証が呼び出されます。 メッシュ内でピア接続が確立されるたびに、両方のピアが相互に認証されます。つまり、双方の検証が呼び出されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [ピアツーピア ネットワーク](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [ピア チャネル メッセージの認証](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [ピア チャネル カスタム認証](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [セキュリティによるピア チャネル アプリケーションの保護](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
