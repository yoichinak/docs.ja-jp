---
title: '方法 : LINQ を使用したクエリ結果内の最小値と最大値の検索'
ms.date: 07/20/2015
helpviewer_keywords:
- max operator [LINQ in Visual Basic]
- aggregate operator [LINQ in Visual Basic]
- aggregate queries
- minimum values [LINQ in Visual Basic]
- min operator [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], minimum and maximum values
- Max property
- maximum values [LINQ in Visual Basic]
- Aggregate clause [Visual Basic]
- queries [LINQ in Visual Basic], aggregate queries
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 238b763b-7dcd-4b14-8050-b65500a4f71c
ms.openlocfilehash: ef5f218cdcc7275f616486110825ad0b9df11cc3
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112363"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>方法 : LINQ を使用したクエリ結果内の最小値と最大値の検索 (Visual Basic)
統合言語クエリ (LINQ) を使用すると、データベース情報に簡単にアクセスし、クエリを実行できます。  
  
 SQL Server データベースに対してクエリを実行する新しいアプリケーションを作成する方法を次の例に示します。 サンプルでは、 および`Aggregate``Group By`句を使用して、結果の最小値と最大値を決定します。 詳細については、「[集計句](../../../../visual-basic/language-reference/queries/aggregate-clause.md)と[グループ化句](../../../../visual-basic/language-reference/queries/group-by-clause.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データベースを使用します。 開発用コンピューターにこのデータベースがない場合は、Microsoft ダウンロード センターからダウンロードできます。 手順については、「[サンプル データベースのダウンロード」を参照してください](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="create-a-connection-to-a-database"></a>データベースへの接続を作成する  
  
1. Visual Studio で、[**表示**] メニューの **[サーバー エクスプローラ**/**データベース エクスプローラー** ] をクリックして **、サーバー エクスプローラ**/データベース**エクスプローラー**を開きます。  
  
2. **サーバー エクスプローラ**/**データベース エクスプローラ**で **[データ接続**] を右クリックし、[**接続の追加**] をクリックします。  
  
3. ノースウィンド サンプル データベースへの有効な接続を指定してください。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL ファイルを含むプロジェクトを追加するには  
  
1. Visual Studio で、[**ファイル**] メニューの [**新規作成**] をポイントし、[**プロジェクト**] をクリックします。 プロジェクトの種類**として [Visual** Basic Windows フォーム アプリケーション] を選択します。  
  
2. **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。 [LINQ **to SQL クラス]** 項目テンプレートを選択します。  
  
3. このファイルには `northwind.dbml` という名前を付けます。 **[追加]** をクリックします。 northwind.dbml ファイル用にオブジェクト リレーショナル デザイナー (O/R デザイナー) が開かれます。  
  
## <a name="add-tables-to-query-to-the-or-designer"></a>O/R デザイナーにクエリするテーブルを追加する  
  
1. **サーバー エクスプローラ**/**のデータベース エクスプローラ**で、ノースウィンド データベースへの接続を展開します。 **[テーブル]** フォルダーを展開します。  
  
     O/R デザイナーを閉じた場合は、前に追加した northwind.dbml ファイルをダブルクリックして、再度開くことができます。  
  
2. [得意先] テーブルをクリックし、デザイナーの左ペインにドラッグします。 [受注] テーブルをクリックし、デザイナーの左ペインにドラッグします。  
  
     デザイナーは、プロジェクト`Customer`の`Order`新しいオブジェクトとオブジェクトを作成します。 デザイナーは、テーブル間のリレーションシップを自動的に検出し、関連するオブジェクトの子プロパティを作成します。 たとえば、IntelliSense は、その顧客`Customer`に関連するすべての`Orders`注文のプロパティをオブジェクトが持っていることを示します。  
  
3. 変更を保存してデザイナーを閉じます。  
  
4. プロジェクトを保存します。  
  
## <a name="add-code-to-query-the-database-and-display-the-results"></a>データベースにクエリを実行して結果を表示するコードを追加する  
  
1. [**ツールボックス**] から、<xref:System.Windows.Forms.DataGridView>プロジェクトの既定の Windows フォーム Form1 にコントロールをドラッグします。  
  
2. Form1 をダブルクリックして、フォームの`Load`イベントにコードを追加します。  
  
3. テーブルを O/R デザイナーに追加すると、デザイナーによってプロジェクト<xref:System.Data.Linq.DataContext>のオブジェクトが追加されます。 このオブジェクトには、各テーブルの個々のオブジェクトとコレクションに加えて、これらのテーブルにアクセスするために必要なコードが含まれています。 プロジェクト<xref:System.Data.Linq.DataContext>のオブジェクトは、.dbml ファイルの名前に基づいて命名されます。 このプロジェクトでは、オブジェクト<xref:System.Data.Linq.DataContext>の名前`northwindDataContext`は です。  
  
     のインスタンスをコード<xref:System.Data.Linq.DataContext>に作成し、O/R デザイナーで指定されたテーブルにクエリを実行できます。  
  
     イベントに次のコードを`Load`追加します。 このコードは、データ コンテキストのプロパティとして公開されているテーブルを照会し、結果の最小値と最大値を決定します。 このサンプルでは、`Aggregate`この句を使用して 1 つの結果`Group By`を照会し、句を使用してグループ化された結果の平均を表示します。  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. **F5 キー**を押してプロジェクトを実行し、結果を表示します。  
  
## <a name="see-also"></a>関連項目

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [データ コンテキスト メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
