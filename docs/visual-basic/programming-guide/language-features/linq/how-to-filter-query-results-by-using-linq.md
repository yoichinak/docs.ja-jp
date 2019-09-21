---
title: '方法: LINQ (Visual Basic) を使用してクエリ結果をフィルター処理する'
ms.date: 07/20/2015
helpviewer_keywords:
- filtering [Visual Basic]
- filtering data [LINQ in Visual Basic]
- filtering [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], filtering results
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
- filtering data [Visual Basic]
ms.assetid: ef103092-9bed-4134-97f4-2db696e83c12
ms.openlocfilehash: 1250f2fe0ccd7661b9bc1986000143ec4a15a9f0
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053289"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a>方法: LINQ (Visual Basic) を使用してクエリ結果をフィルター処理する

統合言語クエリ (LINQ) を使用すると、データベース情報に簡単にアクセスしてクエリを実行できます。

次の例では、SQL Server データベースに対してクエリを実行し、 `Where`句を使用して結果を特定の値でフィルター処理する新しいアプリケーションを作成する方法を示します。 詳細については、「 [Where 句](../../../../visual-basic/language-reference/queries/where-clause.md)」を参照してください。

このトピックの例では、Northwind サンプルデータベースを使用します。 開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロードセンターからダウンロードできます。 手順については、「[サンプルデータベースのダウンロード](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)」を参照してください。

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-a-connection-to-a-database"></a>データベースへの接続を作成するには

1. Visual Studio で、**表示** メニューの **サーバーエクスプローラー**/の**データベースエクスプローラー**をクリックして**サーバーエクスプローラー**/**データベースエクスプローラー**を開きます。

2. **サーバーエクスプローラー** データベースエクスプローラー/で データ接続 を右クリックし、**接続の追加** をクリックします。

3. Northwind サンプルデータベースへの有効な接続を指定します。

## <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL ファイルを含むプロジェクトを追加するには

1. Visual Studio で、 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。 プロジェクトの種類として [Visual Basic **Windows フォームアプリケーション**] を選択します。

2. **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。 **[LINQ to SQL Classes]** 項目テンプレートを選択します。

3. そのファイルに `northwind.dbml` という名前を付けます。 **[追加]** をクリックします。 Northwind .dbml ファイルのオブジェクトリレーショナルデザイナー (O/R デザイナー) が開きます。

## <a name="to-add-tables-to-query-to-the-or-designer"></a>O/R デザイナーに対してクエリを実行するテーブルを追加するには

1. **サーバーエクスプローラー**/**データベースエクスプローラー**で、Northwind データベースへの接続を展開します。 **[テーブル]** フォルダーを展開します。

     O/R デザイナーを閉じた場合は、前の手順で追加した northwind .dbml ファイルをダブルクリックして再度開くことができます。

2. Customers テーブルをクリックし、デザイナーの左ペインにドラッグします。 [Orders] テーブルをクリックし、デザイナーの左ペインにドラッグします。

     デザイナーは、プロジェクト`Customer`の`Order`新しいオブジェクトとオブジェクトを作成します。 デザイナーがテーブル間のリレーションシップを自動的に検出し、関連するオブジェクトの子プロパティを作成することに注意してください。 たとえば、IntelliSense は、 `Customer`オブジェクトに、その顧客に関連するすべての注文の`Orders`プロパティがあることを示します。

3. 変更を保存し、デザイナーを閉じます。

4. プロジェクトを保存します。

## <a name="to-add-code-to-query-the-database-and-display-the-results"></a>データベースに対してクエリを実行し、結果を表示するコードを追加するには

1. **[ツールボックス]** からコントロール<xref:System.Windows.Forms.DataGridView>を、Form1 というプロジェクトの既定の Windows フォームにドラッグします。

2. Form1 をダブルクリックして、フォームの`Load`イベントにコードを追加します。

3. O/R デザイナーにテーブルを追加すると、デザイナーによって<xref:System.Data.Linq.DataContext>プロジェクトのオブジェクトが追加されます。 このオブジェクトには、各テーブルの個々のオブジェクトとコレクションに加えて、それらのテーブルにアクセスするために必要なコードが含まれています。 プロジェクト<xref:System.Data.Linq.DataContext>のオブジェクトには、.dbml ファイルの名前に基づいた名前が付けられます。 このプロジェクトの場合、 <xref:System.Data.Linq.DataContext>オブジェクトには`northwindDataContext`という名前が付けられます。

    コード<xref:System.Data.Linq.DataContext>でのインスタンスを作成し、O/R デザイナーによって指定されたテーブルに対してクエリを実行できます。

    `Load`イベントに次のコードを追加して、データコンテキストのプロパティとして公開されているテーブルに対してクエリを実行します。 クエリは結果をフィルター処理し、に`London`配置されている顧客のみを返します。

    [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]

4. F5 キーを押してプロジェクトを実行し、結果を表示します。

5. 他にも、次のようなフィルターを試してみることができます。

    [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]

## <a name="see-also"></a>関連項目

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
