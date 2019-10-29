---
ms.openlocfilehash: 56b394c4698f60baeb70d3c17d1abee5d867deb7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394169"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>ID: SignInManager コンストラクターは新しいパラメーターを受け入れる

ASP.NET Core 3.0 以降、`SignInManager` コンストラクターに新しい `IUserConfirmation<TUser>` パラメーターが追加されました。 詳細については、[aspnet/AspNetCore#8356](https://github.com/aspnet/AspNetCore/issues/8356) を参照してください。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="reason-for-change"></a>変更理由

変更の動機は、ID での新しいメール/確認フローのサポートを追加するためでした。

#### <a name="recommended-action"></a>推奨される操作

手動で `SignInManager` を構築している場合は、`IUserConfirmation` の実装を提供するか、依存関係の挿入から 1 つを取得して提供します。

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
