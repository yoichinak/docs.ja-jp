---
title: '方法: LINQ (Visual Basic) を使用してストアド プロシージャを呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], stored procedure calls
- stored procedures sample [Visual Basic]
- stored procedures [LINQ to SQL]
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: 6436d384-d1e0-40aa-8afd-451007477260
ms.openlocfilehash: 2d05d43ae8f9b93fd3e5e405bb7ff0d59832e830
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58823351"
---
# <a name="how-to-call-a-stored-procedure-by-using-linq-visual-basic"></a>方法: LINQ (Visual Basic) を使用してストアド プロシージャを呼び出す
統合言語クエリ (LINQ) を簡単にデータベースなどに格納されているオブジェクトの手順も含め、データベースの情報にアクセスします。  
  
 次の例では、SQL Server データベースでストアド プロシージャを呼び出すアプリケーションを作成する方法を示します。 データベースの 2 つの異なるストアド プロシージャを呼び出す方法を示します。 各手順では、クエリの結果を返します。 1 つのプロシージャは、入力パラメーターを受け取り、その他のプロシージャはパラメーターを取りません。  
  
 このトピックの例では、Northwind サンプル データベースを使用します。 開発用コンピューターにこのデータベースがいない場合は、Microsoft ダウンロード センターからダウンロードできます。 手順については、[サンプル データベースのダウンロード](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)を参照してください。  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>データベースへの接続を作成するには  
  
1.  Visual Studio で開く**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**をクリックして**サーバー エクスプ ローラー**/**データベースエクスプ ローラー**上、**ビュー**メニュー。  
  
2.  右クリック**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**  をクリックし、**接続の追加**します。  
  
3.  Northwind サンプル データベースへの接続を有効なを指定します。  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>LINQ to SQL ファイルを格納しているプロジェクトを追加するには  
  
1.  Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。 Visual Basic を選択**Windows フォーム アプリケーション**プロジェクトの種類として。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。 選択、 **LINQ to SQL クラス**項目テンプレート。  
  
3.  そのファイルに `northwind.dbml` という名前を付けます。 **[追加]** をクリックします。 Northwind.dbml ファイル用には、オブジェクト リレーショナル デザイナー (O/R デザイナー) を開きます。  
  
### <a name="to-add-stored-procedures-to-the-or-designer"></a>ストアド プロシージャを O/R デザイナーに追加するには  
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。 展開、 **Stored Procedures**フォルダー。  
  
     O/R デザイナーを閉じた場合は、先ほど追加した northwind.dbml ファイルをダブルクリックして開くことができます。  
  
2.  をクリックして、 **Sales by Year**ストアド プロシージャと、デザイナーの右ペインにドラッグします。 をクリックして、 **10 最も高価な製品**ストアド プロシージャは、デザイナーの右側のペインにドラッグします。  
  
3.  変更を保存し、デザイナーを閉じます。  
  
4.  プロジェクトを保存します。  
  
### <a name="to-add-code-to-display-the-results-of-the-stored-procedures"></a>ストアド プロシージャの結果を表示するコードを追加するには  
  
1.  **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.DataGridView>に、プロジェクトの Form1 の既定の Windows フォーム コントロール。  
  
2.  コードを追加する Form1 をダブルクリックしてその`Load`イベント。  
  
3.  デザイナーが追加されたストアド プロシージャを O/R デザイナーに追加したときに、<xref:System.Data.Linq.DataContext>プロジェクトのオブジェクト。 このオブジェクトには、これらのプロシージャにアクセスするに必要なコードが含まれています。 <xref:System.Data.Linq.DataContext>オブジェクトの名前は、プロジェクトに基づく .dbml ファイルの名前。 このプロジェクトで、<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`します。  
  
     インスタンスを作成することができます、 <xref:System.Data.Linq.DataContext> O/R デザイナーによって、コードの呼び出しでストアド プロシージャのメソッドを指定します。 バインドする、<xref:System.Windows.Forms.DataGridView>オブジェクト、クエリを強制的に呼び出すことによってすぐに実行する必要があります、<xref:System.Linq.Enumerable.ToList%2A>メソッドでは、ストアド プロシージャの結果。  
  
     次のコードを追加、`Load`データ コンテキストのメソッドとして公開されたストアド プロシージャのいずれかを呼び出すイベントです。  
  
     [!code-vb[VbLINQtoSQLHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#1)]  
    [!code-vb[VbLINQtoSQLHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form3.vb#2)]  
  
4.  F5 キーを押してプロジェクトを実行し、結果を表示します。  
  
## <a name="see-also"></a>関連項目

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [方法: 更新、挿入、および削除を実行するストアド プロシージャを割り当てる (O/R デザイナー)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
