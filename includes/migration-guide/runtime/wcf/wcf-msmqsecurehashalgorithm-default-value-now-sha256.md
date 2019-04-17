---
ms.openlocfilehash: ce8e162e11802de1b06bfbc63d5c55de67ef23df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236226"
---
### <a name="wcf-msmqsecurehashalgorithm-default-value-is-now-sha256"></a>WCF MsmqSecureHashAlgorithm の既定値が SHA256 になった

|   |   |
|---|---|
|説明|.NET Framework 4.7.1 以降では、Msmq メッセージの WCF での既定のメッセージ署名アルゴリズムは SHA256 です。 .NET Framework 4.7 以前のバージョンでは、既定のメッセージ署名アルゴリズムは SHA1 です。|
|提案される解決策|.NET Framework 4.7.1 以降でこの変更に関する互換性の問題が発生した場合は、次の行を app.config ファイルの <code>&lt;runtime&gt;</code> セクションに追加することで、変更を無効にできます。<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.ServiceModel.UseSha1InMsmqEncryptionAlgorithm=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|スコープ|マイナー|
|Version|4.7.1|
|型|ランタイム|
