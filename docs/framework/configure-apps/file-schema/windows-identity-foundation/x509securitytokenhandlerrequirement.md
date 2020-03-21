---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152451"
---
# <a name="x509securitytokenhandlerrequirement"></a>\<>の要件を満たしています。
クラスまたは派生クラスの<xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>オプションの構成を提供します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<id構成>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>を追加する**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>の要件を満>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
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
|certificateValidationMode|X.509 証明書に使用する検証モードを指定する<xref:System.ServiceModel.Security.X509CertificateValidationMode>値。 既定値は"ピアオーチェーントラスト" です。|  
|ウィンドウズにマップします。|トークン ハンドラーが、入力方向の UPN 要求を使用して検証トークンを Windows アカウントにマップするかどうかを指定します。 既定値は "false" です。|  
|revocationMode|X.509 証明書に使用する失効モードを指定する<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>値。 デフォルト値は「オンライン」です。|  
|trustedStoreLocation|X.509 証明書ストアを指定する<xref:System.Security.Cryptography.X509Certificates.StoreLocation>値。 デフォルト値は「ローカルマシン」です。|  
|証明書検証ツール|から<xref:System.IdentityModel.Selectors.X509CertificateValidator>派生するカスタム型。 属性が`certificateValidationMode`"カスタム" の場合、この型のインスタンスは発行者証明書の検証に使用されます。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<>を追加する](add.md)|指定したセキュリティ トークン ハンドラーをトークン ハンドラー コレクションに追加します。|  
  
## <a name="example"></a>例  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
