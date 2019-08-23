---
title: <message> の <wsDualHttpBinding>
ms.date: 03/30/2017
ms.assetid: 75101744-eed8-4d61-91f4-5fc4473a21f2
ms.openlocfilehash: 796c6bf5df541e525624a609fcfba255eda673cd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931475"
---
# <a name="message-of-wsdualhttpbinding"></a>\<wsDualHttpBinding > の\<メッセージ >
WsDualHttpBinding > のメッセージレベルのセキュリティを[ \<](wsdualhttpbinding.md)定義します。  
  
 \<system.ServiceModel >  
\<bindings>  
\<wsDualHttpBinding >  
\<binding>  
\<セキュリティ >  
\<message>  
  
## <a name="syntax"></a>構文  
  
```xml  
<message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
         negotiateServiceCredential="Boolean"
         algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
</message>
```  
  
## <a name="type"></a>型  
 <xref:System.ServiceModel.MessageSecurityOverHttp>  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|algorithmSuite|任意。 メッセージの暗号化とキー ラップ アルゴリズムを設定します。 アルゴリズムとキー サイズは、<xref:System.ServiceModel.Security.SecurityAlgorithmSuite> クラスにより決まります。 これらのアルゴリズムは、セキュリティ ポリシー言語 (WS-SecurityPolicy) 仕様で指定されたアルゴリズムにマップされます。<br /><br /> 有効値については、以下を参照してください。 既定値は `Basic256` です。|  
|clientCredentialType|任意。 セキュリティ モード `Message` を使用してクライアント認証を実行するときに使用される資格情報の種類を指定します。 有効値については、以下を参照してください。 既定値は `Windows` です。<br /><br /> この属性は <xref:System.ServiceModel.MessageCredentialType> 型です。|  
|negotiateServiceCredential|任意。 サービス資格情報がクライアントの帯域外で提供されるか、ネゴシエーションのプロセスによってサービスからクライアントに取得されるかを指定するブール値。 そのようなネゴシエーションは、通常のメッセージ交換の準備です。<br /><br /> 場合、`clientCredentialType`属性が [なし]、ユーザー名、またはこの属性を設定、証明書に等しい`false`サービス証明書がクライアントの帯域外で使用可能であり、クライアントがサービス証明書を指定する必要があることを意味 (を使用して、[ \<serviceCertificate >](servicecertificate-of-servicecredentials.md)) で、 [ \<serviceCredentials >](servicecredentials.md)サービス動作。 このモードは、WS-Trust および WS-SecureConversation が実装された SOAP スタックと同時使用できます。<br /><br /> `ClientCredentialType` 属性が `Windows` に設定されている場合、この属性を `false` に設定すると Kerberos ベースの認証が指定されます。 つまり、クライアントとサービスは同じ Kerberos ドメイン内に含める必要があります。 このモードは、Kerberos トークン プロファイル (OASIS WSS TC で定義) に加えて WS-Trust および WS-SecureConversation が実装された SOAP スタックと同時使用できます。 この属性が `true` の場合、SOAP メッセージを介して SPNego 交換をトンネル化する .NET SOAP ネゴシエーションが行われます。<br /><br /> 既定値は `true` です。|  
  
## <a name="algorithmsuite-attribute"></a>algorithmSuite 属性  
  
|値|説明|  
|-----------|-----------------|  
|Basic128|Aes128 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。|  
|Basic192|Aes192 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。|  
|Basic256|Aes256 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。|  
|Basic256Rsa15|メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。|  
|Basic192Rsa15|メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。|  
|TripleDes|TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa-oaep-mgf1p を使用します。|  
|Basic128Rsa15|メッセージの暗号化には Aes128 を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。|  
|TripleDesRsa15|TripleDes 暗号化を使用し、メッセージ ダイジェストには Sha1 を、キー ラップには Rsa15 を使用します。|  
|Basic128Sha256|メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。|  
|Basic192Sha256|メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。|  
|Basic256Sha256|メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。|  
|TripleDesSha256|メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa-oaep-mgf1p を使用します。|  
|Basic128Sha256Rsa15|メッセージの暗号化には Aes128 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。|  
|Basic192Sha256Rsa15|メッセージの暗号化には Aes192 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。|  
|Basic256Sha256Rsa15|メッセージの暗号化には Aes256 を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。|  
|TripleDesSha256Rsa15|メッセージの暗号化には TripleDes を使用し、メッセージ ダイジェストには Sha256 を、キー ラップには Rsa15 を使用します。|  
  
## <a name="clientcredentialtype-attribute"></a>clientCredentialType 属性  
  
|値|説明|  
|-----------|-----------------|  
|なし|サービスが匿名クライアントと対話できるようになります。 サービス側では、サービスがクライアントの資格情報を必要としないことを示しています。 クライアント側では、クライアントがクライアントの資格情報を提示しないことを示しています。|  
|Windows|SOAP 交換を、Windows 資格情報の認証されたコンテキストで行うことが可能になります。 `negotiateServiceCredential` 属性が `true` に設定されている場合、SSPI ネゴシエーションと Kerberos (同時使用可能な標準) のいずれかが実行されます。|  
|UserName|サービスが、UserName 資格情報を使用したクライアントの認証を要求できるようにします。 WCF では、パスワードダイジェストの送信や、パスワードを使用したキーの派生、およびメッセージセキュリティのためのこのようなキーの使用はサポートされていません。 そのため、ユーザー名の資格情報を使用する場合、WCF はトランスポートがセキュリティで保護されることを強制します。 この資格情報モードは、`negotiateServiceCredential` 属性に基づいて、同時実行可能な交換か、同時実行できないネゴシエーションのいずれかになります。|  
|証明書|証明書を使用したクライアントの認証を、サービスで要求することが可能になります。 メッセージのセキュリティ モードが使用されており、`negotiateServiceCredential` 属性が `false` に設定されている場合、クライアントをサービス証明書で準備する必要があります。|  
|IssuedToken|カスタム トークン (通常はセキュリティ トークン サービスにより発行される) を指定します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<security>](security-of-wsdualhttpbinding.md)|[ \<WsDualHttpBinding >](wsdualhttpbinding.md)のセキュリティ機能を定義します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.WSDualHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.WSDualHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>
- <xref:System.ServiceModel.MessageSecurityOverHttp>
- [サービスおよびクライアントのセキュリティ保護](../../../wcf/feature-details/securing-services-and-clients.md)
- [バインディング](../../../wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
