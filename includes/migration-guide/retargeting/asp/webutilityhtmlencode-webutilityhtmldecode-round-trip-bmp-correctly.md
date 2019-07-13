---
ms.openlocfilehash: ca662b57fae9b1d0d41290f3052f71bca66e9bf3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59774465"
---
### <a name="webutilityhtmlencode-and-webutilityhtmldecode-round-trip-bmp-correctly"></a>WebUtility.HtmlEncode と WebUtility.HtmlDecode で BMP が正常に往復する

|   |   |
|---|---|
|説明|.NET Framework 4.5 を対象とするアプリケーションの場合、基本多言語面 (BMP: Basic Multilingual Plane) の外部にある文字は、<xref:System.Net.WebUtility.HtmlDecode(System.String)> メソッドに渡されたときに正常に往復します。|
|提案される解決策|この変更は現在のアプリケーションに影響を与えないはずですが、元の動作に戻すには、<code>&lt;httpRuntime&gt;</code> 要素の <code>targetFramework</code> 属性を &quot;4.5&quot; 以外の文字列に設定します。 また、.NET Framework の対象バージョンに関係なくこの動作を制御するために <code>unicodeEncodingConformance</code> 構成要素の <code>unicodeDecodingConformance</code> 属性と <code>&lt;webUtility&gt;</code> 属性を設定することもできます。|
|スコープ|エッジ|
|Version|4.5|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Net.WebUtility.HtmlEncode(System.String)?displayProperty=nameWithType></li><li><xref:System.Net.WebUtility.HtmlEncode(System.String,System.IO.TextWriter)?displayProperty=nameWithType></li></ul>|
