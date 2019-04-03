---
title: <transport> の <msmqIntegrationBinding>
ms.date: 03/30/2017
ms.assetid: 054579e3-7fdd-47df-99ca-952706ba5c8e
ms.openlocfilehash: f404782ed54d27d5dcfdfba126f6992d9badf060
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463398"
---
# <a name="transport-of-msmqintegrationbinding"></a>\<トランスポート > の\<msmqIntegrationBinding >
メッセージ キュー統合トランスポートのセキュリティ設定を定義します。  
  
 \<system.ServiceModel >  
\<bindings>  
msmqIntegrationBinding  
\<binding>  
\<セキュリティ >  
\<transport>  
  
## <a name="syntax"></a>構文  
  
```xml  
<security>
  <transport msmqAuthenticationMode="None/WindowsDomain/Certificate"
             msmqEncryptionAlgorithm="RC4Stream/AES"
             msmqProtectionLevel="None/Sign/EncryptAndSign"
             msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />
</security>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`msmqAuthenticationMode`|MSMQ トランスポートによるメッセージの認証方法を指定します。 これが `None` に設定されている場合、`msmqProtectionLevel` 属性の値も `None` に設定する必要があります。<br /><br /> 以下の値が有効です。<br /><br /> -None。認証はありません。<br />-   WindowsDomain:認証メカニズムでは、Active Directory を使用して、メッセージに関連付けられている SID の X.509 証明書を取得します。 次に、これを使用してキューの ACL がチェックされ、ユーザーがキューに書き込む権限を持っていることが確認されます。<br />-証明書:チャネルは、証明書ストアから証明書を取得します。<br /><br /> 既定値は WindowsDomain です。 この属性は <xref:System.ServiceModel.MsmqAuthenticationMode> 型です。|  
|`msmqEncryptionAlgorithm`|メッセージ キュー マネージャー間でメッセージを転送するときに、ネットワーク上でメッセージの暗号化に使用されるアルゴリズムを指定します。 以下の値が有効です。<br /><br /> -[Rc4stream]<br />-AES<br /><br /> 既定値は RC4Stream です。 この属性は <xref:System.ServiceModel.MsmqEncryptionAlgorithm> 型です。|  
|`msmqProtectionLevel`|MSMQ トランスポートのレベルでメッセージをセキュリティで保護する方法を指定します。 暗号化を行うとメッセージの整合性が確保されますが、EncryptAndSign を使用するとメッセージの整合性と否認防止の両方が確保されます。つまり、メッセージは本当にその送信者から送信されていることになり、記載されている送信者が実際の送信者になります。<br /><br /> -有効な値を以下に示します。<br />-None。保護されません。<br />署名:メッセージは署名されます。<br />-EncryptAndSign:メッセージは暗号化および署名されます。<br /><br /> 既定値は Sign です。 この属性は、ProtectionLevel 型です。|  
|`msmqSecureHashAlgorithm`|-署名の一部としてダイジェストを計算で使用するアルゴリズムを指定します。 以下の値が有効です。<br />-   MD5<br />-SHA1<br />-   SHA256<br />-SHA512<br /><br /> 既定値は SHA1 です。 この属性は <xref:System.ServiceModel.MsmqSecureHashAlgorithm> 型です。<br>MD5 と SHA1 に衝突の問題、SHA256 以上をお勧めします。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|MSMQ バインディングのセキュリティ設定を定義します。|  
  
## <a name="remarks"></a>Remarks  
 この要素は、メッセージ キュー統合トランスポートのセキュリティ設定をカプセル化します。 設定は、メッセージ キュー統合トランスポートとキューに置かれているトランスポートの両方で同じです。 この設定を使用すると、認証モード、暗号化アルゴリズム、セキュア ハッシュ アルゴリズム、および保護レベルを設定できます。  
  
## <a name="see-also"></a>関連項目
- <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement>
- <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement.Transport%2A>
- <xref:System.ServiceModel.MsmqTransportSecurity>
- [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [バインディング](../../../../../docs/framework/wcf/bindings.md)
- [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [サービスとクライアントを構成するためのバインディングの使用](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](../../../../../docs/framework/misc/binding.md)
