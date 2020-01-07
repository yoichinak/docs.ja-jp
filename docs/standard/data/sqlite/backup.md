---
title: オンライン バックアップ。
ms.date: 12/13/2019
description: SQLite のオンラインバックアップ機能を使用する方法について説明します。
ms.openlocfilehash: 885aa2c5555b58deb2551c0a4e6933742a093457
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/25/2019
ms.locfileid: "75450346"
---
# <a name="online-backup"></a>オンライン バックアップ。

SQLite は、アプリの実行中にデータベースファイルをバックアップできます。 この機能は、`SqliteConnection`の <xref:Microsoft.Data.Sqlite.SqliteConnection.BackupDatabase%2A> メソッドとして、Microsoft. Data. Sqlite で使用できます。

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/BackupSample/Program.cs?name=snippet_Backup)]

現時点では、`BackupDatabase` はできるだけ早くデータベースをバックアップし、他の接続がデータベースへの書き込みをブロックします。 問題[#13834](https://github.com/aspnet/EntityFrameworkCore/issues/13834)は、データベースをバックグラウンドでバックアップするための代替 API を提供し、他の接続がバックアップとデータベースへの書き込みを中断できるようにします。 関心がある場合は、問題に関するフィードバックをお寄せください。
