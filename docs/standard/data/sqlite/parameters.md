---
title: パラメーター
ms.date: 12/13/2019
description: SQL パラメーターの使用方法について説明します。
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401203"
---
# <a name="parameters"></a>パラメーター

パラメータは、SQL インジェクション攻撃から保護するために使用されます。 ユーザー入力を SQL ステートメントと連結する代わりに、入力がリテラル値としてのみ扱われ、決して実行されないようにするためのパラメーターを使用します。 SQLite では、通常、SQL ステートメントでリテラルが許可されている場所であれば、パラメーターを使用できます。

パラメータの先頭には、 、 `:` `@`、または`$`を付けることができます。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

NET 値が SQLite 値にマップされる方法の詳細については、「[データ型](types.md)」を参照してください。

## <a name="truncation"></a>切り捨て

<xref:Microsoft.Data.Sqlite.SqliteParameter.Size> TEXT 値と BLOB 値を切り捨てるには、このプロパティを使用します。

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a>代替タイプ

代替 SQLite タイプを使用する場合があります。 プロパティを設定して、<xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType>これを行います。

次の代替型マッピングを使用できます。 デフォルトのマッピングについては、[データ型](types.md)を参照してください。

| Value          | Sqlite 型 | 解説          |
| -------------- | ---------- | ---------------- |
| Char           | Integer    | UTF-16           |
| DateTime       | Real       | ユリウス日の値 |
| DateTimeOffset | Real       | ユリウス日の値 |
| Guid           | BLOB       |                  |
| TimeSpan       | Real       | 数日で          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>出力パラメーター

SQLite は出力パラメータをサポートしていません。 代わりにクエリ結果の値を返します。

## <a name="see-also"></a>関連項目

* [データ型](types.md)
