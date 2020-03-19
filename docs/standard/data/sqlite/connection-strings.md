---
title: Connection strings
ms.date: 12/13/2019
description: サポートされている接続文字列のキーワードと値。
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401197"
---
# <a name="connection-strings"></a>Connection strings

接続文字列を使用して、データベースへの接続方法を指定します。 Microsoft.Data.Sqlite の接続文字列は、キーワードと値のセミコロン区切りのリストとして標準の[ADO.NET構文](../../../framework/data/adonet/connection-strings.md)に従います。

## <a name="keywords"></a>Keywords

次の接続文字列キーワードを使用できます。

### <a name="data-source"></a>データ ソース

データベース ファイルのパス。 *データソース*(スペースなし) と*ファイル名*はこのキーワードのエイリアスです。

SQLite は、現在の作業ディレクトリに対する相対パスを扱います。 絶対パスも指定できます。

**空**の場合、SQLite は接続が閉じられたときに削除される一時的なディスク上のデータベースを作成します。

の`:memory:`場合、インメモリ データベースが使用されます。 詳細については、「[インメモリ データベース](in-memory-databases.md)」を参照してください。

`|DataDirectory|`置換文字列で始まるパスは、相対パスと同じように扱われます。 設定すると、パスは DataDirectory アプリケーション ドメイン プロパティの値に対して相対的に作成されます。

このキーワードは[、URI ファイル名](https://www.sqlite.org/uri.html)もサポートしています。

### <a name="mode"></a>モード

接続モード。

| Value           | 説明                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| 書き込み書き込み作成 | データベースを読み書き用に開き、存在しない場合は作成します。 これは既定値です。 |
| ReadWrite       | データベースを読み書き用に開きます。                                                        |
| ReadOnly        | データベースを読み取り専用モードで開きます。                                                              |
| メモリ          | インメモリ データベースを開きます。                                                                       |

### <a name="cache"></a>キャッシュ

接続で使用されるキャッシュ モード。

| Value   | 説明                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| Default | 基になる SQLite ライブラリの既定のモードを使用します。 これは既定値です。                   |
| プライベート | 各接続はプライベート キャッシュを使用します。                                                          |
| 共有  | 接続はキャッシュを共有します。 このモードは、トランザクションとテーブルロックの動作を変更できます。 |

### <a name="password"></a>Password

暗号化キー。 指定すると、`PRAGMA key`接続を開いた直後に送信されます。

> [!WARNING]
> パスワードは、暗号化がネイティブの SQLite ライブラリでサポートされていない場合には無効です。

### <a name="foreign-keys"></a>外部キー

外部キー制約を有効にするかどうかを示す値。

| Value   | 説明
| ------- | --- |
| True    | 接続`PRAGMA foreign_keys = 1`を開いた直後に送信します。
| False   | 接続`PRAGMA foreign_keys = 0`を開いた直後に送信します。
| (空) | を送信`PRAGMA foreign_keys`しません。 これは既定値です。 |

ネイティブ SQLite ライブラリのコンパイルに使用SQLITE_DEFAULT_FOREIGN_KEYS、e_sqlite3のように、外部キーを有効にする必要はありません。

### <a name="recursive-triggers"></a>再帰的トリガー

再帰的なトリガーを有効にするかどうかを示す値。

| Value | 説明                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | 接続`PRAGMA recursive_triggers`を開いた直後に送信します。 |
| False | を送信`PRAGMA recursive_triggers`しません。 これは既定値です。              |

## <a name="connection-string-builder"></a>接続文字列ビルダ

接続文字列を作成<xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder>する厳密に型指定された方法として使用できます。 また、接続文字列の挿入攻撃を防ぐためにも使用できます。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>例

### <a name="basic"></a>Basic

同時実行性を向上させる共有キャッシュを持つ基本的な接続文字列。

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a>Encrypted

暗号化されたデータベース。

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a>読み取り専用

アプリで変更できない読み取り専用データベース。

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a>メモリ内

プライベートなメモリ内データベース。

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a>メモリ内で共有可能

名前で識別される共有可能なインメモリ データベース*で、*

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>関連項目

* [ADO.NET での接続文字列](../../../framework/data/adonet/connection-strings.md)
* [インメモリ データベース](in-memory-databases.md)
* [トランザクション](transactions.md)
