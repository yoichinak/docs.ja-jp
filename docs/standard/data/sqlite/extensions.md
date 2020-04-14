---
title: 拡張機能
ms.date: 12/13/2019
description: SQLite 拡張機能を読み込む方法について説明します。
ms.openlocfilehash: 51c705349c25240fe42e0edda8004a3e3b013ca3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242960"
---
# <a name="extensions"></a>拡張機能

SQLite は、実行時に拡張機能の読み込みをサポートします。 拡張機能には、追加の SQL 関数、照合順序、仮想テーブルなどが含まれます。

.NET Core には、参照される NuGet パッケージなどの追加の場所でネイティブ ライブラリを検索するための追加のロジックが含まれています。 残念ながら、SQLiteはこのロジックを活用できません。プラットフォーム API を直接呼び出してライブラリを読み込みます。 このため、SQLite 拡張機能をロードする前に、PATH、LD_LIBRARY_PATH、またはDYLD_LIBRARY_PATH環境変数を変更する必要がある場合があります。 GitHub には、参照される NuGet パッケージ内の現在のランタイムのバイナリを見つける方法を示す[サンプル](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs)があります。

内線番号を読み込<xref:Microsoft.Data.Sqlite.SqliteConnection.LoadExtension%2A>むには、メソッドを呼び出します。 Microsoft.Data.Sqlite は、接続が閉じられ、再び開かれた場合でも、拡張機能が読み込まれたままであることを確認します。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ExtensionsSample/Program.cs?name=snippet_LoadExtension)]

## <a name="see-also"></a>関連項目

* [ランタイムロード可能拡張機能](https://www.sqlite.org/loadext.html)
