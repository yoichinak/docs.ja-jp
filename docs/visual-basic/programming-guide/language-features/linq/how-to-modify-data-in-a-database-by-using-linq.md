---
title: '方法: LINQ (Visual Basic) を使用して、データベース内のデータを変更します。'
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: c92a94cd6223aad8e4ea3da86a8dd37bd71aad2c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58820998"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>方法: LINQ (Visual Basic) を使用して、データベース内のデータを変更します。
統合言語クエリ (LINQ) クエリを行う簡単にデータベース情報にアクセスして、データベース内の値を変更します。  
  
 次の例では、SQL Server データベースを取得する新しいアプリケーションを作成する方法と更新プログラムの情報を示します。  
  
 このトピックの例では、Northwind サンプル データベースを使用します。 開発用コンピューターにこのデータベースがいない場合は、Microsoft ダウンロード センターからダウンロードできます。 手順については、[サンプル データベースのダウンロード](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md)を参照してください。  
  
### <a name="to-create-a-connection-to-a-database"></a>データベースへの接続を作成するには  
  
1.  Visual Studio で開く**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**をクリックして、**ビュー** ] メニューの [クリックして**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**します。  
  
2.  右クリックして**データ接続**で**サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、 をクリック**接続の追加**します。  
  
3.  Northwind サンプル データベースへの接続を有効なを指定します。  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>SQL ファイルに、LINQ でのプロジェクトを追加するには  
  
1.  Visual Studio で、**[ファイル]** メニューの **[新規作成]** をポイントし、**[プロジェクト]** をクリックします。 Visual Basic を選択**Windows フォーム アプリケーション**プロジェクトの種類として。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。 選択、 **LINQ to SQL クラス**項目テンプレート。  
  
3.  そのファイルに `northwind.dbml` という名前を付けます。 **[追加]** をクリックします。 オブジェクト リレーショナル デザイナー (O/R デザイナー) が開かれた、`northwind.dbml`ファイル。  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>クエリを実行し、デザイナーを変更するテーブルを追加するには  
  
1.  **サーバー エクスプ ローラー**/**データベース エクスプ ローラー**、Northwind データベースへの接続を展開します。 展開、**テーブル**フォルダー。  
  
     O/R デザイナーを閉じた場合をダブルクリックして開くことができます、`northwind.dbml`先ほど追加したファイル。  
  
2.  Customers テーブルをクリックし、デザイナーの左側のペインにドラッグします。  
  
     デザイナーは、プロジェクトの新しい Customer オブジェクトを作成します。  
  
3.  変更を保存し、デザイナーを閉じます。  
  
4.  プロジェクトを保存します。  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>データベースを変更し、結果を表示するコードを追加するには  
  
1.  **ツールボックス**、ドラッグ、<xref:System.Windows.Forms.DataGridView>に、プロジェクトの Form1 の既定の Windows フォーム コントロール。  
  
2.  O/R デザイナーにテーブルを追加したときに、デザイナーが追加、<xref:System.Data.Linq.DataContext>オブジェクトをプロジェクトにします。 このオブジェクトには、Customers テーブルへのアクセスに使用できるコードが含まれています。 ローカルの Customer オブジェクトと、テーブルの顧客のコレクションを定義するコードも含まれています。 <xref:System.Data.Linq.DataContext>オブジェクトの名前は、プロジェクトに基づく .dbml ファイルの名前。 このプロジェクトで、<xref:System.Data.Linq.DataContext>オブジェクトの名前は`northwindDataContext`します。  
  
     インスタンスを作成することができます、<xref:System.Data.Linq.DataContext>コードとクエリ内のオブジェクトし、O/R デザイナーで指定された顧客のコレクションを変更します。 データベースでは、それらを呼び出すことによって送信されるまで顧客のコレクションに対して行った変更は反映されません、<xref:System.Data.Linq.DataContext.SubmitChanges%2A>のメソッド、<xref:System.Data.Linq.DataContext>オブジェクト。  
  
     コードを追加する Windows フォーム、Form1 をダブルクリックして、 <xref:System.Windows.Forms.Form.Load> Customers テーブルを照会するイベントのプロパティとして公開される、<xref:System.Data.Linq.DataContext>します。 次のコードを追加します。  
  
    ```vb  
    Private db As northwindDataContext  
  
    Private Sub Form1_Load(ByVal sender As System.Object,   
                           ByVal e As System.EventArgs  
                          ) Handles MyBase.Load  
      db = New northwindDataContext()  
  
      RefreshData()  
    End Sub  
  
    Private Sub RefreshData()  
      Dim customers = From cust In db.Customers   
                      Where cust.City(0) = "W"   
                      Select cust  
  
      DataGridView1.DataSource = customers  
    End Sub  
    ```  
  
3.  **ツールボックス**、3 つをドラッグして<xref:System.Windows.Forms.Button>をフォームにコントロール。 最初の選択`Button`コントロール。 **プロパティ**ウィンドウで、設定、`Name`の`Button`に制御を`AddButton`と`Text`に`Add`します。 2 番目のボタンを選択し、設定、`Name`プロパティを`UpdateButton`と`Text`プロパティを`Update`します。 3 番目のボタンを選択し、設定、`Name`プロパティを`DeleteButton`と`Text`プロパティを`Delete`します。  
  
4.  ダブルクリックして、**追加**ボタンのコードを追加するその`Click`イベント。 次のコードを追加します。  
  
    ```vb  
    Private Sub AddButton_Click(ByVal sender As System.Object,   
                                ByVal e As System.EventArgs  
                               ) Handles AddButton.Click  
      Dim cust As New Customer With {   
        .City = "Wellington",   
        .CompanyName = "Blue Yonder Airlines",   
        .ContactName = "Jill Frank",   
        .Country = "New Zealand",   
        .CustomerID = "JILLF"}  
  
      db.Customers.InsertOnSubmit(cust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
5.  ダブルクリック、 **Update**ボタンのコードを追加するその`Click`イベント。 次のコードを追加します。  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"
      updateCust.Country = "Wales"
      updateCust.CompanyName = "Red Yonder Airlines"
      updateCust.City = "Cardiff"
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  ダブルクリック、**削除**ボタンのコードを追加するその`Click`イベント。 次のコードを追加します。  
  
    ```vb  
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles DeleteButton.Click  
      Dim deleteCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      db.Customers.DeleteOnSubmit(deleteCust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
7.  F5 キーを押してプロジェクトを実行します。 クリックして**追加**新しいレコードを追加します。 クリックして**Update**新しいレコードを変更します。 クリックして**削除**新しいレコードを削除します。  
  
## <a name="see-also"></a>関連項目

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
- [方法: 更新、挿入、および削除を実行するストアド プロシージャを割り当てる (O/R デザイナー)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)
