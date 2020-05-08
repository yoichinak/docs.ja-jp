---
title: カスタム SQLite のバージョン
ms.date: 12/13/2019
description: ネイティブ SQLite ライブラリのカスタム バージョンを使用する方法について説明します。
ms.openlocfilehash: dd27278c1dbe17b12e5067d04d19043bf259b1e8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746995"
---
# <a name="custom-sqlite-versions"></a>カスタム SQLite のバージョン

Microsoft.Data.Sqlite は、SQLitePCLRaw に基づいて作成されています。 カスタム バージョンのネイティブ SQLite を使用するには、バンドルを使用するか、SQLitePCLRaw プロバイダーを構成します。

## <a name="bundles"></a>バンドル

SQLitePCLRaw にはバンドル パッケージが用意されているため、さまざまなプラットフォームで適切な依存関係を簡単に取り込むことができます。

メインの Microsoft.Data.Sqlite パッケージでは、既定で SQLitePCLRaw.bundle_e_sqlite3 が取り込まれます。

別のバンドルを使用するには、使用するバンドル パッケージとともに、`Microsoft.Data.Sqlite.Core` パッケージを代わりにインストールします。 バンドルは、Microsoft.Data.Sqlite によって自動的に初期化されます。

| バンドル | 説明 |
| --- | --- |
| SQLitePCLRaw.bundle_e_sqlite3 | すべてのプラットフォームで同じバージョンの SQLite を提供します。 FTS4、FTS5、JSON1、R*Tree 拡張機能を含みます。 既定値です。 |
| SQLitePCLRaw.bundle_green | Bundle_e_sqlite3 と同じですが、iOS の場合は例外で、システム SQLite ライブラリを使用します。 |
| SQLitePCLRaw.bundle_zetetic | Zetetic の公式の SQLCipher ビルドを使用します (含まれていません)。 |
| SQLitePCLRaw.bundle_winsqlite3 | Windows 10 のシステム SQLite ライブラリである winsqlite3.dll を使用します。 |
| SQLitePCLRaw.bundle_e_sqlcipher | オープン ソースの非公式の SQLCipher ビルドを提供します。 |

たとえば、オープン ソースの非公式の SQLCipher ビルドを使用するには、次のコマンドを使用します。

### <a name="net-core-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite.Core
dotnet add package SQLitePCLRaw.bundle_e_sqlcipher
```

### <a name="visual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite.Core
Install-Package SQLitePCLRaw.bundle_e_sqlcipher
```

---

## <a name="sqlitepclraw-providers"></a>SQLitePCLRaw プロバイダー

`SQLitePCLRaw.provider.dynamic_cdecl` パッケージを利用すると、独自の SQLite ビルドを使用できます。 この場合、アプリとともにネイティブ ライブラリをデプロイする必要があります。 ただし、アプリとともにネイティブ ライブラリをデプロイする場合の詳細は、使用している .NET プラットフォームとランタイムによって大きく異なります。

まず、IGetFunctionPointer を実装する必要があります。 この実装は、.NET Core では比較的簡単です。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_NativeLibraryAdapter)]

次に、SQLitePCLRaw プロバイダーを構成します。 これは、アプリで Microsoft.Data.Sqlite が使用される前に行ってください。 なお、SQLitePCLRaw バンドル パッケージを使用しないようにしてください。プロバイダーがオーバーライドされる可能性があります。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/SystemLibrarySample/Program.cs?name=snippet_SetProvider)]
