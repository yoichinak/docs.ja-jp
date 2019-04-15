---
ms.openlocfilehash: 9c3eedb7f7d4cd030a12c141b8630876c1ffdb4d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236450"
---
### <a name="throttle-concurrent-requests-per-session"></a>セッションあたりの同時実行される要求のスロットル

|   |   |
|---|---|
|説明|.NET Framework 4.6.2 以前の場合、ASP.NET は同じ Sessionid の要求を順番に実行します。ASP.NET は既定で常にクッキーを経由して Sessionid を発行します。 ページの応答に長い時間がかかる場合、ブラウザーの F5 を押すと、サーバーのパフォーマンスが大幅に低下します。 この修正プログラムでは、キューに置かれた要求を追跡し、特定の制限を超えたときに要求を終了するためのカウンターを追加しました。 既定値は 50 です。 制限に達すると、警告がイベント ログに記録され、HTTP 500 応答は IIS ログに記録される可能性があります。|
|提案される解決策|以前の動作を復元するには、次の設定を web.config ファイルに追加して、新しい動作を無効にできます。<pre><code class="lang-xml">&lt;appSettings&gt;&#13;&#10;&lt;add key=&quot;aspnet:RequestQueueLimitPerSession&quot; value=&quot;2147483647&quot;/&gt;&#13;&#10;&lt;/appSettings&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.7|
|型|再ターゲット中|
