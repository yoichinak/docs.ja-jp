---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235626"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>終了時に WinRT ストリーム アダプターで FlushAsync が自動的に呼び出されなくなりました

|   |   |
|---|---|
|説明|Windows ストア アプリの Windows ランタイム ストリーム アダプターで、Dispose メソッドから FlushAsync メソッドが呼び出されなくなりました。|
|提案される解決策|この変更は透過的である必要があります。 開発者は次のようなコードを記述して以前の動作を復元できます。<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|スコープ|透明|
|Version|4.5.1|
|型|ランタイム|
