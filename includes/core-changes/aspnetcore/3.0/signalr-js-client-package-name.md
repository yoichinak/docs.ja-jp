---
ms.openlocfilehash: acef6d7177ee5ad7e18dc8ba1e383d6f76263623
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394447"
---
### <a name="signalr-javascript-client-package-name-changed"></a>SignalR:JavaScript クライアント パッケージ名が変更されました

ASP.NET Core 3.0 Preview 7 で、SignalR JavaScript クライアント パッケージの名前が `@aspnet/signalr` から `@microsoft/signalr` に変更されました。 この名前変更は、Azure SignalR Service のおかげで、ASP.NET Core アプリ以外でも SignalR が便利になっている事実を反映しています。

この変更に合わせるため、*package.json* ファイル、`require` ステートメント、ECMAScript `import` ステートメントで参照を変更してください。 この名前変更の一環として API が変更されることはありません。

ディスカッションについては、[aspnet/AspNetCore#11637](https://github.com/aspnet/AspNetCore/issues/11637) を参照してください。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

クライアント パッケージの名前は `@aspnet/signalr` でした。

#### <a name="new-behavior"></a>新しい動作

クライアント パッケージの名前は `@microsoft/signalr` です。

#### <a name="reason-for-change"></a>変更理由

この名前変更は、Azure SignalR Service のおかげで、ASP.NET Core アプリ以外でも SignalR が便利になっていることを表わしています。

#### <a name="recommended-action"></a>推奨される操作

新しいパッケージ `@microsoft/signalr` に切り替えます。

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

なし

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
