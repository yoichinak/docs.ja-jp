---
ms.openlocfilehash: 22c4b61b293ac2366cae1dc73e0f6805a4a5fb8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236243"
---
### <a name="chained-popups-with-staysopenfalse"></a>StaysOpen=False でポップアップがチェーンされる

|   |   |
|---|---|
|説明|ポップアップの外側をクリックすると、StaysOpen=False のポップアップが閉じられることが想定されます。 このような 2 つ以上のポップアップがチェーンされている (つまり、1 つに別のものが含まれている) 場合、次のような、多くの問題が発生します。<ul><li>2 つのレベルを開き、P2 の外側と、P1 の内側をクリックします。  何も起こりません。</li><li>2 つのレベルを開き、P1 の外側をクリックします。  両方のポップアップが閉じます。</li><li>2 つのレベルを開いて閉じます。  次に、P2 をもう一度開いてみます。  何も起こりません。</li><li>3 つのレベルを開いてみます。  この操作を行うことはできません   (クリックする場所に応じて、何も起こらないか、最初の 2 つのレベルが閉じます)。このような場合 (および他のバリアント) は、予期したとおり動作します。</li></ul>|
|スコープ|エッジ|
|Version|4.7.1|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|
