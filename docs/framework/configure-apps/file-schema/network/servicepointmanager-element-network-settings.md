---
title: <servicePointManager> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: 407ed85de109a671030eccff8ddd92af91628014
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202210"
---
# <a name="servicepointmanager-element-network-settings"></a>\<servicePointManager > 要素 (ネットワーク設定)
ネットワーク リソースへの接続を構成します。  
  
 \<configuration>  
\<system.net>  
\<settings>  
\<servicePointManager>  
  
## <a name="syntax"></a>構文  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|`checkCertificateName`|システムが証明書の名前、証明書を使用する前にサーバーのホスト名が一致することを確認する必要があるかどうかを指定します。 既定値は `true` です。|  
|`checkCertificateRevocationList`|システムが、証明書を使用する前に、証明書を失効するかどうかをチェックする必要があるかどうかを指定します。 既定値は `false` です。|  
|`dnsRefreshTimeout`|(ミリ秒単位)、DNS ラウンド ロビン オプションと共に、どのくらいの時間ドメイン ネーム サービス (DNS) 解決策はキャッシュを指定します。 既定値は 120,000 ミリ秒 (2 分) です。|  
|`enableDnsRoundRobin`|すべてのアドレス、または最初の 1 つだけホストの DNS 解決の戻り値の複数のインターネット プロトコル (IP) アドレスを持つ名前かどうかを指定します。 既定値は `false` です。|  
|`encryptionPolicy`|SSL や TLS セッションに適用する暗号化ポリシーを指定します、<xref:System.Net.ServicePointManager>インスタンス。 使用可能な値がの値に等しい、<xref:System.Net.Security.EncryptionPolicy>列挙体。 使用<xref:System.Security.Authentication.CipherAlgorithmType.Null>暗号化ポリシーが設定されている場合は、必要な`NoEncryption`します。 既定値は `RequireEncryption` です。|  
|`expect100Continue`|POST メソッドが受信することが予想されるかどうかを指定します、`100-continue`サーバーからの応答。 既定値は `true` です。|  
|`useNagleAlgorithm`|サービス ポイントのマネージャーによって制御される接続で Nagle アルゴリズムを使用するかどうかを指定します。 既定値は `true` です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
