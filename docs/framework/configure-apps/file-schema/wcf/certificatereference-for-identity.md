---
title: <certificateReference> for <identity>
ms.date: 03/30/2017
ms.assetid: ac359c65-c22d-42d2-97de-db53b77cebdb
ms.openlocfilehash: 3b7779ac00c2fca6300c12ac18ff2d5f6b868424
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138815"
---
# <a name="certificatereference-for-identity"></a>\<certificateReference > の\<identity >
X.509 証明書検証の設定を指定します。 この id を持つエンドポイントに接続するセキュリティで保護された Windows Communication Foundation (WCF) クライアントは、サーバーによって提示されるクレームがこの id を構築するために使用する id クレームを含めることを確認します。  
  
 \<identity>  
\<certificateReference>  
  
## <a name="syntax"></a>構文  
  
```xml  
<certificateReference findValue="String"
                      isChainIncluded="Boolean"
                      storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                      storeLocation="LocalMachine/CurrentUser"
                      X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier">
</certificateReference>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|findValue|X.509 証明書ストアで検索する値を指定します。 この属性に格納されている型は、指定された `X509FindType` 値の要件を満たす必要があります。 既定値は空の文字列です。|  
|isChainIncluded|証明書チェーンを使用して検証を行うかどうかを指定するブール値です。|  
|storeLocation|クライアントがサーバーの証明書の検証に使用できる証明書ストアの場所を指定します。<br /><br /> 以下の値が有効です。<br /><br /> -   LocalMachine:ローカル コンピューターに割り当てられている証明書ストア。<br />-   CurrentUser:現在のユーザーに割り当てられている証明書ストア。<br /><br /> 既定値は LocalMachine です。<br /><br /> この属性は <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 型です。|  
|storeName|開く X.509 証明書ストアの名前を指定します。<br /><br /> 以下の値が有効です。<br /><br /> -AddressBook:他のユーザーの証明書ストア。<br />-   AuthRoot:サード パーティ証明機関 (Ca) 証明書ストア。<br />-[証明機関]:中間 ca 証明書ストア。<br />-許可されていません。失効した証明書の証明書ストア。<br />-My:個人用証明書の証明書ストア。<br />ルート:信頼されたルート Ca 証明書ストア。<br />-TrustedPeople:直接信頼されたユーザーとリソースの証明書ストア。<br />-TrustedPublisher:直接信頼された発行者の証明書ストア。<br /><br /> 既定値は、My です。<br /><br /> この属性は <xref:System.Security.Cryptography.X509Certificates.StoreName> 型です。|  
|X509FindType|実行する X.509 検索の種類を指定します。 `findValue` 属性に含まれている型は、指定された X509FindType の要件を満たしている必要があります。<br /><br /> 以下の値が有効です。<br /><br /> -FindByThumbPrint<br />-   FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> 既定値は FindBySubjectDistinguishedName です。<br /><br /> この属性は <xref:System.Security.Cryptography.X509Certificates.X509FindType> 型です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identity>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする設定を指定します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.CertificateReferenceElement>
- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
