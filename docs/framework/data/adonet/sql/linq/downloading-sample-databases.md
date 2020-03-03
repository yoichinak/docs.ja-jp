---
title: ADO.NET コードサンプルのサンプル SQL Server データベースを取得する
description: ADO.NET のドキュメントのコードサンプルに使用されているサンプル SQL Server データベースと、SQL Server および管理ツールをダウンロードします。
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 60566041ff4f99e96c9aee052dbcc17b5e5da9e5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794032"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>ADO.NET コードサンプルのサンプルデータベースを入手する

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ドキュメントに記載されているいくつかの例とチュートリアルでは、サンプル SQL Server データベースと SQL Server Express を使用します。 これらの製品は、Microsoft から無料でダウンロードできます。

## <a name="get-the-northwind-sample-database-for-sql-server"></a>SQL Server の Northwind サンプルデータベースを取得する

次の GitHub `instnwnd.sql`リポジトリからスクリプトをダウンロードして、SQL Server 用の Northwind サンプルデータベースを作成して読み込みます。

[Microsoft SQL Server 用の Northwind および pubs サンプルデータベース](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Northwind データベースを使用するには、ダウンロード`instnwnd.sql`したスクリプトファイルを実行して、 [SQL Server Management Studio](#get_ssms)または同様のツールを使用して SQL Server のインスタンスにデータベースを再作成する必要があります。 リポジトリの Readme ファイルに記載されている手順に従います。

> [!TIP]
> Microsoft Access 用の Northwind データベースをお探しの場合は、「 [Microsoft access 用の northwind サンプルデータベースのインストール](#northwind_access)」を参照してください。

## <a name="northwind_access"></a>Microsoft Access 用の Northwind サンプルデータベースを入手する

Microsoft Access 用の Northwind サンプルデータベースは、Microsoft ダウンロードセンターでは使用できません。 Access 内から直接 Northwind をインストールするには、次の操作を行います。

1. [アクセス] を開きます。

1. **[オンラインテンプレートの検索]** ボックスに「 **Northwind** 」と入力し、 **enter**キーを押します。

1. 結果 画面で  **Northwind** を選択します。 新しいウィンドウが開き、Northwind データベースの説明が表示されます。

1. 新しいウィンドウで、 **[ファイル名]** テキストボックスに Northwind データベースのコピーのファイル名を入力します。

1. **[作成]** を選択します。 Access は Northwind データベースをダウンロードし、ファイルを準備します。

1. この処理が完了すると、データベースが [ようこそ] 画面で開きます。

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>SQL Server の AdventureWorks サンプルデータベースを取得する

次の GitHub リポジトリから SQL Server 用の AdventureWorks サンプルデータベースをダウンロードします。

[AdventureWorks サンプルデータベース](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

データベースバックアップ (\*.bak) ファイルの1つをダウンロードした後、SQL Server Management Studio (SSMS) を使用して SQL Server のインスタンスにバックアップを復元します。 「 [Get SQL Server Management Studio](#get_ssms)」を参照してください。

## <a name="get_ssms"></a>SQL Server Management Studio の取得
ダウンロードしたデータベースを表示または変更する場合は、SQL Server Management Studio (SSMS) を使用できます。 次のページから SSMS をダウンロードします。

[SQL Server Management Studio (SSMS) のダウンロード](/sql/ssms/download-sql-server-management-studio-ssms) 

また、Visual Studio 統合開発環境 (IDE) でデータベースを表示および管理することもできます。 [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)で、 **SQL Server オブジェクトエクスプローラー**からデータベースに接続するか、**サーバーエクスプローラー**でデータベースへのデータ接続を作成します。 これらのエクスプローラーウィンドウは、 **[表示]** メニューから開きます。

## <a name="get_sql"></a>SQL Server Express の取得

SQL Server Express は、アプリケーションと共に再頒布できる SQL Server の無料のエントリレベルエディションです。 次のページから SQL Server Express をダウンロードします。
  
[SQL Server Express エディション](https://www.microsoft.com/sql-server/sql-server-editions-express)

[Visual studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)を使用している場合、SQL Server Express LocalDB は、visual studio の無料の Community edition、および Professional 以上のエディションに含まれています。  

## <a name="see-also"></a>関連項目

- [はじめに](getting-started.md)
