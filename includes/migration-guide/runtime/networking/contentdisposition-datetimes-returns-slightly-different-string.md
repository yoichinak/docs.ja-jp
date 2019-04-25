---
ms.openlocfilehash: 705bbd0e0bf80e0726d41898685a5e166e039f99
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774154"
---
### <a name="contentdisposition-datetimes-returns-slightly-different-string"></a>ContentDisposition DateTimes で少し異なる文字列が返される

|   |   |
|---|---|
|説明|<xref:System.Net.Mime.ContentDisposition?displayProperty=name> の文字列表現が更新され、4.6 以降では、常に <xref:System.DateTime?displayProperty=name> の時間コンポーネントが 2 桁で表されます。 これは、[RFC822](https://www.ietf.org/rfc/rfc0822.txt) と [RFC2822](https://www.ietf.org/rfc/rfc2822.txt) に準拠しています。 これにより、4.6 では、配置の時間要素の 1 つが午前 10 時より前のシナリオでは、<xref:System.Net.Mime.ContentDisposition.ToString> は少し異なる文字列を返します。 ContentDispositions は文字列への変換によってシリアル化される場合があるため、<xref:System.Net.Mime.ContentDisposition.ToString> 操作、シリアル化、または GetHashCode 呼び出しを見直す必要があることに注意してください。|
|提案される解決策|異なるバージョンの .NET Framework からの ContentDispotisions の文字列表現が互いに正しく対応することを期待しないでください。 可能な場合は、比較を行う前に、文字列を ContentDispositions に戻してください。|
|スコープ|マイナー|
|Version|4.6|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Net.Mime.ContentDisposition.ToString?displayProperty=nameWithType></li><li><xref:System.Net.Mime.ContentDisposition.GetHashCode?displayProperty=nameWithType></li></ul>|
