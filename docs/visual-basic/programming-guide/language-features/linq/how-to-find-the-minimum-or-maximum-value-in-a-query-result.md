---
title: 'How to: Find the Minimum or Maximum Value in a Query Result by Using LINQ'
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
ms.openlocfilehash: bddb90baa0b01fd9d724583b472af9f9fa7569e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344977"
---
# <a name="how-to-find-the-minimum-or-maximum-value-in-a-query-result-by-using-linq-visual-basic"></a>方法 : LINQ を使用したクエリ結果内の最小値と最大値の検索 (Visual Basic)
Language-Integrated Query (LINQ) makes it easy to access database information and execute queries.  
  
 The following example shows how to create a new application that performs queries against a SQL Server database. The sample determines the minimum and maximum values for the results by using the `Aggregate` and `Group By` clauses. For more information, see [Aggregate Clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) and [Group By Clause](../../../../visual-basic/language-reference/queries/group-by-clause.md).  
  
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
  
2. Click the Customers table and drag it to the left pane of the designer. Click the Orders table and drag it to the left pane of the designer.  
  
     The designer creates new `Customer` and `Order` objects for your project. Notice that the designer automatically detects relationships between the tables and creates child properties for related objects. For example, IntelliSense will show that the `Customer` object has an `Orders` property for all orders related to that customer.  
  
3. Save your changes and close the designer.  
  
4. プロジェクトを保存します。  
  
### <a name="to-add-code-to-query-the-database-and-display-the-results"></a>To add code to query the database and display the results  
  
1. From the **Toolbox**, drag a <xref:System.Windows.Forms.DataGridView> control onto the default Windows Form for your project, Form1.  
  
2. Double-click Form1 to add code to the `Load` event of the form.  
  
3. When you added tables to the O/R Designer, the designer added a <xref:System.Data.Linq.DataContext> object for your project. This object contains the code that you must have to access those tables, in addition to individual objects and collections for each table. The <xref:System.Data.Linq.DataContext> object for your project is named based on the name of your .dbml file. For this project, the <xref:System.Data.Linq.DataContext> object is named `northwindDataContext`.  
  
     You can create an instance of the <xref:System.Data.Linq.DataContext> in your code and query the tables specified by the O/R Designer.  
  
     Add the following code to the `Load` event. This code queries the tables that are exposed as properties of your data context and determines the minimum and maximum values for the results. The sample uses he `Aggregate` clause to query for a single result, and the `Group By` clause to show an average for grouped results.  
  
     [!code-vb[VbLINQToSQLHowTos#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQtoSQLHowTos/VB/Form7.vb#14)]  
  
4. Press F5 to run your project and view the results.  
  
## <a name="see-also"></a>関連項目

- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [DataContext メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
