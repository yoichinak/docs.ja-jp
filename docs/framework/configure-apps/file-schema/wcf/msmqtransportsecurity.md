---
title: <msmqTransportSecurity>
ms.date: 03/30/2017
ms.assetid: 092e911b-ab1b-4069-a26e-6134c3299e06
ms.openlocfilehash: 5899c609b3cf52c4a275ba6fb10c5826fcf37f1e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153010"
---
# <a name="msmqtransportsecurity"></a>\<>
カスタム バインディングの MSMQ トランスポート セキュリティ設定を指定します。  
  
[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<システム.サービスモデル>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<バインディング>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<カスタムバインド>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<バインド>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>**](msmqintegration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>**  
  
## <a name="syntax"></a>構文  
  
```xml  
<msmqTransportSecurity msmqAuthenticationMode="None/Windows/Certificate"
                       msmqEncryptionAlgorithm="RC4Stream/AES"
                       msmqProtectionLevel="None/Sign/EncryptAndSign"
                       msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</msmqTransportSecurity>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|MSMQ トランスポートによるメッセージの認証方法を指定します。 これが `None` に設定されている場合、`msmqProtectionLevel` 属性の値も `None` に設定する必要があります。<br /><br /> 有効な値は次のとおりです。<br /><br /> - なし: 認証なし。<br />- Windows: 認証メカニズムは、Active Directory を使用して、メッセージに関連付けられた SID の X.509 証明書を取得します。 次に、これを使用してキューの ACL がチェックされ、ユーザーがキューに書き込む権限を持っていることが確認されます。<br />- 証明書: チャネルは証明書ストアから証明書を取得します。<br /><br /> 既定値は Windows です。 この属性は <xref:System.ServiceModel.MsmqAuthenticationMode> 型です。|  
|`msmqEncryptionAlgorithm`|メッセージ キュー マネージャー間でメッセージを転送するときに、ネットワーク上でメッセージの暗号化に使用されるアルゴリズムを指定します。 有効な値は次のとおりです。<br /><br /> - RC4ストリーム<br />- AES<br /><br /> 既定値は RC4Stream です。 この属性は <xref:System.ServiceModel.MsmqEncryptionAlgorithm> 型です。|  
|`msmqProtectionLevel`|MSMQ トランスポートのレベルでメッセージをセキュリティで保護する方法を指定します。 暗号化はメッセージの整合性を保証し、EncryptAndSign はメッセージの整合性と否認防止の両方を保証します。つまり、メッセージは実際に送信者から来ており、送信者は彼らが誰であるかを示します。 有効な値は次のとおりです。<br /><br /> - なし:保護なし。<br />- 署名: メッセージは署名されています。<br />- 暗号化と署名: メッセージは暗号化され、署名されています。<br /><br /> 既定値は Sign です。 この属性は <xref:System.Net.Security.ProtectionLevel> 型です。|  
|`msmqSecureHashAlgorithm`|署名の一部としてダイジェストの計算に使用されるアルゴリズムを指定します。 有効な値は次のとおりです。<br /><br /> - MD5<br />- SHA1<br />- SHA256<br />- SHA512<br /><br /> 既定値は SHA1 です。 この属性は <xref:System.ServiceModel.MsmqSecureHashAlgorithm> 型です。<br>MD5 と SHA1 の衝突の問題のため、マイクロソフトは SHA256 以上を推奨します。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<>](msmqintegration.md)|Message Queuing (MSMQ) の送信側または受信側とのやり取りに必要な設定を指定します。|  
|[\<トランスポート>](msmqtransport.md)|ネイティブ MSMQ プロトコルを使用する Windows Communication Foundation (WCF) サービスのキュー通信プロパティを指定します。|  
  
## <a name="remarks"></a>解説  
 トランスポート セキュリティの詳細については、「[トランスポート セキュリティ](../../../wcf/feature-details/transport-security.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [WCF のキュー](../../../wcf/feature-details/queues-in-wcf.md)
- [トランスポート](../../../wcf/feature-details/transports.md)
- [トランスポートの選択](../../../wcf/feature-details/choosing-a-transport.md)
- [バインド](../../../wcf/bindings.md)
- [バインディングの拡張](../../../wcf/extending/extending-bindings.md)
- [カスタム バインディング](../../../wcf/extending/custom-bindings.md)
- [\<カスタムバインド>](custombinding.md)
- [輸送セキュリティ](../../../wcf/feature-details/transport-security.md)
