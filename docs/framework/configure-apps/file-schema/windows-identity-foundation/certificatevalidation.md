---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 8185153eb02c5794b0f6ac02a6837806f2073c07
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941917"
---
# <a name="certificatevalidation"></a>\<certificateValidation >
トークンハンドラーが証明書を検証するために使用する設定を制御します。 特定のハンドラーが独自の検証コントロールを使用して構成されている場合、これらの設定はオーバーライドされます。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<certificateValidation >  
  
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
|certificateValidationMode|X.509 証明書に使用する検証モードを指定する値。<xref:System.ServiceModel.Security.X509CertificateValidationMode> 既定値は "PeerOrChainTrust" です。 カスタム検証を指定するには、この属性を "custom" に設定し、 [ \<certificatevalidator >](certificatevalidator.md)要素を使用して検証コントロールを指定します。 任意。|  
|revocationMode|X.509 証明書に使用する失効モードを指定する値。<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 既定値は "Online" です。 任意。|  
|trustedStoreLocation|X.509 証明書ストアを示す値です。<xref:System.Security.Cryptography.X509Certificates.StoreLocation> 既定値は "LocalMachine" です。 任意。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|証明書の検証に使用するカスタムの種類を指定します。 この型は、 `certificateValidationMode` [ \<certificatevalidation >](certificatevalidation.md)要素の属性が "Custom" に設定されている場合にのみ使用されます。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|サービスレベルの id 設定を指定します。|  
|[\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md)|セキュリティトークンハンドラーのコレクションの構成を提供します。|  
  
## <a name="remarks"></a>Remarks  
 要素は、要素の`<identityConfiguration>`下のサービスレベルで指定することも、 `<securityTokenHandlerConfiguration>`要素の下のセキュリティトークンハンドラーコレクションレベルで指定することもできます。 `<certificateValidation>` トークンハンドラーコレクションの設定は、サービスで指定された設定よりも優先されます。 一部のトークンハンドラーでは、構成で証明書の検証設定を指定できます。 個々のトークンハンドラーの設定は、サービスレベルとセキュリティトークンハンドラーコレクションの両方で指定された設定よりも優先されます。  
  
## <a name="example"></a>例  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
