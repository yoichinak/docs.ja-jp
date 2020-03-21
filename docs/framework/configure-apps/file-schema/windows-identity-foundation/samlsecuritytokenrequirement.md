---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152633"
---
# <a name="samlsecuritytokenrequirement"></a>\<>
<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>クラス、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラス、またはこれらのクラスのいずれかの派生クラスの構成を提供します。 クラスによって表<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>されます。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<id構成>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>を追加する**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<要件>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|ウィンドウズにマップします。|トークン ハンドラーが、入力方向の UPN 要求を使用して検証トークンを Windows アカウントにマップするかどうかを指定します。 既定値は "false" です。|  
|発行者証明書失効モード|X.509 証明書に使用する失効モードを指定する<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>値。 デフォルト値は「オンライン」です。|  
|証明書検証モードを発行します。|X.509 証明書に使用する検証モードを指定する<xref:System.ServiceModel.Security.X509CertificateValidationMode>値。 既定値は"ピアオーチェーントラスト" です。|  
|発行者証明書信頼されたストアの場所|X.509 証明書ストアを指定する<xref:System.Security.Cryptography.X509Certificates.StoreLocation>値。 デフォルト値は「ローカルマシン」です。|  
|発行者証明書検証ツール|から<xref:System.IdentityModel.Selectors.X509CertificateValidator>派生するカスタム型。 属性が`issuerCertificateValidationMode`"カスタム" の場合、この型のインスタンスは発行者証明書の検証に使用されます。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<名前クレームタイプ>](nameclaimtype.md)|プロパティを指定するクレームの種類<xref:System.Security.Principal.IIdentity.Name%2A>を設定します。|  
|[\<ロールクレームタイプ>](roleclaimtype.md)|トークン ハンドラーのメソッドによって返されるオブジェクトのコレクション内の<xref:System.Security.Claims.ClaimsIdentity>ロールの種類の要求<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>を定義するクレームの種類を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<>を追加する](add.md)|指定したセキュリティ トークン ハンドラーをトークン ハンドラー コレクションに追加します。|  
  
## <a name="remarks"></a>解説  
 要素`<samlSecurityTokenRequirement>`はオブジェクト モデルの<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>クラスによって表され、 または のプロパティを`SamlSecurityTokenRequirement`<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>構成するために使用されます<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>。  
  
## <a name="example"></a>例  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
