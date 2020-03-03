---
ms.openlocfilehash: 6c2c6422ca4d426fcc2ff5827a2387abb5578e3d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59234743"
---
### <a name="systemuri-parsing-adheres-to-rfc-3987"></a>System.Uri 解析が RFC 3987 に準拠

|   |   |
|---|---|
|説明|.NET Framework 4.5 では、URI 解析がいくつかの点で変更されました。 ただし、これらの変更は .NET Framework 4.5 を対象としたコードのみに影響することに注意してください。 バイナリが .NET Framework 4.0 を対象としている場合、以前の動作が実行されます。 .NET Framework 4.5 での URI 解析の変更は次のとおりです。<ul><li>URI 解析は、RFC 3987 の最新の IRI 規則に従って、正規化と文字チェックを実行します。</li><li>Unicode 正規化フォーム C は、URI のホスト部分でのみ実行されます。</li><li>無効な mailto:URI は、例外の原因になります。</li><li>パス セグメントの最後の末尾のドットが保存されるようになりました。</li><li><code>file://</code> URI は <code>?</code> 文字をエスケープしません。</li><li>Unicode 制御文字の <code>U+0080</code> から <code>U+009F</code> まではサポートされません。</li><li>コンマ文字 <code>,</code> または <code>%2c</code> は自動的にエスケープ解除されません。</li></ul>|
|提案される解決策|古い .NET Framework 4.0 URI 解析セマンティクスが必要な場合 (めったにありません)、.NET Framework 4.0 を対象とすることによって使用できます。 これは、アセンブリで <xref:System.Runtime.Versioning.TargetFrameworkAttribute?displayProperty=name> を使用することによって、または、[プロジェクトのプロパティ] ページの Visual Studio のプロジェクト システム UI によって実現できます。|
|スコープ|Major|
|バージョン|4.5|
|型|再ターゲット中|
|影響を受ける API|<ul><li><xref:System.Uri.%23ctor(System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.String,System.Boolean)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.String,System.UriKind)?displayProperty=nameWithType></li><li><xref:System.Uri.%23ctor(System.Uri,System.String)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.String,System.UriKind,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.String,System.Uri@)?displayProperty=nameWithType></li><li><xref:System.Uri.TryCreate(System.Uri,System.Uri,System.Uri@)?displayProperty=nameWithType></li></ul>|
