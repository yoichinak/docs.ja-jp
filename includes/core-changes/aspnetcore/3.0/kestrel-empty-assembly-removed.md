---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394379"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kestrel: 空の HTTPS アセンブリを削除

アセンブリ <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> が削除されました。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="reason-for-change"></a>変更理由

ASP.NET Core 2.1 では、`Microsoft.AspNetCore.Server.Kestrel.Https` のコンテンツが <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName> に移動されました。 この変更は、`[TypeForwardedTo]` 属性を使用して非破壊的な方法で行われました。

#### <a name="recommended-action"></a>推奨される操作

- `Microsoft.AspNetCore.Server.Kestrel.Https` 2.0 を参照するライブラリでは、ASP.NET Core のすべての依存関係を 2.1 以降に更新する必要があります。 そうしないと、ASP.NET Core 3.0 アプリに読み込んだときに破損する可能性があります。
- ASP.NET Core 2.1 以降をターゲットとするアプリとライブラリでは、`Microsoft.AspNetCore.Server.Kestrel.Https` NuGet パッケージへの直接参照をすべて削除する必要があります。

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

なし

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
