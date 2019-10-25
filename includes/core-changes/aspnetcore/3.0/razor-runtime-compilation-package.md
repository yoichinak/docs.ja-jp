---
ms.openlocfilehash: 8479168b64153d3c729f8814a2649df8d46f2135
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394431"
---
### <a name="razor-runtime-compilation-moved-to-a-package"></a>Razor: 実行時コンパイルをパッケージに移動

Razor ビューおよび Razor Pages の実行時コンパイルのサポートが個別のパッケージに移動されました。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

追加のパッケージを必要とせずに、実行時コンパイルを利用できます。

#### <a name="new-behavior"></a>新しい動作

この機能は、`Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` パッケージに移動されました。

次の API は、実行時コンパイルをサポートするために、以前は `Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions` で使用できました。 これらの API は、`Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation.MvcRazorRuntimeCompilationOptions` を介して使用できるようになりました。

- `RazorViewEngineOptions.FileProviders` -> `MvcRazorRuntimeCompilationOptions.FileProviders`
- `RazorViewEngineOptions.AdditionalCompilationReferences` -> `MvcRazorRuntimeCompilationOptions.AdditionalReferencePaths`

また、`Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions.AllowRecompilingViewsOnFileChange` が削除されました。 ファイルの変更時の再コンパイルは、`Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` パッケージを参照することによって既定で有効になります。

#### <a name="reason-for-change"></a>変更理由

この変更は、ASP.NET Core 共有フレームワークの Roslyn への依存関係を削除するために必要でした。

#### <a name="recommended-action"></a>推奨される操作

Razor ファイルの実行時コンパイルまたは再コンパイルを必要とするアプリでは、次の手順を実行する必要があります。

1. `Microsoft.AspNetCore.Mvc.Razor.RuntimeCompilation` パッケージへの参照を追加します。
1. プロジェクトの `Startup.ConfigureServices` メソッドを更新して、`AddMvcRazorRuntimeCompilation` の呼び出しを含めます。 たとえば、`Startup.ConfigureServices` では次のようにします。

    ```csharp
    services.AddMvc()
        .AddMvcRazorRuntimeCompilation();
    ```

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions?displayProperty=fullName>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Mvc.Razor.RazorViewEngineOptions`

-->
