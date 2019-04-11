---
ms.openlocfilehash: ce7e2db3f74ec24f47b1c224335451c997c4c349
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761060"
---
### <a name="wcf-binding-with-the-transportwithmessagecredential-security-mode"></a>TransportWithMessageCredential セキュリティ モードを使用する WCF バインド

|   |   |
|---|---|
|説明|.NET Framework 4.6.1 より、TransportWithMessageCredential セキュリティ モードを使用する WCF バインドで署名のない非対称セキュリティ キーの &quot;to&quot; ヘッダーを含むメッセージを取得するように設定できるようになりました。既定では、署名のない &quot;to&quot; ヘッダーは .NET Framework 4.6.1 でも引き続き拒否されます。 これは、アプリケーションが Switch.System.ServiceModel.AllowUnsignedToHeader 構成スイッチを使用するこの新しい動作モードをオプトインした場合にのみ許可されます。|
|提案される解決策|これはオプトイン機能であるため、既存のアプリの動作に影響はないはずです。<br/>新しい動作を使用するかどうかを制御するには、次の構成設定を使用します。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.AllowUnsignedToHeader=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|透明|
|Version|4.6.1|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.ServiceModel.BasicHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.BasicHttpsSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li><li><xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential?displayProperty=nameWithType></li></ul>|

