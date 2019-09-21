---
title: サンプル データベースのダウンロード (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: eb42a7af-d410-4b7f-b4a8-13c72ce6fd09
ms.openlocfilehash: c67ee699cf594f476a728c7345b47b0c32dea7ff
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795178"
---
# <a name="downloading-sample-databases-linq-to-dataset"></a>サンプル データベースのダウンロード (LINQ to DataSet)
LINQ to DataSet ドキュメントのサンプルとチュートリアルでは、AdventureWorks サンプルデータベースを使用します。 この製品は、Microsoft のダウンロード サイトから無償でダウンロードできます。 LINQ to DataSet ドキュメントのサンプルとチュートリアルでは、データストアとして SQL Server を使用します。 SQL Server の代わりに、無償で提供されている SQL Server Express Edition をデータ ストアとして使用することもできます。  
  
## <a name="downloading-and-installing-the-adventureworks-database"></a>AdventureWorks データベースのダウンロードとインストール  
  
#### <a name="to-download-and-install-the-adventureworks-sample-database-for-sql-server"></a>SQL Server の AdventureWorks サンプル データベースをダウンロードおよびインストールするには  
  
1. Internet Explorer を開きます。  
  
2. [SQL Server 2005 のサンプルとサンプルデータベース](https://go.microsoft.com/fwlink/?linkid=31046)の Web サイトにアクセスします。  
  
3. 記載されている手順に従ってプロセッサの種類に応じた AdventureWorks サンプル データベース (AdventureWorksDB.msi など) をダウンロードし、.MSI ファイルをローカル コンピューターに保存します。  
  
4. 以前のバージョンの AdventureWorks は、単体でダウンロードしたか SQL Server のセットアップ時にインストールしたかに関係なく、AdventureWorks.msi の実行前に削除しておく必要があります。  
  
#### <a name="to-remove-a-previous-download-of-an-adventureworks-sample-database"></a>単体でダウンロードした以前のバージョンの AdventureWorks サンプル データベースを削除するには  
  
1. AdventureWorks データベースまたは AdventureWorksDW データベースを削除します。  
  
2. **[プログラムの追加と削除]** から**Adventureworksdb.msi**または**adventureworksbi.msi**を選択し、 **[削除]** をクリックします。  
  
#### <a name="to-remove-an-adventureworks-sample-database-previously-installed-using-setup"></a>過去にセットアップ プログラムを使用してインストールした AdventureWorks サンプル データベースを削除するには  
  
1. AdventureWorks データベースまたは AdventureWorksDW データベースを削除します。  
  
2. **[プログラムの追加と削除]** で**Microsoft SQL Server 2005**を選択し、 **[変更]** をクリックします。  
  
3. **[コンポーネントの選択]** で、 **[ワークステーションコンポーネント]** を選択し、 **[次へ]** をクリックします。  
  
4. ようこそ の  **SQL Server インストールウィザード** で、**次へ** をクリックします。  
  
5. **[システム構成チェック]** で、 **[次へ]** をクリックします。  
  
6. **[インスタンスの変更または削除]** で、 **[インストールされたコンポーネントの変更]** をクリックします。  
  
7. **[機能の選択]** で、[**ドキュメント]、[サンプル]、[サンプルデータベース**] ノードの順に展開します。  
  
8. **[サンプルコードとアプリケーション]** を選択します。 **サンプルデータベース** を展開し、削除するサンプルデータベースを選択します。 機能全体を選択する**は使用**できません。 **[次へ]** をクリックします。  
  
9. **[インストール]** をクリックし、インストールウィザードを完了します。  
  
#### <a name="to-attach-the-adventureworks-sample-database-files-to-an-instance-of-sql-server"></a>AdventureWorks サンプル データベース ファイルを SQL Server のインスタンスにアタッチするには  
  
1. ファイルサンプルデータベースインストーラーファイルがダウンロードされたら、 **adventureworksdb.msi**ファイル (またはダウンロードしたファイル) をダブルクリックして、データベースをインストールします。 既定では、データベースは c:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data にインストールされます。  
  
2. SQLCMD または SQL Server Management Studio で次のスクリプトを実行し、AdventureWorks データベース ファイルを SQL Server のインスタンスにアタッチします。  
  
    ```sql
    exec sp_attach_db @dbname=N'AdventureWorks', @filename1=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_Data.mdf', @filename2=N'C:\Program Files\Microsoft SQL Server\MSSQL.1\MSSQL\Data\AdventureWorks_log.ldf'  
    ```  
  
     これらのファイルが異なるドライブまたはディレクトリにインストールされている場合は、パスを適宜修正してから、`sp_attach_db` ストアド プロシージャを実行してください。  
  
## <a name="downloading-sql-server-express-edition"></a>SQL Server Express Edition のダウンロード  
 LINQ to DataSet セクションのサンプルとチュートリアルでは、データストアとして 2005 SQL Server を使用しますが、代わりに SQL Server Express エディションを使用するように変更することもできます。 SQL Server Express Edition は無料で入手でき、アプリケーションと共に再配布できます。 Visual Studio を使用している場合、SQL Server Express Edition は Pro 以降のエディションに含まれています。  
  
#### <a name="to-download-and-install-sql-server-express-edition"></a>SQL Server Express Edition をダウンロードおよびインストールするには  
  
1. Internet Explorer を開始します。  
  
2. [Microsoft SQL Server 2005 Express Edition](https://go.microsoft.com/fwlink/?LinkID=31070)のダウンロードページにアクセスします。  
  
3. Web サイトに記載されているインストールの指示に従います。  
  
## <a name="see-also"></a>関連項目

- [はじめに](getting-started-linq-to-dataset.md)
