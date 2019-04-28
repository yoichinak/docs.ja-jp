---
title: <certificateReference>
ms.date: 03/30/2017
ms.assetid: 2ac8bc14-e9f1-48fb-b662-f5991558fbe4
author: BrucePerlerMS
ms.openlocfilehash: 6c9c77f96ff6032de43d9b5a257bc0796a19b858
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667380"
---
# <a name="certificatereference"></a>\<certificateReference>
検索して、証明書ストアに X.509 証明書の検証に使用される設定を指定します。  
  
 \<system.identityModel.services>  
\<federationConfiguration>  
\<serviceCertificate>  
\<certificateReference>  
  
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
|storeName|X.509 証明書ストアの名前。 既定値は"My"です。 省略可能です。|  
|storeLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> X.509 証明書ストアの場所を指定する値。 既定値は、"LocalMachine"です。 省略可能です。|  
|x509FindType|<xref:System.Security.Cryptography.X509Certificates.X509FindType>を実行する検索の種類を指定する値。 既定値は、「findbysubjectdistinguishedname です」です。 任意。|  
|findValue|X.509 証明書ストアで検索する値。 省略可能です。|  
|isChainIncluded|証明書チェーンを使用して検証を実行するかどうかを指定します。 既定値は"true"になります。証明書チェーンを使用して検証します。 省略可能です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|暗号化し、トークン暗号化解除に使用される証明書を構成します。|  
  
## <a name="remarks"></a>Remarks  
 `<certificateReference>`要素を検索し、証明書ストアに X.509 証明書の検証に使用される設定を指定します。 子要素として指定されている場合、`<serviceCertficate>`の暗号化し、トークン暗号化解除に使用される X.509 証明書の場所と検証の設定を指定します。 `<certificateReference>`要素が表される、<xref:System.ServiceModel.Configuration.CertificateReferenceElement>クラス。
