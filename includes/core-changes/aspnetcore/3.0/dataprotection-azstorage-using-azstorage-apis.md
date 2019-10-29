---
ms.openlocfilehash: f103c96588bae167216d09a82973a4a7abfb5cc3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394088"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a>データの保護: DataProtection.AzureStorage で新しい Azure Storage API が使用されるようになる

<xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> は [Azure Storage ライブラリ](https://github.com/Azure/azure-storage-net)に依存します。 これらのライブラリで、アセンブリ、パッケージ、名前空間の名前が変更されました。 ASP.NET Core 3.0 以降、`Microsoft.AspNetCore.DataProtection.AzureStorage` では `Microsoft.Azure.Storage.` というプレフィックスが付いた新しい API およびパッケージが使用されます。

Azure Storage API に関する質問については、<https://github.com/Azure/azure-storage-net> を使用してください。 この問題に関するディスカッションについては、[aspnet/AspNetCore#8472](https://github.com/aspnet/AspNetCore/issues/8472) を参照してください。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

パッケージでは `WindowsAzure.Storage` NuGet パッケージが参照されていました。

#### <a name="new-behavior"></a>新しい動作

パッケージでは `Microsoft.Azure.Storage.Blob` NuGet パッケージが参照されています。

#### <a name="reason-for-change"></a>変更理由

この変更により、`Microsoft.AspNetCore.DataProtection.AzureStorage` は推奨される Azure Storage パッケージに移行できるようになります。

#### <a name="recommended-action"></a>推奨される操作

ASP.NET Core 3.0 で古い Azure Storage API をまだ使用する必要がある場合は、[Windowsazure.servicebus](https://www.nuget.org/packages/WindowsAzure.Storage/) パッケージに対する直接的な依存関係を追加してください。 このパッケージは、新しい `Microsoft.Azure.Storage` API と共にインストールできます。

多くの場合、アップグレードで必要なのは、新しい名前空間を使用するように `using` ステートメントを変更することだけです。

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

なし

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
