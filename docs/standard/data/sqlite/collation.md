---
title: 照合順序
ms.date: 12/13/2019
description: カスタム照合シーケンスを作成する方法について説明します。
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242973"
---
# <a name="collation"></a>照合順序

照合シーケンスは、順序と等価性を決定するために TEXT 値を比較するときに SQLite によって使用されます。 SQL クエリで列を作成するとき、または操作ごとに使用する照合順序を指定できます。 SQLite には、デフォルトで 3 つの照合シーケンスが含まれています。

| 照合順序 | 説明                               |
| --------- | ----------------------------------------- |
| RTRIM     | 末尾の空白を無視します。               |
| ノーケース    | ASCII 文字 A から Z の大文字と小文字を区別しない |
| BINARY    | 大文字 小文字。 バイトを直接比較する   |

## <a name="custom-collation"></a>カスタム照合順序

また、独自の照合順序を定義したり、組み込みシーケンスをオーバーライドしたり<xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>することもできます。 次の例は、UNIcode 文字をサポートするために NOCASE 照合順序をオーバーライドする方法を示しています。 [完全なサンプル コード](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs)は GitHub で入手できます。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Like 演算子

SQLite の LIKE 演算子は照合順序を受け入れない。 既定の実装は、NOCASE 照合順序と同じセマンティクスを持っています。 ASCII 文字 A から Z の場合は大文字と小文字を区別しないだけです。

LIKE 演算子は、次のプラグマ ステートメントを使用して簡単に大文字と小文字を区別できます。

```sql
PRAGMA case_sensitive_like = 1
```

LIKE 演算子の実装のオーバーライドの詳細については、[ユーザー定義関数](user-defined-functions.md)を参照してください。

## <a name="see-also"></a>関連項目

* [ユーザー定義関数](user-defined-functions.md)
* [SQL 構文](https://www.sqlite.org/lang.html)
