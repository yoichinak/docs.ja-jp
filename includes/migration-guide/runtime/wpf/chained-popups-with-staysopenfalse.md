---
ms.openlocfilehash: 2bb40294685c987de84138ee889e6b88f7184bb0
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857207"
---
### <a name="chained-popups-with-staysopenfalse"></a>StaysOpen=False でポップアップがチェーンされる

|   |   |
|---|---|
|説明|ポップアップの外側をクリックすると、StaysOpen=False のポップアップが閉じられることが想定されます。 このような 2 つ以上のポップアップがチェーンされている (つまり、1 つに別のものが含まれている) 場合、次のような、多くの問題が発生します。<ul><li>2 つのレベルを開き、P2 の外側と、P1 の内側をクリックします。  何も起こりません。</li><li>2 つのレベルを開き、P1 の外側をクリックします。  両方のポップアップが閉じます。</li><li>2 つのレベルを開いて閉じます。  次に、P2 をもう一度開いてみます。  何も起こりません。</li><li>3 つのレベルを開いてみます。  この操作を行うことはできません  (クリックする場所に応じて、何も起こらないか、最初の 2 つのレベルが閉じます)。このような場合 (および他のバリアント) は、予期したとおり動作します。</li></ul>|
|スコープ|エッジ|
|Version|4.7.1|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Windows.Controls.Primitives.Popup.StaysOpen?displayProperty=nameWithType></li></ul>|

