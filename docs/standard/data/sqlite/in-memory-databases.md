---
title: インメモリ データベース
ms.date: 12/13/2019
description: インメモリ SQLite データベースの使用方法について説明します。
ms.openlocfilehash: 408c81f538e27dcfffad20db74b7809912b7905f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391209"
---
# <a name="in-memory-databases"></a>インメモリ データベース

SQLite インメモリ データベースは、ディスクではなく、メモリに完全に格納されたデータベースです。 メモリ内データベースを作成するには`:memory:`、特殊なデータ ソース ファイル名を使用します。 接続が閉じられると、データベースは削除されます。 を使用`:memory:`すると、各接続で独自のデータベースが作成されます。

```ConnectionString
Data Source=:memory:
```

## <a name="shareable-in-memory-databases"></a>共有可能なインメモリ データベース

インメモリ データベースは、接続文字列を使用`Mode=Memory`して複数`Cache=Shared`の接続間で共有できます。 この`Data Source`キーワードは、メモリ内データベースに名前を付けるために使用されます。 同じ名前を使用する接続文字列は、同じメモリ内データベースにアクセスします。 データベースへの接続が少なくとも 1 つ開いている限り、データベースは保持されます。 これを示す[サンプル](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/InMemorySample/Program.cs)は GitHub で入手できます。

```ConnectionString
Data Source=InMemorySample;Mode=Memory;Cache=Shared
```
