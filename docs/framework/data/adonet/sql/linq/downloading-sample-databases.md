---
title: ADO.NET コード サンプルについては、サンプルの SQL Server データベースを取得します。
description: ADO.NET のドキュメントと SQL Server および管理ツールのコード サンプルで使用されるサンプルの SQL Server データベースをダウンロードします。
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 5580f06f3d28ed6d70f75b619498ac8de7bc3326
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037935"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>ADO.NET コード サンプルについては、サンプル データベースを取得します。

さまざまな例とチュートリアルで、[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]ドキュメントは、SQL Server のサンプル データベースおよび SQL Server Express を使用します。 これらの製品を無料では、Microsoft からダウンロードできます。

## <a name="get-the-northwind-sample-database-for-sql-server"></a>SQL Server の Northwind サンプル データベースを取得します。

スクリプトをダウンロードする`instnwnd.sql`作成し、SQL Server の Northwind サンプル データベースを読み込むには、次の GitHub リポジトリから。

[Microsoft SQL Server 用の Northwind および pubs サンプル データベース](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Northwind データベースを使用する前に、ダウンロードした実行がある`instnwnd.sql`を使用して SQL Server のインスタンス上のデータベースを再作成するスクリプト ファイル[SQL Server Management Studio](#get_ssms)または同様のツール。 リポジトリに Readme ファイルの指示に従います。

> [!TIP]
> Microsoft Access の Northwind データベースで必要な場合を参照してください。 [Microsoft Access の Northwind サンプル データベースをインストール](#northwind_access)します。

## <a name="northwind_access"></a> Microsoft Access の Northwind サンプル データベースを取得します。

Microsoft ダウンロード センターでは、Microsoft Access の Northwind サンプル データベースを使用できません。 Access から直接 Northwind をインストールするには、次のことを行います。

1. アクセスを開きます。

1. Enter **Northwind**で、**オンライン テンプレートの検索**ボックスを選び **」と入力**します。

1. [結果] 画面で選択**Northwind**します。 Northwind データベースの説明では、新しいウィンドウが開きます。

1. 新しいウィンドウで、**ファイル名**テキスト ボックスに、Northwind データベースのコピーのファイル名を指定します。

1. **[作成]** を選択します。 アクセスは、Northwind データベースをダウンロードし、ファイルを準備します。

1. このプロセスが完了したら、[ようこそ] 画面で、データベースを開きます。

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>SQL Server の AdventureWorks サンプル データベースを取得します。

次の GitHub リポジトリからの SQL Server の AdventureWorks サンプル データベースをダウンロードします。

[AdventureWorks サンプル データベース](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

データベースのバックアップのいずれかをダウンロードした後 (\*.bak) ファイル、SQL Server のインスタンスに SQL Server Management Studio (SSMS) を使用して、バックアップを復元します。 参照してください[SQL Server Management Studio を入手する](#get_ssms)します。

## <a name="get_ssms"></a> SQL Server Management Studio を入手します。
表示またはダウンロードしたデータベースを変更する場合は、SQL Server Management Studio (SSMS) を使用することができます。 次のページから SSMS をダウンロードします。

[SQL Server Management Studio (SSMS) のダウンロード](/sql/ssms/download-sql-server-management-studio-ssms) 

また、表示、Visual Studio 統合開発環境 (IDE) でデータベースを管理およびできます。 [Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)からデータベースに接続する**SQL Server オブジェクト エクスプ ローラー**、データベースにデータ接続を作成または**サーバー エクスプ ローラー**します。 これらのエクスプ ローラー ウィンドウを開き、**ビュー**メニュー。

## <a name="get_sql"></a> SQL Server Express の入手します。

SQL Server Express は、アプリケーションで再配布する SQL Server の無料のエントリー エディションです。 次のページから SQL Server Express をダウンロードします。
  
[SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)

使用している場合[Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)、SQL Server Express LocalDB は、Visual Studio の無料の Community edition と Professional 以上のエディションに含まれます。  

## <a name="see-also"></a>関連項目

- [はじめに](../../../../../../docs/framework/data/adonet/sql/linq/getting-started.md)
