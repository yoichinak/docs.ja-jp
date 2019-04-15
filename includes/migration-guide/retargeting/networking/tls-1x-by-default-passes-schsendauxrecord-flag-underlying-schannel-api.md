---
ms.openlocfilehash: 377a80e2580d035f63ee757de4687f293b120609
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58761048"
---
### <a name="tls-1x-by-default-passes-the-schsendauxrecord-flag-to-the-underlying-schannel-api"></a>TLS 1.x は既定で SCH_SEND_AUX_RECORD フラグを基になる SCHANNEL API に渡す

|   |   |
|---|---|
|説明|TLS 1.x を使用するとき、.NET Framework は基になる Windows SCHANNEL API に依存します。 .NET Framework 4.6 以降、[SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/desktop/api/schannel/ns-schannel-_schannel_cred) フラグは既定で SCHANNEL に渡されます。 SCHANNEL によって、暗号化するデータが 2 つの別個のレコードに分割されます。1 つ目のレコードはシングル バイトで、2 つ目のレコードは <em>n</em>-1 バイトです。 その結果、まれに、データがシングル レコードに置かれていると想定する既存サーバーとクライアントの間の通信が途切れることがあります。|
|提案される解決策|この変更によって既存サーバーとの接続が途切れる場合、[SCH_SEND_AUX_RECORD](https://docs.microsoft.com/windows/desktop/api/schannel/ns-schannel-_schannel_cred) フラグの送信を無効にし、アプリ構成ファイルの [\<runtime>](~/docs/framework/configure-apps/file-schema/runtime/runtime-element.md)セクションの [\<AppContextSwitchOverrides>](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 要素に次のスイッチを追加することで、データを別個のレコードに分割しない、以前の動作に復元できます。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides&#13;&#10;value=&quot;Switch.System.Net.DontEnableSchSendAuxRecord=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre> <blockquote> [!IMPORTANT] この設定は下位互換性のためにのみ提供されます。 それ以外の目的での使用はお勧めしません。</blockquote> |
|スコープ|エッジ|
|Version|4.6|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Net.Security.SslStream?displayProperty=nameWithType></li><li><xref:System.Net.ServicePointManager?displayProperty=nameWithType></li><li><xref:System.Net.Http.HttpClient?displayProperty=nameWithType></li><li><xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType></li><li><xref:System.Net.HttpWebRequest?displayProperty=nameWithType></li><li><xref:System.Net.FtpWebRequest?displayProperty=nameWithType></li></ul>|

