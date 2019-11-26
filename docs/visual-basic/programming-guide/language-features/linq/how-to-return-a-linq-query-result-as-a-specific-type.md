---
title: '方法 : 特定の型での LINQ クエリ結果の取得'
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], specific type returned
- projection [LINQ in Visual Basic]
- anonymous types [Visual Basic]
- querying databases [LINQ]
- queries [LINQ in Visual Basic], how-to topics
- query samples [Visual Basic]
ms.assetid: 621bb10a-e5d7-44fb-a025-317964b19d92
ms.openlocfilehash: 1084743b0c50d381375b76a3116ed7c9e6f9d769
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354200"
---
# <a name="how-to-return-a-linq-query-result-as-a-specific-type-visual-basic"></a>方法 : LINQ クエリ結果を特定の型で返す (Visual Basic)
Language-Integrated Query (LINQ) makes it easy to access database information and execute queries. By default, LINQ queries return a list of objects as an anonymous type. You can also specify that a query return a list of a specific type by using the `Select` clause.  
  
 The following example shows how to create a new application that performs queries against a SQL Server database and projects the results as a specific named type. For more information, see [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md) and [Select Clause](../../../../visual-basic/language-reference/queries/select-clause.md).  
  
 The examples in this topic use the Northwind sample database. If you do not have this database on your development computer, you can download it from the Microsoft Download Center. For instructions, see [Downloading Sample Databases](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-connection-to-a-database"></a>To create a connection to a database  
  
1. In Visual Studio, open **Server Explorer**/**Database Explorer** by clicking **Server Explorer**/**Database Explorer** on the **View** menu.  
  
2. Right-click **Data Connections** in **Server Explorer**/**Database Explorer** and then click **Add Connection**.  
  
3. Specify a valid connection to the Northwind sample database.  
  
### <a name="to-add-a-project-that-contains-a-linq-to-sql-file"></a>To add a project that contains a LINQ to SQL file  
  
1. Visual Studio で、 **[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。 Select Visual Basic **Windows Forms Application** as the project type.  
  
2. **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。 Select the **LINQ to SQL Classes** item template.  
  
3. そのファイルに `northwind.dbml` という名前を付けます。 **[追加]** をクリックします。 The Object Relational Designer (O/R Designer) is opened for the northwind.dbml file.  
  
### <a name="to-add-tables-to-query-to-the-or-designer"></a>To add tables to query to the O/R Designer  
  
1. In **Server Explorer**/**Database Explorer**, expand the connection to the Northwind database. Expand the **Tables** folder.  
  
     If you have closed the O/R Designer, you can reopen it by double-clicking the northwind.dbml file that you added earlier.  
  
2. Click the Customers table and drag it to the left pane of the designer.  
  
     The designer creates a new `Customer` object for your project. You can project a query result as the `Customer` type or as a type that you create. This sample will create a new type in a later procedure and project a query result as that type.  
  
3. Save your changes and close the designer.  
  
4. プロジェクトを保存します。  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>To add code to query the database and display the results  
  
1. From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.  
  
2. Double-click Form1 to modify the Form1 class.  
  
3. After the `End Class` statement of the Form1 class, add the following code to create a `CustomerInfo` type to hold the query results for this sample.  
  
     [!code-vb[VbLINQToSQLHowTos#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#16)]  
  
4. When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object to your project. This object contains the code that you must have to access those tables, and to access individual objects and collections for each table. The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file. For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.  
  
     You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.  
  
     In the `Load` event of the Form1 class, add the following code to query the tables that are exposed as properties of your data context. The `Select` clause of the query will create a new `CustomerInfo` type instead of an anonymous type for each item of the query result.  
  
     [!code-vb[VbLINQToSQLHowTos#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form8.vb#15)]  
  
5. Press F5 to run your project and view the results.  
  
## <a name="see-also"></a>関連項目

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
