---
ms.openlocfilehash: e5355387d5cb6d9e6de89f5b85e64bc100b32ae1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522649"
---
### <a name="spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger"></a>SPA:SpaServices と NodeServices は今後、コンソール ロガーにフォールバックしません。

ログ記録が構成されていない限り、<xref:Microsoft.AspNetCore.SpaServices?displayProperty=nameWithType> と <xref:Microsoft.AspNetCore.NodeServices?displayProperty=nameWithType> にはコンソール ログが表示されません。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

ログ記録が構成されていないとき、コンソール ロガーを自動作成する目的で `Microsoft.AspNetCore.SpaServices` と `Microsoft.AspNetCore.NodeServices` が使用されます。

#### <a name="new-behavior"></a>新しい動作

ログ記録が構成されていない限り、`Microsoft.AspNetCore.SpaServices` と `Microsoft.AspNetCore.NodeServices` にはコンソール ログが表示されません。

#### <a name="reason-for-change"></a>変更理由

他の ASP.NET Core パッケージでのログ記録の実装方法に合わせる必要があります。

#### <a name="recommended-action"></a>推奨される操作

以前の動作が必要な場合、コンソール ログ記録を構成するために、`services.AddLogging(builder => builder.AddConsole())` を `Setup.ConfigureServices` メソッドに追加します。

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

なし

<!--

#### Affected APIs

Not detectable via API analysis

-->
