---
ms.openlocfilehash: 16b9fde49f513643a37f65f3e926a34fc991c55a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394313"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>ホスティング:ObjectPoolProvider が WebHostBuilder 依存関係から削除されました

ASP.NET Core の定額課金を増やすために、`ObjectPoolProvider` が主な依存関係のセットから削除されました。 `ObjectPoolProvider` に依存する特定のコンポーネント自体で、それが追加されるようになりました。

詳細については、[aspnet/AspNetCore#5944](https://github.com/aspnet/AspNetCore/issues/5944) を参照してください。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

`WebHostBuilder` によって、DI コンテナーに既定で `ObjectPoolProvider` が提供されます。

#### <a name="new-behavior"></a>新しい動作

`WebHostBuilder` によって、DI コンテナーに既定で `ObjectPoolProvider` が提供されなくなりました。

#### <a name="reason-for-change"></a>変更理由

この変更は、ASP.NET Core の定額課金を増やすために行われました。

#### <a name="recommended-action"></a>推奨される操作

コンポーネントに `ObjectPoolProvider` が必要な場合は、`IServiceCollection` を介して依存関係に追加する必要があります。

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

なし

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
