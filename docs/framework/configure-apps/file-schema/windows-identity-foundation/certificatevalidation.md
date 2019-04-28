---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 7b8823d792e3f15846a9483d670994be4b368980
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667354"
---
# <a name="certificatevalidation"></a>\<certificateValidation>
トークン ハンドラーを使用して証明書の検証の設定を制御します。 特定のハンドラーが、独自の検証ツールで構成されている場合、これらの設定が上書きされます。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<certificateValidation>  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|certificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode> X.509 証明書を使用する検証モードを指定する値。 既定値は、"PeerOrChainTrust"です。 カスタム検証を指定するには、"Custom"には、この属性を設定し、検証を指定、 [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)要素。 任意。|  
|revocationMode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> X.509 証明書を使用する失効モードを指定する値。 既定値は、"Online"です。 省略可能です。|  
|trustedStoreLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 証明書ストアを指定する値。 既定値は、"LocalMachine"です。 省略可能です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<certificateValidator>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|証明書の検証のカスタム型を指定します。 場合にのみ、この型が使用される、`certificateValidationMode`の属性、 [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)要素が"Custom"に設定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス レベルの id の設定を指定します。|  
|[\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|トークン ハンドラー コレクションのセキュリティの構成を提供します。|  
  
## <a name="remarks"></a>Remarks  
 A`<certificateValidation>`下で、サービス レベルで要素を指定することができます、`<identityConfiguration>`要素またはセキュリティ トークン ハンドラー コレクション レベルの下で、`<securityTokenHandlerConfiguration>`要素。 トークン ハンドラー コレクションの設定は、サービスに指定されているものをオーバーライドします。 いくつかのトークン ハンドラーを使用すると、構成で証明書検証の設定を指定できます。 個々 のトークン ハンドラーの設定は、サービス レベルとセキュリティ トークン ハンドラー コレクションの両方に指定されたオーバーライドします。  
  
## <a name="example"></a>例  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
