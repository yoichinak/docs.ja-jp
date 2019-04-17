---
ms.openlocfilehash: fbc39b6e1cc19f6c2846caaabb9a8a721494b4e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59236138"
---
### <a name="allow-unicode-in-uris-that-resemble-unc-shares"></a>UNC 共有に似た URI での Unicode の許可

|   |   |
|---|---|
|説明|<xref:System.Uri?displayProperty=fullName> では、UNC 共有名と Unicode 文字の両方を含むファイル URI の構築時に、URI が無効な内部状態にならなくなります。 以下のすべてに該当する場合にのみ、動作が変わります。<ul><li>URI にスキーム <code>file:</code> があり、4 つ以上のスラッシュが続く。</li><li>ホスト名がアンダースコアまたはその他の予約されていないシンボルで始まる。</li><li>URI に Unicode 文字が含まれている。</li></ul>|
|提案される解決策|Unicode を含む URI を一貫して操作するアプリケーションでこの動作を使用して、UNC 共有への参照を許可しないようにした可能性があります。 これらのアプリケーションでは代わりに <xref:System.Uri.IsUnc> を使用する必要があります。|
|スコープ|エッジ|
|Version|4.7.2|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Uri?displayProperty=nameWithType></li></ul>|
