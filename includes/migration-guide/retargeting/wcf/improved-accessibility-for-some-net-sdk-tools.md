---
ms.openlocfilehash: 79005f19ac31ba32e7e468ef61eb867a052eff40
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67858951"
---
### <a name="improved-accessibility-for-some-net-sdk-tools"></a>一部の .NET SDK ツールのアクセシビリティが強化されました

|   |   |
|---|---|
|説明|.NET Framework SDK 4.7.1 では、さまざまなアクセシビリティの問題を修正することで、SvcConfigEditor.exe と SvcTraceViewer.exe のツールが改善されました。 その問題のほとんどは、名前の未定義や、特定の UI の自動化パターンが正しく実装されていないといった軽微なものです。 このような問題は、多くのユーザーが認識しないものですが、スクリーン リーダーのような支援技術を使用するお客様はこれらの SDK ツールのアクセシビリティの強化を実感されるでしょう。 実際に、この修正によって、キーボード フォーカスの順序のような以前の動作がいくつか変更されます。これらのツールのアクセシビリティの修正をすべて取得するには、app.config ファイルを次のようにします。<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|スコープ|エッジ|
|Version|4.7.1|
|型|再ターゲット中|

