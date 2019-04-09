---
title: <socket> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/socket
- http://schemas.microsoft.com/.NetConfiguration/v2.0#socket
helpviewer_keywords:
- <socket> element
- socket element
ms.assetid: 366c634c-7d16-478f-aedf-053eda94a1a0
ms.openlocfilehash: 82bfe3b6e3107ff787716657dbf0b31dcadde911
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160161"
---
# <a name="socket-element-network-settings"></a>\<ソケット > 要素 (ネットワーク設定)
ソケット操作が完了ポートを使用するかどうかを指定します。  
  
 \<configuration>  
\<system.net>  
\<settings>  
\<socket>  
  
## <a name="syntax"></a>構文  
  
```xml  
<socket  
  alwaysUseCompletionPortsForConnect="true|false"  
  alwaysUseCompletionPortsForAccept="true|false"  
  ipProtectionLevel="EdgeRestricted|Restricted|Unrestricted|Unspecified"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|**属性**|**説明**|  
|-------------------|---------------------|  
|`alwaysUseCompletionPortsForAccept`|受け入れメソッド呼び出しの場合、ソケットで常に完了ポートを使用するかどうかを示します。 既定値は `false` です。|  
|`alwaysUseCompletionPortsForConnect`|Connect メソッドの呼び出しの場合、ソケットで常に完了ポートを使用するかどうかを示します。 既定値は `false` です。|  
|`ipProtectionLevel`|既定値を指定します<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>ソケットを使用します。 既定値は、Windows のバージョンによって異なります。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|**要素**|**説明**|  
|-----------------|---------------------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<xref:System.Net> 名前空間の基本的なネットワーク オプションを構成します。|  
  
## <a name="remarks"></a>Remarks  
 `alwaysUseCompletionPortsForAccept`と`alwaysUseCompletionPortsForConnect`内のクラスで属性を使用して、完了ポートの使用に関する既定の動作を指定、 <xref:System.Net.Sockets?displayProperty=nameWithType>.namespace します。 高パフォーマンス サーバー アプリケーションは、完了ポートがお勧めします。  
  
 既定値、`alwaysUseCompletionPortsForAccept`と`alwaysUseCompletionPortsForConnect`属性は**false**します。  
  
 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForAccept%2A>の現在の値を取得するために使用できる、`alwaysUseCompletionPortsForAccept`該当する構成ファイルからの属性。 <xref:System.Net.Configuration.SocketElement.AlwaysUseCompletionPortsForConnect%2A>の現在の値を取得するために使用できる、`alwaysUseCompletionPortsForConnect`該当する構成ファイルからの属性。  
  
 `ipProtectionLevel`属性を既定値を指定します<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>ソケットを使用します。 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>プロパティなど、リンク ローカルまたはサイト ローカル プレフィックスを同じアドレスを特定のスコープ、IPv6 ソケットの制限の構成を使用できます。 このオプションにより、IPv6 ソケットに対するアクセス制限を設定できます。 この制限により、プライベート LAN で実行されるアプリケーションを外部からの攻撃に対して簡単かつ堅牢に強化できます。 このオプションは、拡大変換されますか、適切な場合は、パブリックおよびプライベートのユーザーまたは必要に応じて、同じサイトにのみアクセスを制限することから無制限のアクセスを有効にすると、リッスン ソケットのスコープを絞り込みます。  
  
 これは、`ipProtectionLevel`属性の設定が最初に受信トラフィックのみに影響します。  
  
-   着信接続をソケットでリッスンしている TCP サーバー。  
  
-   ソケットでのパケットを受信 UDP アプリケーションです。  
  
 この構成設定では既に確立されている TCP 接続が (トラフィックは両方向に無制限) には影響しません UDP パケットを送信するアプリケーションには影響しません。  
  
 使用可能な値を`ipProtectionLevel`属性の設定が指定された定義済みの保護レベルに対応して、<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>列挙体として次のとおりです。  
  
|**属性の値**|**説明**|  
|-|-|  
|EdgeRestricted|IP 保護レベルはエッジ制限付きです。 この値は、インターネット経由で動作するように設計アプリケーションによって使用されます。 この設定は、Windows Teredo 実装を使用して、ネットワーク アドレス変換 (NAT) トラバーサルを許可しません。 これらのアプリケーションが IPv4 のファイアウォールをバイパスため、開かれたポートに送信するインターネット攻撃に対するアプリケーションのセキュリティを強化する必要があります。 Windows Server 2003 および Windows XP では、ソケットの IP 保護レベルの既定値はエッジ制限付きです。|  
|Restricted|IP 保護レベルは、制限付きです。 この値については、インターネットのシナリオを実装しないイントラネット アプリケーションで使用します。 これらのアプリケーションは通常、テストもインターネット スタイルの攻撃に対して強固です。 この設定は、受信トラフィックはリンク ローカルのみに制限されます。|  
|無制限|IP 保護レベルは制限されません。 この値は組み込まれている IPv6 NAT traversal 機能を活用するアプリケーションを含め、インターネット経由で動作するようにデザインされたアプリケーションによって使用される Windows (Teredo の使用例) にします。 これらのアプリケーションが IPv4 のファイアウォールをバイパスため、開かれたポートに送信するインターネット攻撃に対するアプリケーションのセキュリティを強化する必要があります。 Windows Server 2008 R2 および Windows Vista では、ソケットの IP 保護レベルの既定値は制限されません。|  
|指定されていません。|IP 保護レベルでは、指定されていません。 Windows 7 および Windows Server 2008 R2 では、ソケットの IP 保護レベルの既定値が指定されていません。|  
  
 既定値、`ipProtectionLevel`属性が**未指定**します。  
  
 <xref:System.Net.Configuration.SocketElement.IPProtectionLevel%2A>プロパティを使用しての現在の値を取得すること、`ipProtectionLevel`該当する構成ファイルからの属性。  
  
## <a name="configuration-files"></a>構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル (Machine.config) で使用できます。  
  
## <a name="example"></a>例  
 次の例は、完了ポートを使用することを指定する方法と、既定<xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>制限する必要があります。  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <socket  
        alwaysUseCompletionPortsForAccept="true"  
        alwaysUseCompletionPortsForConnect="true"  
        ipProtectionLevel="Unrestricted"  
       />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SocketElement?displayProperty=nameWithType>
- <xref:System.Net.Sockets?displayProperty=nameWithType>
- <xref:System.Net.Sockets.IPProtectionLevel?displayProperty=nameWithType>
- <xref:System.Net.Sockets.SocketOptionName.IPProtectionLevel?displayProperty=nameWithType>
- [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
