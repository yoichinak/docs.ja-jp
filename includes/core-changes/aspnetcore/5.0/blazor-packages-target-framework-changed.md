---
ms.openlocfilehash: 17a167e5245914329195d61ab45ae2d8ecb617d6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416274"
---
### <a name="blazor-target-framework-of-nuget-packages-changed"></a>Blazor: NuGet パッケージのターゲット フレームワークを変更

Blazor 3.2 WebAssembly プロジェクトは、.NET Standard 2.1 (`<TargetFramework>netstandard2.1</TargetFramework>`) をターゲットにするようコンパイルされていました。 ASP.NET Core 5.0 では、Blazor Server と Blazor WebAssembly プロジェクトの両方で .NET 5.0 (`<TargetFramework>net5.0</TargetFramework>`) がターゲットとされます。 ターゲット フレームワークの変更に対応するため、次の Blazor パッケージで .NET Standard 2.1 がターゲットとされることはなくなりました。

* [Microsoft.AspNetCore.Components](https://www.nuget.org/packages/Microsoft.AspNetCore.Components)
* [Microsoft.AspNetCore.Components.Authorization](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Authorization)
* [Microsoft.AspNetCore.Components.Forms](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Forms)
* [Microsoft.AspNetCore.Components.Web](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.Web)
* [Microsoft.AspNetCore.Components.WebAssembly](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly)
* [Microsoft.AspNetCore.Components.WebAssembly.Authentication](https://www.nuget.org/packages/Microsoft.AspNetCore.Components.WebAssembly.Authentication)
* [Microsoft.JSInterop](https://www.nuget.org/packages/Microsoft.JSInterop)
* [Microsoft.JSInterop.WebAssembly](https://www.nuget.org/packages/Microsoft.JSInterop.WebAssembly)
* [Microsoft.Authentication.WebAssembly.Msal](https://www.nuget.org/packages/Microsoft.Authentication.WebAssembly.Msal)

ディスカッションについては、GitHub イシュー [dotnet/aspnetcore#23424](https://github.com/dotnet/aspnetcore/issues/23424) を参照してください。

#### <a name="version-introduced"></a>導入されたバージョン

5.0 Preview 7

#### <a name="old-behavior"></a>以前の動作

Blazor 3.1 および 3.2 では、.NET Standard 2.1 and .NET Core 3.1 がパッケージによりターゲットとされます。

#### <a name="new-behavior"></a>新しい動作

ASP.NET Core 5.0 では、.NET 5.0 がパッケージによりターゲットとされます。

#### <a name="reason-for-change"></a>変更理由

.NET ターゲット フレームワークの要件に対応するために変更が行われました。

#### <a name="recommended-action"></a>推奨アクション

Blazor 3.2 WebAssembly のプロジェクトは、パッケージ参照の 5.x.x への更新の一環として、.NET 5.0 をターゲットとする必要があります。 これらのパッケージのいずれかを参照するライブラリでは、要件に応じて、.NET 5.0 をターゲットとするか、またはマルチターゲットとすることができます。

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

None

<!--

#### Affected APIs

Not detectable via API analysis

-->
