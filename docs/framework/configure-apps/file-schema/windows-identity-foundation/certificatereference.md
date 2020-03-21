---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 47d432a84d070476ddffd9b98a4ba46d8163bdc3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152815"
---
# <a name="certificatereference"></a>\<証明書リファレンス>
証明書ストア内の X.509 証明書を検索および検証するために使用する設定を指定します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<サービス>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<フェデレーション構成>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<サービス証明書>**](servicecertificate.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<証明書参照>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <serviceCertificate>  
      <certificateReference
        storeName="AddressBook||AuthRoot||CertificateAuthority||Disallowed||My||Root||TrustedPeople||TrustedPublisher"  
        storeLocation="CurrentUser||LocalMachine"  
        x509FindType="FindByThumbprint||FindBySubjectName||FindBySubjectDistinguishedName||FindByIssuerName||FindByIssuerDistinguishedName||FindBySerialNumber||FindByTimeValid||FindByTimeNotYetValid||FindByTimeExpired||FindByTemplateName||FindByApplicationPolicy||FindByCertificatePolicy||FindByExtension||FindByKeyUsage||FindBySubjectKeyIdentifier"  
        findValue=xs:String  
        isChainIncluded=xs:Boolean >  
      </certificateReference>  
    </serviceCertificate>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|storeName|X.509 証明書ストアの名前。 デフォルトは "My" です。 省略可能。|  
|storeLocation|X.509 証明書ストアの場所を指定する<xref:System.Security.Cryptography.X509Certificates.StoreLocation>値。 デフォルト値は「ローカルマシン」です。 省略可能。|  
|x509FindType|実行<xref:System.Security.Cryptography.X509Certificates.X509FindType>される検索の種類を指定する値。 デフォルトは「識別名を見つける」です。 省略可能。|  
|findValue|X.509 証明書ストアで検索する値。 省略可能。|  
|isChainIncluded|証明書チェーンを使用して検証を実行するかどうかを指定します。 デフォルトは "true" です。検証は、証明書チェーンを使用して実行されます。 省略可能。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<サービス証明書>](servicecertificate.md)|トークンの暗号化と復号化に使用される証明書を構成します。|  
  
## <a name="remarks"></a>解説  
 この`<certificateReference>`要素は、証明書ストア内の X.509 証明書を検索して検証するために使用される設定を指定します。 `<serviceCertificate>`要素の子要素として指定すると、トークンの暗号化と復号化に使用される X.509 証明書の場所と検証の設定を指定します。 要素`<certificateReference>`は<xref:System.ServiceModel.Configuration.CertificateReferenceElement>クラスによって表されます。
