---
title: インメモリデータベース
ms.date: 12/13/2019
description: メモリ内 SQLite データベースの使用方法について説明します。
ms.openlocfilehash: b125ff5aa4128bd4c3ff558c5573b7d11802090a
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75450466"
---
# <a name="in-memory-databases"></a>インメモリデータベース

SQLite インメモリデータベースは、ディスク上ではなく、メモリ内に完全に格納されるデータベースです。 メモリ内データベースを作成するには、特殊なデータソースファイル名 `:memory:` を使用します。 接続が閉じられると、データベースは削除されます。 `:memory:`を使用する場合、各接続は独自のデータベースを作成します。

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>共有可能なインメモリデータベース

インメモリデータベースは、接続文字列で `Mode=Memory` と `Cache=Shared` を使用して、複数の接続間で共有できます。 `Data Source` キーワードを使用して、メモリ内のデータベースに名前を付けます。 同じ名前を使用する接続文字列は、同じメモリ内のデータベースにアクセスします。 データベースは、少なくとも1つの接続が開いたままになっている間は保持されます。 これをデモンストレーションする[サンプル](https://github.com/dotnet/samples/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs)は GitHub で入手できます。

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
