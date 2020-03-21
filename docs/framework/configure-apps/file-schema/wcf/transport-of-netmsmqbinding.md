---
title: <transport> の <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 72e1b338-39f0-4af1-a5d9-7a2fb79f6a0b
ms.openlocfilehash: cc47c01cccc931e81ba57ab37ad9e3accfaa693b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152932"
---
# <a name="transport-of-netmsmqbinding"></a>\<\<転送>の>
トランスポートのセキュリティ設定を定義します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<システム.サービスモデル>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<バインディング>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>をバインドします。**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<バインド>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<セキュリティ>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<輸送>**  
  
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
|msmqAuthenticationMode|MSMQ トランスポートによるメッセージの認証方法を指定します。 有効な値は次のとおりです。<br /><br /> - なし: 認証なし。<br />- Windows ドメイン: 認証メカニズムは、Active Directory を使用して、メッセージに関連付けられたセキュリティ識別子の X.509 証明書を取得します。 次に、これを使用してキューの ACL がチェックされ、ユーザーがキューへの書き込み権限を持っていることが確認されます。<br />- 証明書: チャネルは証明書ストアから証明書を取得します。<br /><br /> 既定では、 `WindowsDomain`です。<br /><br /> この属性が `None` に設定されている場合、`msmqProtectionLevel` 属性も `None` に設定する必要があります。 この属性は <xref:System.ServiceModel.MsmqAuthenticationMode> 型です。|  
|msmqEncryptionAlgorithm|メッセージ キュー マネージャー間でメッセージを転送するときに、ネットワーク上でメッセージの暗号化に使用されるアルゴリズムを指定します。 有効な値は次のとおりです。<br /><br /> - RC4ストリーム<br />- AES<br />- デフォルト値は`RC4Stream`です。 この属性は <xref:System.ServiceModel.MsmqEncryptionAlgorithm> 型です。|  
|msmqProtectionLevel|MSMQ トランスポートのレベルでメッセージをセキュリティで保護する方法を指定します。 暗号化を行うとメッセージの整合性が確保されますが、署名および暗号化を使用するとメッセージの整合性と否認防止の両方が確保されます。 つまり、メッセージは実際に送信者から来て、送信者は彼らが誰であるかを言う。 有効な値は次のとおりです。<br /><br /> - なし:保護なし。<br />- 署名: メッセージは署名されています。<br />- 暗号化と署名: メッセージは暗号化され、署名されています。<br />- デフォルトは`Sign`です。|  
|msmqSecureHashAlgorithm|メッセージ ダイジェストの計算に使用されるハッシュ アルゴリズムを指定します。 有効な値は次のとおりです。<br /><br /> - MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> 既定では、 `SHA1`です。 この属性は <xref:System.ServiceModel.MsmqSecureHashAlgorithm> 型です。<br>MD5 と SHA1 の衝突の問題のため、マイクロソフトは SHA256 以上を推奨します。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<セキュリティ>](security-of-netmsmqbinding.md)|キューに置かれているトランスポートのセキュリティ設定を定義します。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [WCF のキュー](../../../wcf/feature-details/queues-in-wcf.md)
- [Securing Services and Clients](../../../wcf/feature-details/securing-services-and-clients.md)
- [バインド](../../../wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<バインド>](bindings.md)
