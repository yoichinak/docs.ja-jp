---
title: '方法: LINQ (Visual Basic) を使用してクエリ結果をフィルター処理します。'
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
ms.openlocfilehash: fc4d43ef9181f1a290d37c137b4fc6f7f16588b7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59332054"
---
# <a name="how-to-filter-query-results-by-using-linq-visual-basic"></a>方法: LINQ (Visual Basic) を使用してクエリ結果をフィルター処理します。
統合言語クエリ (LINQ) により、簡単にデータベース情報にアクセスしてクエリを実行できます。  
  
 次の例は、SQL Server データベースに対してクエリを実行し、特定の値で結果をフィルター処理を使用して新しいアプリケーションを作成する方法を示します、`Where`句。 詳細については、次を参照してください。 [Where 句](../../../../visual-basic/language-reference/queries/where-clause.md)します。  
  
 このトピックの例では、Northwind サンプル データベースを使用します。 開発用コンピューターにこのデータベースがいない場合は、Microsoft ダウンロード センターからダウンロードできます。 手順については、次を参照してください。[サンプル データベースのダウンロード](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)します。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>データベースへの接続を作成するには  
  
1. Visual Studio で開く**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**をクリックして**サーバー エクスプ ローラー**/**データベースエクスプ ローラー**上、**ビュー**メニュー。  
  
2. 右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックし、**接続の追加**します。  
  
3. Northwind サンプル データベースへの接続を有効なを指定します。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL ファイルを格納しているプロジェクトを追加するには  
  
1. Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。 Visual Basic を選択**Windows フォーム アプリケーション**プロジェクトの種類として。  
  
2. **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。 選択、 **LINQ to SQL クラス**項目テンプレート。  
  
3. そのファイルに `northwind.dbml` という名前を付けます。 **[追加]** をクリックします。 オブジェクト リレーショナル デザイナー (O/R デザイナー) は、northwind.dbml ファイルが開きます。  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>O/R デザイナーをクエリにテーブルを追加するには  
  
1. **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。 展開、**テーブル**フォルダー。  
  
     O/R デザイナーを閉じた場合は、先ほど追加した northwind.dbml ファイルをダブルクリックして開くことができます。  
  
2. Customers テーブルをクリックし、デザイナーの左側のペインにドラッグします。 Orders テーブルをクリックし、デザイナーの左側のペインにドラッグします。  
  
     デザイナーを新規作成`Customer`と`Order`プロジェクトのオブジェクト。 デザイナーが自動的にテーブル間のリレーションシップを検出し、関連オブジェクトのプロパティの子を作成することに注意してください。 たとえば、IntelliSense が表示されますが、`Customer`オブジェクトには、`Orders`その顧客に関連するすべての注文のプロパティ。  
  
3. 変更を保存し、デザイナーを閉じます。  
  
4. プロジェクトを保存します。  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>データベース クエリを実行し、結果を表示するコードを追加するには  
  
1. **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.DataGridView>に、プロジェクトの Form1 の既定の Windows フォーム コントロール。  
  
2. コードを追加する Form1 をダブルクリックして、`Load`フォームのイベント。  
  
3. O/R デザイナーにテーブルを追加したときに、デザイナーが追加、<xref:System.Data.Linq.DataContext>プロジェクトのオブジェクト。 このオブジェクトには、個々 のオブジェクトと各テーブルのコレクションだけでなく、それらのテーブルにアクセスするに必要なコードが含まれています。 <xref:System.Data.Linq.DataContext>オブジェクトの名前は、プロジェクトに基づく .dbml ファイルの名前。 このプロジェクトで、<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`します。  
  
     インスタンスを作成することができます、 <xref:System.Data.Linq.DataContext> O/R デザイナーによって、コードとクエリにテーブルが指定されています。  
  
     次のコードを追加、`Load`データ コンテキストのプロパティとして公開されるテーブルを照会するイベントです。 クエリの結果をフィルター処理し、内にある顧客のみを返す`London`します。  
  
     [!code-vb[VbLINQToSQLHowTos#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#11)]  
  
4. F5 キーを押してプロジェクトを実行し、結果を表示します。  
  
5. 試用できるその他のいくつかのフィルターを次に示します。  
  
     [!code-vb[VbLINQToSQLHowTos#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form5.vb#12)]  
  
## <a name="see-also"></a>関連項目

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
