---
ms.openlocfilehash: 65bac44c84589fb55d2b04c39088c2825c451a6b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72393951"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>Authorization:AddAuthorization のオーバーロードが別のアセンブリに移動した

`Microsoft.AspNetCore.Authorization` に以前あったコア `AddAuthorization` メソッドが `AddAuthorizationCore` に名前変更されました。 古い `AddAuthorization` メソッドはまだありますが、代わりに `Microsoft.AspNetCore.Authorization.Policy` パッケージに含まれています。 両方のメソッドを使用するアプリには影響はありません。 ポリシー パッケージを使用していないアプリは、`AddAuthorizationCore` を使用するように切り替える必要があります。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

`AddAuthorization` メソッドは `Microsoft.AspNetCore.Authorization` にありました。

#### <a name="new-behavior"></a>新しい動作

`AddAuthorization` メソッドは `Microsoft.AspNetCore.Authorization.Policy` にあります。 `AddAuthorizationCore` は、古いメソッドの新しい名前です。

#### <a name="reason-for-change"></a>変更理由

`AddAuthorization` は、承認に必要な一般的なすべてのサービスを追加するのにより適切なメソッド名です。

#### <a name="recommended-action"></a>推奨される操作

`Microsoft.AspNetCore.Authorization.Policy` に参照を追加するか、代わりに `AddAuthorizationCore` を使用します。

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
