---
title: 概要
ms.date: 12/13/2019
description: Microsoft.Data.Sqlite の概要
ms.openlocfilehash: a5dc1366cc0ddfcd5501e26bf2a994456bcd5d98
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75353467"
---
# <a name="microsoftdatasqlite-overview"></a>Microsoft.Data.Sqlite 概要

Microsoft.Data.Sqlite は SQLite の軽量 [ADO.NET](../../../framework/data/adonet/index.md) プロバイダーです。 SQLite 用の [Entity Framework Core](/ef/core/) プロバイダーはこのライブラリの上に構築されます。 ただし、非依存で使用したり、他のデータ アクセス ライブラリと共に使用したりすることもできます。

## <a name="installation"></a>インストール

最新の安定バージョンを [NuGet](https://www.nuget.org/packages/Microsoft.Data.Sqlite) で入手できます。

### <a name="net-core-clitabnetcore-cli"></a>[.NET Core CLI](#tab/netcore-cli)

```dotnetcli
dotnet add package Microsoft.Data.Sqlite
```

### <a name="visual-studiotabvisual-studio"></a>[Visual Studio](#tab/visual-studio)

``` PowerShell
Install-Package Microsoft.Data.Sqlite
```

---

## <a name="usage"></a>使用方法

このライブラリによって、接続、コマンド、データ リーダーなどのために共通の ADO.NET 抽象化が実装されます。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_HelloWorld)]

## <a name="see-also"></a>関連項目

* [接続文字列](connection-strings.md)
* [API リファレンス](/dotnet/api/?view=msdata-sqlite-3.0.0)
* [SQL 構文](https://www.sqlite.org/lang.html)
