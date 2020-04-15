---
title: データ型
ms.date: 12/13/2019
description: サポートされているデータ型と、そのデータ型に関する制限事項について説明します。
ms.openlocfilehash: a11ff382f80cd979506d6195c299c8234c3eb8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389037"
---
# <a name="data-types"></a>データ型

SQLite には、整数、実数、テキスト、BLOB の 4 つのプリミティブ データ型しかありません。 データベース値を a として返`object`す API は、これら 4 つの型のうちの 1 つだけを返します。 追加の .NET 型は Microsoft.Data.Sqlite でサポートされていますが、値は最終的にこれらの型と 4 つのプリミティブ型の 1 つとの間で強制的に変換されます。

| .NET           | SQLite  | 解説                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Boolean        | INTEGER | `0` または `1`                                                    |
| Byte           | INTEGER |                                                               |
| Byte[]         | BLOB    |                                                               |
| Char           | [TEXT]    | UTF-8                                                         |
| DateTime       | [TEXT]    | yyyy-MM-dd HH:mm:ss.フフフフ                                   |
| DateTimeOffset | [TEXT]    | yyyy-MM-dd HH:mm:ss.FFFFFFFzzzz                                |
| Decimal        | [TEXT]    | `0.0###########################`形式。 REALは損失を出すだろう。 |
| Double         | real    |                                                               |
| Guid           | [TEXT]    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | INTEGER |                                                               |
| Int32          | INTEGER |                                                               |
| Int64          | INTEGER |                                                               |
| SByte          | INTEGER |                                                               |
| Single         | real    |                                                               |
| String         | [TEXT]    | UTF-8                                                         |
| TimeSpan       | [TEXT]    | d.hh:mm:ss.fffffff                                            |
| UInt16         | INTEGER |                                                               |
| UInt32         | INTEGER |                                                               |
| UInt64         | INTEGER | 大きな値のオーバーフロー                                         |

## <a name="alternative-types"></a>代替タイプ

NET 型の中には、代替 SQLite 型から読み取ることができるものがあります。 パラメーターは、これらの代替タイプを使用するように構成することもできます。 詳しくは、「[パラメーター](parameters.md#alternative-types)」をご覧ください。

| .NET           | SQLite  | 解説          |
| -------------- | ------- | ---------------- |
| Char           | INTEGER | UTF-16           |
| DateTime       | real    | ユリウス日の値 |
| DateTimeOffset | real    | ユリウス日の値 |
| Guid           | BLOB    |                  |
| TimeSpan       | real    | 数日で          |

たとえば、次のクエリは、結果セット内の REAL 列から TimeSpan 値を読み取ります。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>列の型

SQLite は動的型システムを使用し、値の型は値自体に関連付けられており、格納されている列には関連付けされません。 任意の列型名を使用できます。 これらの名前に追加のセマンティクスを適用しません。

列の型名は、[型のアフィニティ](https://www.sqlite.org/datatype3.html#type_affinity)に影響を与えます。 一般的な問題の 1 つは、列型の STRING を使用すると、値を INTEGER または REAL に変換しようと試み、予期しない結果を招く可能性があるという点です。 4 つのプリミティブ SQLite 型名 (整数、実数、テキスト、BLOB) のみを使用することをお勧めします。

SQLite では、長さ、精度、スケールなどのタイプ ファセットを指定できますが、データベース エンジンによって強制されません。 アプリは、これらを適用する責任があります。

## <a name="see-also"></a>関連項目

- [SQLite のデータ型](https://www.sqlite.org/datatype3.html)
