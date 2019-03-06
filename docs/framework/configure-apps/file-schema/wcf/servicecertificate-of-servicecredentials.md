---
title: <serviceCertificate> の <serviceCredentials>
ms.date: 03/30/2017
ms.assetid: 597ae6d5-4938-4950-9f5e-b2280e816182
ms.openlocfilehash: bd2d59218ce40639ac04aa7c5cc157fe37eb9937
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57373804"
---
# <a name="servicecertificate-of-servicecredentials"></a>\<serviceCertificate > の\<serviceCredentials >
メッセージ セキュリティ モードを使用しているクライアントへのサービスの認証に使用する X.509 証明書を指定します。  
  
 \<system.ServiceModel >  
\<<behaviors>  
\<serviceBehaviors>  
\<behavior>  
\<serviceCredentials>  
\<serviceCertificate >  
  
## <a name="syntax"></a>構文  
  
```xml  
<serviceCertificate findValue="String"
                    storeLocation="LocalMachine/CurrentUser"
                    storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
                    x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`findValue`|X.509 証明書ストアで検索する値を含む文字列。 属性に含まれている型は、指定された X509FindType の要件を満たしている必要があります。 既定値は空の文字列です。|  
|`storeLocation`|クライアントがサーバーの証明書の検証に使用する X.509 証明書ストアの場所を指定します。 以下の値が有効です。<br /><br /> -LocalMachine: ローカル マシンに割り当てられている証明書ストア。<br />-CurrentUser: 現在のユーザーに割り当てられている証明書ストア。<br /><br /> 既定は LocalMachine です。|  
|`storeName`|開く X.509 証明書ストアの名前を指定します。 以下の値が有効です。<br /><br /> -AddressBook:他のユーザーの証明書ストア。<br />-   AuthRoot:サード パーティ証明機関 (Ca) 証明書ストア。<br />-CertificatAuthority:中間証明機関 (Ca) 証明書ストア。<br />-許可されていません。失効した証明書の証明書ストア。<br />-My:個人用証明書の証明書ストア。<br />ルート:信頼されたルート証明機関 (Ca) 証明書ストア。<br />-TrustedPeople:直接信頼されたユーザーとリソースの証明書ストア。<br />-TrustedPublisher:直接信頼された発行者の証明書ストア。<br /><br /> 既定値は My です。|  
|`x509FindType`|実行する X.509 検索の種類を定義します。 以下の値が有効です。<br /><br /> -FindByThumbprint<br />-   FindBySubjectName<br />-FindBySubjectDistinguishedName<br />-   FindByIssuerName<br />-FindByIssuerDistinguishedName<br />-   FindBySerialNumber<br />-   FindByTimeValid<br />-   FindByTimeNotYetValid<br />-   FindByTemplateName<br />-   FindByApplicationPolicy<br />-FindByCertificatePolicy<br />-FindByExtension<br />-   FindByKeyUsage<br />-   FindBySubjectKeyIdentifier<br /><br /> 
  `findValue` 属性に含まれている型は、指定された X509FindType の要件を満たしている必要があります。<br /><br /> 既定値は FindBySubjectDistinguishedName です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<serviceCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecredentials.md)|サービスの認証に使用される資格情報と、クライアントの資格情報検証関連の設定を指定します。|  
  
## <a name="remarks"></a>Remarks  
 メッセージ セキュリティ モードを使用しているクライアントへのサービスの認証に使用する X.509 証明書を指定するには、この要素を使用します。 定期的に更新される証明書を使用している場合は、証明書のサムプリントが変更されます。 その場合、証明書を同じサブジェクト名で再発行できるため、`x509FindType` としてサブジェクト名を使用します。  
  
 詳細については、要素を使用して、次を参照してください。[方法。クライアント資格情報の値を指定](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateServiceElement>
- <xref:System.ServiceModel.Configuration.ServiceCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.Description.ServiceCredentials.ServiceCertificate%2A>
- [方法: クライアント資格情報の値を指定します。](../../../../../docs/framework/wcf/how-to-specify-client-credential-values.md)
- [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
