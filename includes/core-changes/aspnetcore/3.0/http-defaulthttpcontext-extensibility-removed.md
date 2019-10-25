---
ms.openlocfilehash: 177617569a93e09f4c2a05acc21dce362edd58bc
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394172"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP:DefaultHttpContext の機能拡張の削除

ASP.NET Core 3.0 のパフォーマンスの改善の一環として、`DefaultHttpContext` の機能拡張が削除されました。 クラスは `sealed` になりました。 詳細については、[aspnet/AspNetCore#6504](https://github.com/aspnet/AspNetCore/pull/6504) を参照してください。

単体テストで `Mock<DefaultHttpContext>` を使用している場合は、代わりに `Mock<HttpContext>` を使用してください。 

ディスカッションについては、[aspnet/AspNetCore#6534](https://github.com/aspnet/AspNetCore/issues/6534) を参照してください。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

クラスは `DefaultHttpContext` から派生できます。

#### <a name="new-behavior"></a>新しい動作

クラスは `DefaultHttpContext` から派生できません。

#### <a name="reason-for-change"></a>変更理由

機能拡張は `HttpContext` のプーリングを可能にするために当初提供されていましたが、不要な複雑さをもたらし、他の最適化の妨げとなっていました。

#### <a name="recommended-action"></a>推奨される操作

単体テストで `Mock<DefaultHttpContext>` を使用する場合、今後は代わりに `Mock<HttpContext>` を使用してください。 

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
