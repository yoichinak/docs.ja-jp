---
title: パラメーター
ms.date: 12/13/2019
description: SQL パラメーターの使用方法について説明します。
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401203"
---
# <a name="parameters"></a>パラメーター

パラメーターを使用して SQL インジェクション攻撃から保護します。 ユーザー入力を SQL ステートメントと連結する代わりにパラメーターを使用することで、入力がリテラル値として扱われ、実行されないようにします。 SQLite では、通常、SQL ステートメント内でリテラルを使用できるすべての場所でパラメーターを使用できます。

パラメーターには、`:`、`@`、または `$` のいずれかのプレフィックスを付けることができます。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

.NET 値がどのように SQLite 値にマップされるかについて詳しくは、「[データ型](types.md)」を参照してください。

## <a name="truncation"></a>切り捨て

TEXT と BLOB の値を切り捨てるには、<xref:Microsoft.Data.Sqlite.SqliteParameter.Size> プロパティを使用します。

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a>代替型

ときにより、代替の SQLite 型を使用する必要が生じる場合があります。 これを行うには、<xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> プロパティを設定します。

使用できる代替型マッピングは次のとおりです。 既定のマッピングについては、「[データ型](types.md)」を参照してください。

| [値]          | SqliteType | Remarks          |
| -------------- | ---------- | ---------------- |
| Char           | 整数型    | UTF-16           |
| DateTime       | Real       | ユリウス日の値 |
| DateTimeOffset | Real       | ユリウス日の値 |
| GUID           | Blob       |                  |
| TimeSpan       | Real       | 日数          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>出力パラメーター

SQLite では、出力パラメーターはサポートされません。 代わりに、クエリ結果の中で値を返します。

## <a name="see-also"></a>関連項目

* [データ型](types.md)
