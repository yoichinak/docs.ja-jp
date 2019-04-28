---
title: <authentication> <clientCertificate>要素
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: e232cde8f6838de734e37aeee3f52cd7f7e7502d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701334"
---
# <a name="authentication-of-clientcertificate-element"></a>\<認証 > の\<clientCertificate > 要素
サービスによって使用されるクライアント証明書の認証動作を指定します。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<serviceCredentials>  
\<clientCertificate>  
\<authentication>  
  
## <a name="syntax"></a>構文  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|customCertificateValidatorType|省略可能な文字列。 カスタム型の検証に使用される型およびアセンブリです。 `certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。|  
|certificateValidationMode|省略可能な列挙体です。 資格情報の検証に使用されるモードのいずれかを指定します。 この属性は <xref:System.ServiceModel.Security.X509CertificateValidationMode> 型です。 <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType> に設定されている場合、`customCertificateValidator` も指定する必要があります。 既定値は、<xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType> です。|  
|includeWindowsGroups|省略可能なブール。 セキュリティ コンテキストに Windows グループが含まれているかどうかを指定します。 この属性を `true` に設定すると、グループ全体が拡張されるため、パフォーマンスに影響が及びます。 ユーザーが属するグループの一覧を生成する必要がない場合は、この属性を `false` に設定します。|  
|mapClientCertificateToWindowsAcccount|ブール型。 証明書を使用してクライアントを Windows ID にマップできるかどうかを指定します。 これを行うには、Active Directory が有効である必要があります。|  
|revocationMode|省略可能な列挙体です。 証明書失効リスト (RCL) のチェックに使用されるモードのいずれかです。 既定値は、`Online` です。 この値は、HTTP トランスポート セキュリティを使用する場合は無視されます。|  
|trustedStoreLocation|省略可能な列挙体です。 2 つのシステム格納場所 (`LocalMachine` または `CurrentUser`) のいずれかです。 この値は、サービス証明書がクライアントにネゴシエートされるときに使用されます。 に対して検証が実行、**信頼されたユーザー**指定したストアの場所に格納します。 既定値は `CurrentUser` です。|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType 属性  
  
|値|説明|  
|-----------|-----------------|  
|String|タイプ名およびアセンブリと、タイプの検索に使用される他のデータを指定します。|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode 属性  
  
|値|説明|  
|-----------|-----------------|  
|列挙|次のいずれかの値です。None、PeerTrust、ChainTrust、PeerOrChainTrust、Custom です。<br /><br /> 詳細については、次を参照してください。 [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)します。|  
  
## <a name="revocationmode-attribute"></a>revocationMode 属性  
  
|値|説明|  
|-----------|-----------------|  
|列挙|次のいずれかの値です。NoCheck、Online、Offline にします。 詳細については、次を参照してください。 [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)します。|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation 属性  
  
|値|説明|  
|-----------|-----------------|  
|列挙型|`LocalMachine` または `CurrentUser` のいずれかの値にします。 既定値は、`CurrentUser` です。 クライアント アプリケーションがシステム アカウントで実行されている場合、証明書は通常 `LocalMachine` の下にあります。 クライアント アプリケーションがユーザー アカウントで実行されている場合、証明書は通常 `CurrentUser` の下にあります。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|サービスに対するクライアントの認証に使用する X.509 証明書を定義します。|  
  
## <a name="remarks"></a>Remarks  
 `<authentication>` 要素は、<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> クラスに対応します。 この要素を使用すると、クライアントを認証する方法をカスタマイズできます。 `certificateValidationMode` 属性は、`None`、`ChainTrust`、`PeerOrChainTrust`、`PeerTrust`、または `Custom` に設定できます。 既定では、レベルに設定が`ChainTrust`で終了する証明書の階層で各証明書を検索するを指定する、*ルート機関*チェーンの上部にあります。 これは最もセキュリティで保護されているモードです。 また、値を `PeerOrChainTrust` に設定することもできます。これは、信頼されたチェーン内の証明書と共に、自己発行された証明書 (ピア信頼) も受け入れるよう指定します。 自己発行の資格情報は信頼された証明機関から購入したものである必要はないため、この値はクライアントとサービスの開発およびデバッグに使用されます。 クライアントを展開するときは、代わりに `ChainTrust` 値を使用します。  
  
 また、値を `Custom` に設定することもできます。 `Custom` 値に設定する場合は、`customCertificateValidatorType` 属性を、証明書の検証に使用するアセンブリと型に設定する必要もあります。 独自のカスタム検証を作成するには、抽象 <xref:System.IdentityModel.Selectors.X509CertificateValidator> クラスを継承する必要があります。 詳細については、「[方法 :カスタム証明書の検証を使用するサービスを作成する](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)します。  
  
## <a name="example"></a>例  
 次のコードは、`<authentication>` 要素の X.509 証明書とカスタム検証タイプを指定します。  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [方法: カスタム証明書の検証を使用するサービスを作成します。](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
