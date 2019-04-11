---
ms.openlocfilehash: d3c6818861f8b0261a9a71a4654029143d928d08
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/01/2019
ms.locfileid: "58760730"
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

