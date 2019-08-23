---
title: <transport> の <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: ede4103f9c8f2f73ac34036fe7a58242e32350e0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934692"
---
# <a name="transport-of-netmsmqbinding"></a>\<netmsmqbinding \<> のトランスポート >
トランスポートのセキュリティ設定を定義します。  
  
 \<system.ServiceModel >  
\<bindings>  
\<netMsmqBinding>  
\<binding>  
\<セキュリティ >  
\<transport>  
  
## <a name="syntax"></a>構文  
  
```xml  
<netMsmqBinding>
  <binding>
    <security>
      <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
                 msmqEncryptionAlgorithm="RC4Stream/AES"
                 msmqProtectionLevel="None/Sign/EncryptAndSign"
                 msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
    </security>
  </binding>
</netMsmqBinding>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|msmqAuthenticationMode|MSMQ トランスポートによるメッセージの認証方法を指定します。 有効な値は次のとおりです。<br /><br /> 存在認証なし。<br />WindowsDomain認証メカニズムでは、Active Directory を使用して、メッセージに関連付けられているセキュリティ識別子の x.509 証明書を取得します。 次に、これを使用してキューの ACL がチェックされ、ユーザーがキューへの書き込み権限を持っていることが確認されます。<br />証明チャネルは、証明書ストアから証明書を取得します。<br /><br /> 既定値は `WindowsDomain` です。<br /><br /> この属性が `None` に設定されている場合、`msmqProtectionLevel` 属性も `None` に設定する必要があります。 この属性は <xref:System.ServiceModel.MsmqAuthenticationMode> 型です。|  
|msmqEncryptionAlgorithm|メッセージ キュー マネージャー間でメッセージを転送するときに、ネットワーク上でメッセージの暗号化に使用されるアルゴリズムを指定します。 以下の値が有効です。<br /><br /> - RC4Stream<br />-AES<br />-既定値は`RC4Stream`です。 この属性は <xref:System.ServiceModel.MsmqEncryptionAlgorithm> 型です。|  
|msmqProtectionLevel|MSMQ トランスポートのレベルでメッセージをセキュリティで保護する方法を指定します。 暗号化を行うとメッセージの整合性が確保されますが、署名および暗号化を使用するとメッセージの整合性と否認防止の両方が確保されます。 つまり、メッセージは本当にその送信者から送信されていることになり、記載されている送信者が実際の送信者になります。 有効な値は次のとおりです。<br /><br /> 存在保護されません。<br />シャープメッセージは署名されます。<br />EncryptAndSignメッセージは暗号化および署名されます。<br />-既定値は`Sign`です。|  
|msmqSecureHashAlgorithm|メッセージ ダイジェストの計算に使用されるハッシュ アルゴリズムを指定します。 有効な値は次のとおりです。<br /><br /> -   MD5<br />-SHA1<br />-   SHA256<br />-SHA512<br /><br /> 既定値は `SHA1` です。 この属性は <xref:System.ServiceModel.MsmqSecureHashAlgorithm> 型です。<br>MD5 と SHA1 の衝突の問題のため、SHA256 以上をお勧めします。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<security>](security-of-netmsmqbinding.md)|キューに置かれているトランスポートのセキュリティ設定を定義します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [WCF のキュー](../../../wcf/feature-details/queues-in-wcf.md)
- [サービスおよびクライアントのセキュリティ保護](../../../wcf/feature-details/securing-services-and-clients.md)
- [バインディング](../../../wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../misc/binding.md)
