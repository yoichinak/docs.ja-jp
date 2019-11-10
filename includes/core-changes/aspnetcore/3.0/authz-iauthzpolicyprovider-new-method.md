---
ms.openlocfilehash: 74b989a2413d2192f7cf5208e400eaed879ea096
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198482"
---
### <a name="authorization-iauthorizationpolicyprovider-implementations-require-new-method"></a>Authorization:IAuthorizationPolicyProvider の実装には新しいメソッドが必要です

ASP.NET Core 3.0 では、`IAuthorizationPolicyProvider` に新しい `GetFallbackPolicyAsync` メソッドが追加されました。 このフォールバック ポリシーは、ポリシーが指定されていない場合に、承認ミドルウェアによって使用されます。

詳細については、[aspnet/AspNetCore#9759](https://github.com/aspnet/AspNetCore/pull/9759) を参照してください。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

`IAuthorizationPolicyProvider` の実装には、`GetFallbackPolicyAsync` メソッドは必要ありませんでした。

#### <a name="new-behavior"></a>新しい動作

`IAuthorizationPolicyProvider` の実装には、`GetFallbackPolicyAsync` メソッドが必要です。

#### <a name="reason-for-change"></a>変更理由

ポリシーが指定されていない場合に新しい `AuthorizationMiddleware` を使用にするには、新しいメソッドが必要でした。

#### <a name="recommended-action"></a>推奨される操作

`IAuthorizationPolicyProvider` の実装に `GetFallbackPolicyAsync` メソッドを追加します。

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

<xref:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider?displayProperty=fullName>

<!-- 

#### Affected APIs

`T:Microsoft.AspNetCore.Authorization.IAuthorizationPolicyProvider`

-->
