---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: da8ea128466457409334cd0b4ee3246a923f969a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941929"
---
# <a name="certificatereference"></a>\<certificateReference >
証明書ストアの x.509 証明書を検索して検証するために使用する設定を指定します。  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<serviceCertificate>  
\<certificateReference >  
  
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
|storeName|X.509 証明書ストアの名前。 既定値は "My" です。 任意。|  
|storeLocation|X.509 証明書ストアの場所を示す値です。<xref:System.Security.Cryptography.X509Certificates.StoreLocation> 既定値は "LocalMachine" です。 任意。|  
|x509FindType|実行する検索の種類を示す値です。<xref:System.Security.Cryptography.X509Certificates.X509FindType> 既定値は "Findbysubjectdistinguishedname です" です。 任意。|  
|findValue|X.509 証明書ストアで検索する値。 任意。|  
|isChainIncluded|証明書チェーンを使用して検証を実行するかどうかを指定します。 既定値は "true" です。検証は、証明書チェーンを使用して実行されます。 任意。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<serviceCertificate >](servicecertificate.md)|トークンの暗号化と復号化に使用される証明書を構成します。|  
  
## <a name="remarks"></a>Remarks  
 要素`<certificateReference>`は、証明書ストア内の x.509 証明書の検索と検証に使用される設定を指定します。 `<serviceCertificate>`要素の子要素として指定されている場合は、トークンの暗号化と復号化に使用される x.509 証明書の場所と検証の設定を指定します。 要素は、 <xref:System.ServiceModel.Configuration.CertificateReferenceElement>クラスによって表されます。 `<certificateReference>`
