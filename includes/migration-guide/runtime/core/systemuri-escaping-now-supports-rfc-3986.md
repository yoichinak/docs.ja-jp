---
ms.openlocfilehash: 1654d58651bf14b0e7c21de2afa827634b7db858
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235663"
---
### <a name="systemuri-escaping-now-supports-rfc-3986"></a>System.Uri エスケープで RFC 3986 がサポート対象に

|   |   |
|---|---|
|説明|URI エスケープは、.NET Framework 4.5 で、[RFC 3986](https://tools.ietf.org/html/rfc3986) をサポートするように変更されました。 具体的な変更内容:<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=name> は、予約されている文字を RFC 3986 に基づいてエスケープします。</li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=name> は、予約されている文字をエスケープしません。</li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> は、無効なエスケープ シーケンスが発生した場合に例外をスローしません。</li><li>予約されていないエスケープ文字はエスケープ解除されます。</li></ul>|
|提案される解決策|<ul><li>無効なエスケープ シーケンスの場合、<xref:System.Uri.UnescapeDataString(System.String)?displayProperty=name> のスローに依存しないように、アプリケーションを更新します。 このようなシーケンスは、直接削除する必要があります。</li><li>同様に、エスケープおよびエスケープ解除された URI とデータ文字列は、.NET Framework 4.0 と .NET Framework 4.5 で異なる場合があるため、.NET のバージョン間で直接比較しないでください。 代わりに、1 つの .NET バージョンで解析と正規化を行ってから比較してください。</li></ul>|
|スコープ|マイナー|
|Version|4.5|
|型|ランタイム|
|影響を受ける API|<ul><li><xref:System.Uri.EscapeDataString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.EscapeUriString(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.UnescapeDataString(System.String)?displayProperty=nameWithType></li></ul>|
