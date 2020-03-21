---
title: ADO.NET コード サンプルのサンプル SQL Server データベースを取得します。
description: ADO.NET のドキュメントのコード サンプルで使用されているサンプル SQL Server データベース、および SQL Server および管理ツールをダウンロードします。
ms.date: 01/11/2019
ms.assetid: ef9d69a1-9461-43fe-94bb-7c836754bcb5
ms.openlocfilehash: 19d659cbe8f39d27b71dc59c738355f12fce92a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148388"
---
# <a name="get-the-sample-databases-for-adonet-code-samples"></a>ADO.NETコード サンプルのサンプル データベースを取得する

ドキュメントの例とチュートリアルの例の例[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]の例では、サンプルの SQL Server データベースと SQL Server のエクスプレスを使用します。 これらの製品は、マイクロソフトから無料でダウンロードできます。

## <a name="get-the-northwind-sample-database-for-sql-server"></a>SQL Server のノースウィンド サンプル データベースを取得する

次の`instnwnd.sql`GitHub リポジトリからスクリプトをダウンロードして、SQL Server 用の Northwind サンプル データベースを作成して読み込みます。

[ノースウィンドおよびパブのサンプル データベース](https://github.com/Microsoft/sql-server-samples/tree/master/samples/databases/northwind-pubs)

Northwind データベースを使用するには、ダウンロードした`instnwnd.sql`スクリプト ファイルを実行して[、SQL Server 管理スタジオ](#get_ssms)または同様のツールを使用して SQL Server のインスタンス上にデータベースを再作成する必要があります。 リポジトリの Readme ファイルの指示に従います。

> [!TIP]
> Access 用のノースウィンド データベースを探している場合は、「Access 用[のノースウィンド サンプル データベースのインストール](#northwind_access)」を参照してください。

## <a name="get-the-northwind-sample-database-for-microsoft-access"></a><a name="northwind_access"></a>Access 用のノースウィンド サンプル データベースを取得する

マイクロソフト のマイクロソフト ダウンロード センターでは、Access 用のノースウィンド サンプル データベースは使用できません。 Access から直接 Northwind をインストールするには、次の操作を行います。

1. アクセスを開きます。

1. **[オンライン テンプレートの検索**] ボックスに **「Northwind」** と入力し、[**入力**] を選択します。

1. 結果画面で、[**ノースウィンド**] を選択します。 Northwind データベースの説明を含む新しいウィンドウが開きます。

1. 新しいウィンドウの **[ファイル名**] テキスト ボックスに、Northwind データベースのコピーのファイル名を入力します。

1. [**作成**] を選択します。 ノースウィンド データベースがダウンロードされ、ファイルが準備されます。

1. このプロセスが完了すると、データベースが開き、ようこそ画面が表示されます。

## <a name="get-the-adventureworks-sample-database-for-sql-server"></a>SQL サーバーのアドベンチャーワークス サンプル データベースを取得する

次の GitHub リポジトリから SQL Server のアドベンチャーワークス サンプル データベースをダウンロードします。

[AdventureWorks サンプル データベース](https://github.com/Microsoft/sql-server-samples/releases/tag/adventureworks)

いずれかのデータベース バックアップ (.bak)\*ファイルをダウンロードした後、SQL Server 管理スタジオ (SSMS) を使用して、バックアップを SQL Server のインスタンスに復元します。 [「SQL Server 管理スタジオの取得](#get_ssms)」を参照してください。

## <a name="get-sql-server-management-studio"></a><a name="get_ssms"></a>取得 SQL サーバー管理スタジオ
ダウンロードしたデータベースを表示または変更する場合は、SQL Server 管理スタジオ (SSMS) を使用できます。 次のページから SSMS をダウンロードします。

[SQL Server Management Studio (SSMS) のダウンロード](/sql/ssms/download-sql-server-management-studio-ssms)

また、Visual Studio 統合開発環境 (IDE) でデータベースを表示および管理することもできます。 [Visual Studio で](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)、 SQL **Server オブジェクト エクスプローラー**からデータベースに接続するか、**またはサーバー エクスプローラー**でデータベースへのデータ接続を作成します。 [**表示**] メニューからこれらのエクスプローラ ペインを開きます。

## <a name="get-sql-server-express"></a><a name="get_sql"></a>SQL サーバー エクスプレスを取得します。

SQL Server Express は、アプリケーションと共に再配布できる、エントリ レベルの無料エディションです。 次のページから SQL Server エクスプレスをダウンロードします。
  
[SQL Server Express Edition](https://www.microsoft.com/sql-server/sql-server-editions-express)

[を](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017)使用している場合は、SQL Server エクスプレス のローカル DB は、無料のコミュニティ エディションの Visual Studio に含まれています。  

## <a name="see-also"></a>関連項目

- [はじめに](getting-started.md)
