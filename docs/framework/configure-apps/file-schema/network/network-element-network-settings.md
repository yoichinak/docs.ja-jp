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
ms.openlocfilehash: f7cfcc3b9d5a717c23175cd15aa48ae97c828e57
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154817"
---
# <a name="network-element-network-settings"></a>\<ネットワーク>要素 (ネットワーク設定)
外部簡易メール転送プロトコル (SMTP) サーバーのネットワーク オプションを構成します。  

[**\<構成>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<メール設定>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<ネットワーク>**

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
|`clientDomain`|SMTP メール サーバーに接続するために最初の SMTP プロトコル要求で使用するクライアント ドメイン名を指定します。 既定値は、要求を送信するローカル コンピューターのローカル ホスト名です。|  
|`defaultCredentials`|SMTP トランザクションの SMTP メール サーバーにアクセスするために既定のユーザー資格情報を使用するかどうかを指定します。 既定値は `false` です。|  
|`enableSsl`|SMTP メール サーバーへのアクセスに SSL を使用するかどうかを指定します。 既定値は `false` です。|  
|`host`|SMTP トランザクションに使用する SMTP メール サーバーのホスト名を指定します。 この属性には既定値はありません。|  
|`password`|SMTP メール サーバーへの認証に使用するパスワードを指定します。 この属性には既定値はありません。|  
|`port`|SMTP メール サーバーへの接続に使用するポート番号を指定します。 既定値は 25 です。|  
|`targetName`|SMTP トランザクションに拡張保護を使用する場合に認証に使用するサービス プロバイダー名 (SPN) を指定します。 この属性には既定値はありません。|  
|`userName`|SMTP メール サーバーへの認証に使用するユーザー名を指定します。 この属性には既定値はありません。|  
  
### <a name="child-elements"></a>子要素  
 [なし] :  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<smtp>要素 (ネットワーク設定)](smtp-element-network-settings.md)|簡易メール転送プロトコル (SMTP) メール送信オプションを構成します。|  
  
## <a name="remarks"></a>解説  
 一部の SMTP サーバーでは、使用する前にサーバーに対して自分自身を認証する必要があります。 ホストのデフォルトのネットワーク資格情報を使用して自分自身を認証する場合は、属性を`defaultCredentials`に`true`設定します。 この<xref:System.Net.Configuration.SmtpNetworkElement.DefaultCredentials%2A?displayProperty=nameWithType>プロパティを使用して、適用可能な構成ファイルから`defaultCredentials`属性の現在の値を取得できます。  
  
 基本認証 (ユーザー名とパスワード) を使用して、SMTP サーバーに対して自分自身を認証することもできます。 このオプションを使用するには、指定した SMTP サーバーの有効なユーザー名とパスワードを指定する必要があります。  
  
> [!NOTE]
> 基本認証では、 `userName` `password`と の値が暗号化されずにサーバーに送信されます。 ネットワーク トラフィックを監視しているユーザーは誰でも、資格情報を表示して、サーバーに接続するために使用できます。 Kerberos や NT LAN マネージャ (NTLM) など、より安全な認証メカニズムの使用を検討する必要があります。が`defaultCredentials`設定`true`されている場合、サーバーがこれらのプロトコルをサポートしている場合は、Kerberos または NTLM が使用されます。  
  
 基本認証と既定のネットワーク資格情報のオプションは相互に排他的です。ユーザー名と`defaultCredentials`パスワード`true`を指定して設定すると、デフォルトのネットワーク資格情報が使用され、基本認証データは無視されます。  
  
 基本認証の 場合は`userName`、 を指定する場合は`password`、メール サーバーに対する認証を自分で指定する必要もあります。  
  
 この<xref:System.Net.Configuration.SmtpNetworkElement.UserName%2A?displayProperty=nameWithType>プロパティを使用して、適用可能な構成ファイルから`userName`属性の現在の値を取得できます。 この<xref:System.Net.Configuration.SmtpNetworkElement.Password%2A?displayProperty=nameWithType>プロパティを使用して、適用可能な構成ファイルから`password`属性の現在の値を取得できます。 通常`password`、セキュリティ上の理由から、属性は構成ファイルに入力されません。  
  
 この`clientDomain`属性は、最初の SMTP プロトコル要求で使用されるクライアント ドメイン名を SMTP サーバーに変更します。 属性`clientDomain`は、デフォルトで使用されるローカルホスト名ではなく、ローカルマシンの完全修飾ドメイン名に設定できます。 これにより、SMTP プロトコル標準への準拠性が向上します。 既定値は、要求を送信するローカル コンピューターのローカル ホスト名です。 この<xref:System.Net.Configuration.SmtpNetworkElement.ClientDomain%2A?displayProperty=nameWithType>プロパティを使用して、適用可能な構成ファイルから`clientDomain`属性の現在の値を取得できます。  
  
 この`targetName`属性は、拡張保護を使用する場合に認証に使用されます。 デフォルト値は、ホスト>が\<\<SMTP メール・サーバーのホスト名である「SMTPSVC/ホスト・>」の形式です。 この<xref:System.Net.Configuration.SmtpNetworkElement.TargetName%2A?displayProperty=nameWithType>プロパティを使用して、適用可能な構成ファイルから`targetName`属性の現在の値を取得できます。  
  
 この`enableSsl`属性は、SSL を使用して SMTP メール・サーバーにアクセスするかどうかを指定します。 この<xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>クラスは、RFC 3207 で定義されているトランスポート層セキュリティ経由でのセキュリティで保護された SMTP の SMTP サービス拡張のみをサポートします。 このモードでは、SMTP セッションは暗号化されていないチャネルで開始され、クライアントから STARTTLS コマンドが発行され、SSL を使用した通信のセキュリティ保護に切り替わります。 詳細については、インターネット技術標準化委員会 (IETF) が発行した RFC 3207 を参照してください。  
  
 代替接続方式は、プロトコル・コマンドが送信される前に SSL セッションが事前に確立される場所です。 この接続方法は SMTPS と呼ばれる場合があり、デフォルトではポート 465 が使用されます。 SSL を使用するこの代替接続方式は、現在サポートされていません。  
  
 この<xref:System.Net.Configuration.SmtpNetworkElement.EnableSsl%2A?displayProperty=nameWithType>プロパティを使用して、適用可能な構成ファイルから`enableSsl`属性の現在の値を取得できます。  
  
## <a name="example"></a>例  
 次の例では、既定のネットワーク資格情報を使用して電子メールを送信するための適切な SMTP パラメーターを指定します。  
  
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
- [ネットワーク設定スキーマ](index.md)
