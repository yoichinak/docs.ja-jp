---
ms.openlocfilehash: e0d0a680915f14c2d33f1864ad5ad05aff3dde5f
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393974"
---
### <a name="http-headernames-constants-changed-to-static-readonly"></a>HTTP:HeaderNames の定数を静的読み取り専用に変更

ASP.NET Core 3.0 Preview 5 以降、<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName> のフィールドが `const` から `static readonly` に変更されました。

ディスカッションについては、[aspnet/aspnet/AspNetCore#9514](https://github.com/aspnet/AspNetCore/issues/9514) を参照してください。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

これらのフィールドは以前は `const` でした。

#### <a name="new-behavior"></a>新しい動作

これらのフィールドは `static readonly` になりました。

#### <a name="reason-for-change"></a>変更理由

変更:

* アセンブリ境界を越えて値が埋め込まれるのを防ぎ、必要に応じて値を修正できるようにします。
* 参照の等価性チェックの高速化を可能にします。

#### <a name="recommended-action"></a>推奨される操作

3\.0 に対して再コンパイルします。 これらのフィールドを次の方法で使用しているソース コードはそれを実行できなくなりました。

* 属性引数として使用
* `switch` ステートメントで `case` として使用
* 別の `const` を定義するときに使用

この破壊的変更を回避するには、ヘッダー名の自己定義型の定数または文字列リテラルの使用に切り替えます。

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.Net.Http.Headers.HeaderNames?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.Net.Http.Headers.HeaderNames`

-->
