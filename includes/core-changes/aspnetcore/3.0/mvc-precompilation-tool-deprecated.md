---
ms.openlocfilehash: 641233df165a1c2208a2185f2b6e99077f9a59d3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394389"
---
### <a name="mvc-precompilation-tool-deprecated"></a>MVC:プリコンパイル ツールは非推奨です

ASP.NET Core 1.1 では、`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` (MVC プリコンパイル ツール) パッケージが導入され、Razor ファイル ( *.cshtml* ファイル) の発行時のコンパイルのサポートが追加されました。 ASP.NET Core 2.1 では、プリコンパイル ツールの機能を拡張するために [Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-2.1) が導入されました。 Razor SDK では、Razor ファイルのビルドおよび発行時のコンパイルのサポートが追加されました。 SDK では、アプリの起動時間を改善しながら、ビルド時に *の* ファイルの正確性を確認します。 Razor SDK は既定でオンになっており、その使用を開始するためにジェスチャは必要ありません。

ASP.NET Core 3.0 では、ASP.NET Core 1.1 世代の MVC のプリコンパイル ツールが削除されました。 以前のバージョンのパッケージでは、修正プログラムのリリースで重要なバグおよびセキュリティ修正プログラムを引き続き受け取ります。 

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

`Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` パッケージは、MVC Razor ビューをプリコンパイルするために使用されました。

#### <a name="new-behavior"></a>新しい動作

Razor SDK では、この機能がネイティブでサポートされます。 `Microsoft.AspNetCore.Mvc.Razor.ViewCompilation` パッケージが更新されなくなりました。

#### <a name="reason-for-change"></a>変更理由

Razor SDK によって、より多くの機能が提供され、ビルド時に *.cshtml* ファイルの正確性が確認されます。 また、SDK によってアプリの起動時間が改善されます。

#### <a name="recommended-action"></a>推奨される操作

ASP.NET Core 2.1 以降のユーザーの場合は、[Razor SDK](/aspnet/core/razor-pages/sdk?view=aspnetcore-3.0) でのプリコンパイルのネイティブ サポートを使用するように更新します。 バグまたは不足している機能によって Razor SDK への移行が妨げられる場合は、[aspnet/AspNetCore](https://github.com/aspnet/AspNetCore/issues) で問題を開きます。

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

なし

<!-- 

### Affected APIs

Not detectable via API analysis

-->
