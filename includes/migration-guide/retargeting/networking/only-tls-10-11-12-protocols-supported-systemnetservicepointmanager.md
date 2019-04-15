---
ms.openlocfilehash: 8438341d6fcc5cf0415a2cae059bc76477a5c5e0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234474"
---
### <a name="only-tls-10-11-and-12-protocols-supported-in-systemnetservicepointmanager-and-systemnetsecuritysslstream"></a>System.Net.ServicePointManager と System.Net.Security.SslStream で TLS 1.0、1.1、1.2 プロトコルのみサポート

|   |   |
|---|---|
|説明|.NET Framework 4.6 から、<xref:System.Net.ServicePointManager> クラスと <xref:System.Net.Security.SslStream> クラスには、Tls1.0、Tls1.1、Tls 1.2 という 3 つのプロトコルのいずれかを使用することのみが許可されます。 SSL3.0 プロトコルと RC4 の暗号化はサポートされていません。|
|提案される解決策|推奨される軽減策はサーバー側のアプリを Tls1.0、Tls1.1、または Tls1.2 にアップグレードすることです。 これが現実的でない場合、またはクライアント アプリが破損している場合は、次の 2 つの方法のいずれかにより、<xref:System.AppContext?displayProperty=name> クラスを使用してこの機能を除外できます。<ol><li>プログラムで <xref:System.AppContext?displayProperty=name> の互換性スイッチを設定する (説明は[こちら](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)にあります)</li><li>app.config ファイルの <code>&lt;runtime&gt;</code> セクションに次の行を追加する: <code>&lt;AppContextSwitchOverrides value=&quot;Switch.System.Net.DontEnableSchUseStrongCrypto=true&quot;/&gt;</code></li></ol>|
|スコープ|マイナー|
|Version|4.6|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Net.SecurityProtocolType.Ssl3?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.None?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl2?displayProperty=nameWithType></li><li><xref:System.Security.Authentication.SslProtocols.Ssl3?displayProperty=nameWithType></li></ul>|
