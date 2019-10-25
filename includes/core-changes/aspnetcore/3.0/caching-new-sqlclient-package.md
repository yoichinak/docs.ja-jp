---
ms.openlocfilehash: 32c7f4e9e4736145f9275b74f34c04404e7c770a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394114"
---
### <a name="caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package"></a>キャッシュ:Microsoft.Extensions.Caching.SqlServer で新しい SqlClient パッケージを使用

`Microsoft.Extensions.Caching.SqlServer` パッケージでは、`System.Data.SqlClient` パッケージの代わりに、新しい `Microsoft.Data.SqlClient` パッケージが使用されます。 この変更により、動作のわずかな破壊的変更が発生する可能性があります。 詳細については、「[Introducing the new Microsoft.Data.SqlClient (新しい Microsoft.Data.SqlClient の導入)](https://devblogs.microsoft.com/dotnet/introducing-the-new-microsoftdatasqlclient/)」をご覧ください。

#### <a name="version-introduced"></a>導入されたバージョン

3.0

#### <a name="old-behavior"></a>以前の動作

`Microsoft.Extensions.Caching.SqlServer` パッケージで、`System.Data.SqlClient` パッケージが使用されていました。

#### <a name="new-behavior"></a>新しい動作

`Microsoft.Extensions.Caching.SqlServer` で、`Microsoft.Data.SqlClient` パッケージが使用されるようになりました。

#### <a name="reason-for-change"></a>変更理由

`Microsoft.Data.SqlClient` は、`System.Data.SqlClient` から構築された新しいパッケージです。 今後、機能の新しい動作はすべてこのパッケージで実行されます。

#### <a name="recommended-action"></a>推奨される操作

`Microsoft.Extensions.Caching.SqlServer` パッケージによって返される型を使用し、それらを `System.Data.SqlClient` の型にキャストしている場合を除き、この破壊的変更について気にする必要はありません。 たとえば、`DbConnection` を[以前の SqlConnection 型](xref:System.Data.SqlClient.SqlConnection)にキャストしている場合は、キャストを新しい `Microsoft.Data.SqlClient.SqlConnection` 型に変更する必要があります。 

#### <a name="category"></a>カテゴリ

ASP.NET Core

#### <a name="affected-apis"></a>影響を受ける API

なし

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
