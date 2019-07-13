---
title: <network> 要素 (ネットワーク設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#network
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/network
helpviewer_keywords:
- <network> element
- network element
ms.assetid: 2c2c6ad4-ed11-48ab-b28e-2bc0ba9b42c7
ms.openlocfilehash: c411e00026f03fdb355664049f8db00f3c800352
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674455"
---
# <a name="network-element-network-settings"></a>\<ネットワーク > 要素 (ネットワーク設定)
外部の簡易メール転送プロトコル (SMTP) サーバーのネットワーク オプションを構成します。  
  
 \<configuration>  
\<system.net>  
\<mailSettings>  
\<smtp>  
\<network>  
  
## <a name="syntax"></a>構文  
  
```xml  
<network  
  clientDomain="string"   
  defaultCredentials="true|false"  
  enableSsl="true|false"  
  host="string"   
  password="string"  
  port="integer"   
  targetName="string"  
  userName="string"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`clientDomain`|SMTP メール サーバーに接続する最初の SMTP プロトコル要求に使用するクライアントのドメイン名を指定します。 既定値は、要求を送信するローカル コンピューターのローカル ホスト名です。|  
|`defaultCredentials`|SMTP トランザクションで、SMTP メール サーバーへのアクセスに既定のユーザー資格情報を使用するかどうかを指定します。 既定値は `false` です。|  
|`enableSsl`|SMTP メール サーバーへのアクセスに SSL が使用されるかどうかを指定します。 既定値は `false` です。|  
|`host`|SMTP トランザクションで使用する SMTP メール サーバーのホスト名を指定します。 この属性には、既定値はありません。|  
|`password`|SMTP メール サーバーへの認証に使用するパスワードを指定します。 この属性には、既定値はありません。|  
|`port`|SMTP メール サーバーへの接続に使用するポート番号を指定します。 既定値は 25 です。|  
|`targetName`|SMTP トランザクションで拡張保護を使用する場合は、認証に使用するサービス プロバイダー名 (SPN) を指定します。 この属性には、既定値はありません。|  
|`userName`|SMTP メール サーバーへの認証に使用するユーザー名を指定します。 この属性には、既定値はありません。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<smtp> 要素 (ネットワーク設定)](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|簡易メール転送プロトコル (SMTP) 電子メールの送信オプションを構成します。|  
  
## <a name="remarks"></a>Remarks  
 一部の SMTP サーバーでは、自分でを使用する前に、サーバーに対して認証することが必要です。 ホストの既定のネットワーク資格情報を使用して自分で認証を設定する場合、`defaultCredentials`属性を`true`します。 <xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`defaultCredentials`該当する構成ファイルからの属性。  
  
 基本認証 (ユーザー名とパスワード) SMTP サーバーに認証を使用することもできます。 このオプションを使用するには、有効なユーザー名とパスワードを指定した SMTP サーバーを指定する必要があります。  
  
> [!NOTE]
>  基本認証で送信、`userName`と`password`暗号化せずに、サーバーの値。 資格情報を表示でき、それらを使用して、サーバーに接続するネットワーク トラフィックを監視している人ことができます。 Kerberos または NT LAN Manager (NTLM。) より安全な認証メカニズムの使用を検討する必要があります。場合`defaultCredentials`は`true`サーバーは、これらのプロトコルをサポートしている場合、Kerberos または NTLM が使用されます。  
  
 基本認証と既定ネットワーク資格情報オプションは相互に排他的です。設定した場合`defaultCredentials`に`true`ユーザー名とパスワードを指定し、既定のネットワーク資格情報を使用すると、および、基本認証データは無視されます。  
  
 基本認証を指定する場合、`userName`も指定する必要があります、`password`認証メール サーバーに自分でします。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`userName`該当する構成ファイルからの属性。 <xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`password`該当する構成ファイルからの属性。 A`password`は、通常セキュリティ上の理由から、構成ファイルに入力することができません属性。  
  
 `clientDomain`属性は、SMTP サーバーへの最初の SMTP プロトコル要求で使用されるクライアントのドメイン名を変更します。 `clientDomain`属性は、既定で使用されるローカル ホスト名ではなく、ローカル コンピューターの完全修飾ドメイン名に設定することができます。 これは、SMTP プロトコルの標準とコンプライアンスの向上を提供します。 既定値は、要求を送信するローカル コンピューターのローカル ホスト名です。 <xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`clientDomain`該当する構成ファイルからの属性。  
  
 `targetName`属性は、拡張保護を使用する場合、認証に使用します。 フォームの既定値は"SMTPSVC/\<ホスト >"を\<ホスト > は、SMTP メール サーバーのホスト名。 <xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`targetName`該当する構成ファイルからの属性。  
  
 `enableSsl`属性は、SMTP メール サーバーへのアクセスに SSL が使用されるかどうかを指定します。 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>クラスのみをサポート SMTP サービスの拡張機能のセキュリティで保護された SMTP トランスポート層セキュリティ経由で RFC 3207 で定義されています。 このモードでは、SMTP セッションの非暗号化チャネルで開始し、STARTTLS コマンドが SSL を使用してセキュリティで保護された通信を切り替えるためにサーバーにクライアントによって発行されたします。 詳細についてはインターネット技術標準化委員会 (IETF) によって発行された RFC 3207 を参照してください。  
  
 代替の接続方法は、任意のプロトコルのコマンドを送信する前の SSL セッションの事前の確立します。 この接続方法が SMTPS とも呼ばれますが、既定ではポート 465 を使用します。 SSL を使用してこの代替の接続方法は現在サポートされていません。  
  
 <xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>プロパティを使用しての現在の値を取得すること、`enableSsl`該当する構成ファイルからの属性。  
  
## <a name="example"></a>例  
 次の例では、既定のネットワーク資格情報を使用して電子メールを送信する適切な SMTP パラメーターを指定します。  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          clientDomain="www.contoso.com"  
          defaultCredentials="true"  
          enableSsl="false"  
          host="mail.contoso.com"  
          port="25"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Net.Configuration.SmtpNetworkElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
