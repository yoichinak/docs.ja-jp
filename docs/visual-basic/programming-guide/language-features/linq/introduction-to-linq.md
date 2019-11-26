---
title: LINQ の概要
ms.date: 08/28/2018
helpviewer_keywords:
- queries [LINQ in Visual Basic], about LINQ in Visual Basic queries
- query execution [LINQ in Visual Basic]
- range variables [Visual Basic]
- LINQ [Visual Basic]
- LINQ [Visual Basic], about LINQ in Visual Basic
- query expressions [LINQ in Visual Basic]
- LINQ
- deferred execution
- iteration variables [Visual Basic]
ms.assetid: 3047d86e-0d49-40e2-928b-dc02e46c7984
ms.openlocfilehash: 610f2a1020cc15f855b3ddfc0917e14aae34fb82
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344935"
---
# <a name="introduction-to-linq-in-visual-basic"></a>Visual Basic における LINQ の概要
Language-Integrated Query (LINQ) adds query capabilities to Visual Basic and provides simple and powerful capabilities when you work with all kinds of data. Rather than sending a query to a database to be processed, or working with different query syntax for each type of data that you are searching, LINQ introduces queries as part of the Visual Basic language. LINQ では、データの型に関係なく、統一された構文を使用します。  
  
 LINQ enables you to query data from a SQL Server database, XML, in-memory arrays and collections, ADO.NET datasets, or any other remote or local data source that supports LINQ. You can do all this with common Visual Basic language elements. Because your queries are written in the Visual Basic language, your query results are returned as strongly-typed objects. これらのオブジェクトは IntelliSense をサポートするので、コードの記述時間を短縮でき、さらに、クエリに含まれるエラーを実行時ではなくコンパイル時に把握できます。 LINQ クエリは、結果を絞り込むための追加クエリのソースとして使用できます。 クエリ結果をユーザーが簡単に表示および変更できるように、コントロールにバインディングすることもできます。  
  
 たとえば、次のコード例は、コレクションから顧客リストを返し、住所に基づいて顧客をグループ化する LINQ クエリを示しています。  
  
 [!code-vb[VbVbalrIntroToLINQ#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#1)]  
  
## <a name="running-the-examples"></a>例の実行  
 To run the examples in the introduction and in the [Structure of a LINQ Query](#structure-of-a-linq-query) section, include the following code, which returns lists of customers and orders.  
  
 [!code-vb[VbVbalrIntroToLINQ#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#31)]  
  
## <a name="linq-providers"></a>LINQ providers  
 A *LINQ provider* maps your Visual Basic LINQ queries to the data source being queried. LINQ クエリを記述すると、そのクエリは、プロバイダーによって、データ ソースが実行できるコマンドに変換されます。 プロバイダーは、ソースのデータを、クエリ結果を構成するオブジェクトに変換する操作も行います。 最後に、プロバイダーは、データ ソースに更新が送信されるときに、オブジェクトをデータに変換します。  
  
 Visual Basic includes the following LINQ providers.  
  
|プロバイダー|説明|  
|---|---|  
|LINQ to Objects|LINQ to Objects プロバイダーは、インメモリ コレクションとインメモリ配列のクエリを可能にします。 オブジェクトが <xref:System.Collections.IEnumerable> インターフェイスまたは <xref:System.Collections.Generic.IEnumerable%601> インターフェイスをサポートしている場合、LINQ to Objects プロバイダーを使用してクエリを実行できます。<br /><br /> You can enable the LINQ to Objects provider by importing the <xref:System.Linq> namespace, which is imported by default for all Visual Basic projects.<br /><br /> For more information about the LINQ to Objects provider, see [LINQ to Objects](../../concepts/linq/linq-to-objects.md).|  
|LINQ to SQL|LINQ to SQL プロバイダーは、SQL Server データベース内のデータのクエリと変更を可能にします。 これにより、アプリケーションのオブジェクト モデルを、データベース内のテーブルとオブジェクトに簡単に対応付けることができます。<br /><br /> Visual Basic makes it easier to work with LINQ to SQL by including the Object Relational Designer (O/R Designer). このデザイナーを使用して、データベース内のオブジェクトに対応付けられるアプリケーション内のオブジェクト モデルを作成します。 The O/R Designer also provides functionality to map stored procedures and functions to the <xref:System.Data.Linq.DataContext> object, which manages communication with the database and stores state for optimistic concurrency checks.<br /><br /> For more information about the LINQ to SQL provider, see [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md). For more information about the Object Relational Designer, see [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).|  
|LINQ to XML|LINQ to XML プロバイダーは、XML のクエリと変更を可能にします。 インメモリ XML を変更することや、XML をファイルから読み込んだりファイルに保存したりすることができます。<br /><br /> Additionally, the LINQ to XML provider enables XML literals and XML axis properties that enable you to write XML directly in your Visual Basic code. For more information, see [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md).|  
|LINQ to DataSet|The LINQ to DataSet provider enables you to query and update data in an ADO.NET dataset. データセットを使用するアプリケーションに LINQ を追加することで、データセット内のデータのクエリ、集計、および更新などの機能を単純化すると同時に拡張できます。<br /><br /> 詳細については、「[LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md)」を参照してください。|  
  
## <a name="structure-of-a-linq-query"></a>Structure of a LINQ query  
 A LINQ query, often referred to as a *query expression*, consists of a combination of query clauses that identify the data sources and iteration variables for the query. クエリ式には、並べ替え、フィルター処理、グループ化、および結合を実行する命令や、ソース データに適用する演算も指定できます。 クエリ式の構文は SQL の構文に似ているので、ほとんどの構文は、改めて覚える必要はありません。  
  
 クエリ式は、`From` 句で始まります。 この句は、クエリのソース データと、ソース データの各要素を個別に参照するために使用される変数を識別します。 These variables are named *range variables* or *iteration variables*. `From` 句は、`Aggregate` クエリ以外のクエリでは必須です。このクエリでは、`From` 句は省略できます。 `From` 句または `Aggregate` 句でクエリのスコープとソースを識別した後、クエリを絞り込むためのクエリ句を自由に組み合わせて記述できます。 For details about query clauses, see Visual Basic LINQ Query Operators later in this topic. たとえば、次のクエリでは、顧客データのソース コレクションを `customers` 変数として識別し、`cust` という名前の反復変数を識別します。  
  
 [!code-vb[VbVbalrIntroToLINQ#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#2)]  
  
 この例はそのままでも有効なクエリですが、結果を絞り込むクエリ句を追加すると、はるかに強力なクエリになります。 たとえば、`Where` 句を追加して、結果を 1 つ以上の値でフィルター処理できます。 クエリ式は、1 行のコードです。追加のクエリ句は、クエリの末尾に単純に追加できます。 You can break up a query across multiple lines of text to improve readability by using the underscore (\_) line-continuation character. 次のコード例は、`Where` 句を含むクエリの例を示しています。  
  
 [!code-vb[VbVbalrIntroToLINQ#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#3)]  
  
 別の強力なクエリ句として、`Select` 句があります。この句を使用すると、データ ソースから選択したフィールドだけを返すことができます。 LINQ クエリは、厳密に型指定されたオブジェクトの列挙可能なコレクションを返します。 クエリは、匿名型または名前付きの型のコレクションを返すことができます。 `Select` 句を使用して、データ ソースから単一のフィールドを返すことができます。 これを行った場合、返されるコレクションの型は、その単一のフィールドの型になります。 `Select` 句を使用して、データ ソースから複数のフィールドを返すこともできます。 これを行った場合、返されるコレクションの型は、新しい匿名型になります。 クエリで返されたフィールドを、指定した名前付きの型のフィールドと一致させることもできます。 次のコード例は、データ ソースから選択されたフィールドのデータが設定されたメンバーのコレクションで、匿名型のコレクションを返すクエリ式を示します。  
  
 [!code-vb[VbVbalrIntroToLINQ#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#4)]  
  
 LINQ クエリを使用して、複数のデータ ソースを結合し、単一の結果を返すこともできます。 これは、1 つまたは複数の `From` 句を使用するか、`Join` クエリ句または `Group Join` クエリ句を使用して実行できます。 次のコード例は、顧客データと注文データを結合し、顧客データと注文データが格納された匿名型のコレクションを返すクエリ式を示します。  
  
 [!code-vb[VbVbalrIntroToLINQ#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#5)]  
  
 `Group Join` 句を使用して、顧客オブジェクトのコレクションを格納する階層的なクエリ結果を作成できます。 各顧客オブジェクトには、その顧客のすべての注文のコレクションを含むプロパティがあります。 次のコード例は、顧客データと注文データを階層的な結果として結合し、匿名型のコレクションを返すクエリ式を示します。 このクエリは、顧客の注文データのコレクションを格納する `CustomerOrders` プロパティを含む型を返します。 その顧客のすべての注文の合計を格納する `OrderTotal` プロパティも含まれます (このクエリは、LEFT OUTER JOIN と同等です)。  
  
 [!code-vb[VbVbalrIntroToLINQ#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/class2.vb#6)]  
  
 上記以外にも、強力なクエリ式を作成するために使用できる、さまざまな LINQ クエリ演算子があります。 このトピックの次のセクションで、クエリ式で使用できるさまざまなクエリ句について説明します。 For details about Visual Basic query clauses, see [Queries](../../../../visual-basic/language-reference/queries/index.md).  
  
## <a name="visual-basic-linq-query-operators"></a>Visual Basic LINQ query operators  

LINQ クエリをサポートする <xref:System.Linq> 名前空間とその他の名前空間のクラスには、アプリケーションの要件に基づいてクエリの作成と絞り込みを行うために呼び出すことができるメソッドが含まれています。 Visual Basic includes keywords for the following common query clauses. For details about Visual Basic query clauses, see [Queries](../../../language-reference/queries/index.md).

### <a name="from-clause"></a>From 句

Either a [`From` clause](../../../../visual-basic/language-reference/queries/from-clause.md) or an `Aggregate` clause is required to begin a query. `From` 句は、クエリのソース コレクションと反復変数を指定します。 (例:

 [!code-vb[VbVbalrIntroToLINQ#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#7)]

### <a name="select-clause"></a>Select 句

省略可能です。 A [`Select` clause](../../../../visual-basic/language-reference/queries/select-clause.md) declares a set of iteration variables for a query. (例:

 [!code-vb[VbVbalrIntroToLINQ#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#8)]

`Select` 句の指定がない場合、クエリの反復変数は、`From` 句または `Aggregate` 句で指定された反復変数で構成されます。

### <a name="where-clause"></a>Where 句

省略可能です。 A [`Where` clause](../../../../visual-basic/language-reference/queries/where-clause.md) specifies a filtering condition for a query. (例:

 [!code-vb[VbVbalrIntroToLINQ#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#9)]

### <a name="order-by-clause"></a>Order By clause]

|Optional. An [`Order By` clause](../../../../visual-basic/language-reference/queries/order-by-clause.md) specifies the sort order for columns in a query. (例:

 [!code-vb[VbVbalrIntroToLINQ#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#10)]

### <a name="join-clause"></a>Join 句

省略可能です。 A [`Join` clause](../../../../visual-basic/language-reference/queries/join-clause.md) combines two collections into a single collection. (例:

 [!code-vb[VbVbalrIntroToLINQ#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#11)]

### <a name="group-by-clause"></a>Group By 句

省略可能です。 A [`Group By` clause](../../../../visual-basic/language-reference/queries/group-by-clause.md) groups the elements of a query result. It can be used to apply aggregate functions to each group. (例:

 [!code-vb[VbVbalrIntroToLINQ#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#12)]

### <a name="group-join-clause"></a>Group Join 句

省略可能です。 A [`Group Join` clause](../../../../visual-basic/language-reference/queries/group-join-clause.md) combines two collections into a single hierarchical collection. (例:

 [!code-vb[VbVbalrIntroToLINQ#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#13)]

### <a name="aggregate-clause"></a>Aggregate 句

Either an [`Aggregate` clause](../../../../visual-basic/language-reference/queries/aggregate-clause.md) or a `From` clause is required to begin a query. `Aggregate` 句は、1 つ以上の集計関数をコレクションに適用します。 For example, you can use the `Aggregate` clause to calculate a sum for all the elements returned by a query, as the following example does.

 [!code-vb[VbVbalrIntroToLINQ#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#14)]

`Aggregate` 句を使用してクエリを変更することもできます。 たとえば、`Aggregate` 句を使用して、関連するクエリ コレクションに対して計算を実行できます。 (例:

 [!code-vb[VbVbalrIntroToLINQ#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#15)]

### <a name="let-clause"></a>Let 句

省略可能です。 A [`Let` clause](../../../../visual-basic/language-reference/queries/let-clause.md) computes a value and assigns it to a new variable in the query. (例:

 [!code-vb[VbVbalrIntroToLINQ#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#16)]

### <a name="distinct-clause"></a>Distinct 句

省略可能です。 A `Distinct` clause restricts the values of the current iteration variable to eliminate duplicate values in query results. (例:

 [!code-vb[VbVbalrIntroToLINQ#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#17)]

### <a name="skip-clause"></a>Skip 句

省略可能です。 A [`Skip` clause](../../../../visual-basic/language-reference/queries/skip-clause.md) bypasses a specified number of elements in a collection and then returns the remaining elements. (例:

 [!code-vb[VbVbalrIntroToLINQ#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#18)]

### <a name="skip-while-clause"></a>Skip While 句

省略可能です。 A [`Skip While` clause](../../../../visual-basic/language-reference/queries/skip-while-clause.md) bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements. (例:

 [!code-vb[VbVbalrIntroToLINQ#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#19)]

### <a name="take-clause"></a>Take 句

省略可能です。 A [`Take` clause](../../../../visual-basic/language-reference/queries/take-clause.md) returns a specified number of contiguous elements from the start of a collection. (例:

 [!code-vb[VbVbalrIntroToLINQ#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#20)]

### <a name="take-while-clause"></a>Take While 句

省略可能です。 A [`Take While` clause](../../../../visual-basic/language-reference/queries/take-while-clause.md) includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements. (例:

 [!code-vb[VbVbalrIntroToLINQ#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#21)]
  
## <a name="use-additional-linq-query-features"></a>Use additional LINQ query features  
  
LINQ によって提供される列挙可能でクエリ可能な型のメンバーを呼び出すことで、追加の LINQ クエリ機能を使用できます。 これらの追加機能は、クエリ式の結果に対して特定のクエリ演算子を呼び出すことで使用できます。 For example, the following example uses the <xref:System.Linq.Enumerable.Union%2A?displayProperty=nameWithType> method to combine the results of two queries into one query result. また、<xref:System.Linq.Enumerable.ToList%2A?displayProperty=nameWithType> メソッドを使用して、クエリ結果をジェネリック リストとして返します。
  
 [!code-vb[VbVbalrIntroToLINQ#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrIntroToLINQ/VB/Class1.vb#22)]  
  
 For details about additional LINQ capabilities, see [Standard Query Operators Overview](../../concepts/linq/standard-query-operators-overview.md).  
  
## <a name="connect-to-a-database-by-using-linq-to-sql"></a>Connect to a database by using LINQ to SQL  
 In Visual Basic, you identify the SQL Server database objects, such as tables, views, and stored procedures, that you want to access by using a LINQ to SQL file. LINQ to SQL ファイルには、.dbml という拡張子が付きます。  
  
 When you have a valid connection to a SQL Server database, you can add a **LINQ to SQL Classes** item template to your project. これを行うと、オブジェクト リレーショナル デザイナー (O/R デザイナー) が表示されます。 The O/R Designer enables you to drag the items that you want to access in your code from the **Server Explorer**/**Database Explorer** onto the designer surface. LINQ to SQL ファイルは、<xref:System.Data.Linq.DataContext> オブジェクトをプロジェクトに追加します。 このオブジェクトには、アクセスするテーブルとビューのプロパティおよびコレクションと、呼び出すストアド プロシージャのメソッドが格納されます。 変更を LINQ to SQL (.dbml) ファイルに保存した後、O/R デザイナーで定義された <xref:System.Data.Linq.DataContext> オブジェクトを参照することで、コード内でこれらのオブジェクトにアクセスできます。 プロジェクトの <xref:System.Data.Linq.DataContext> オブジェクトには、LINQ to SQL ファイルの名前に基づいて名前が付けられます。 たとえば、Northwind.dbml という名前の LINQ to SQL ファイルの場合は、<xref:System.Data.Linq.DataContext> という名前の `NorthwindDataContext` オブジェクトが作成されます。  
  
 For examples with step-by-step instructions, see [How to: Query a Database](how-to-query-a-database-by-using-linq.md) and [How to: Call a Stored Procedure](how-to-call-a-stored-procedure-by-using-linq.md).  
  
## <a name="visual-basic-features-that-support-linq"></a>Visual Basic features that support LINQ  
 Visual Basic includes other notable features that make the use of LINQ simple and reduce the amount of code that you must write to perform LINQ queries. 次に例を示します。  
  
- **Anonymous types**, which enable you to create a new type based on a query result.  
  
- **Implicitly typed variables**, which enable you to defer specifying a type and let the compiler infer the type based on the query result.  
  
- **Extension methods**, which enable you to extend an existing type with your own methods without modifying the type itself.  
  
 For details, see [Visual Basic Features That Support LINQ](../../concepts/linq/features-that-support-linq.md).  
  
## <a name="deferred-and-immediate-query-execution"></a>Deferred and immediate query execution

 クエリの実行とクエリの作成は分離しています。 クエリを作成した後、その実行は、別のメカニズムによってトリガーされます。 A query can be executed as soon as it is defined (*immediate execution*), or the definition can be stored and the query can be executed later (*deferred execution*).  
  
 既定では、クエリを作成しても、クエリ自体が直ちに実行されることはありません。 代わりに、クエリ結果を参照するために使用される変数にクエリ定義が格納されます。 そのクエリ結果変数が、後でコード内の `For…Next` ループなどでアクセスされると、クエリが実行されます。 This process is referred to as *deferred execution*.  
  
 Queries can also be executed when they are defined, which is referred to as *immediate execution*. 即時実行は、クエリ結果の個々の要素にアクセスする必要があるメソッドを適用することで開始できます。 `Count`、`Sum`、`Average`、`Min`、`Max` などの集計関数を含めることで、この結果を得ることができます。 For more information about aggregate functions, see [Aggregate Clause](../../../language-reference/queries/aggregate-clause.md).  
  
 `ToList` メソッドまたは `ToArray` メソッドを使用することでも、即時実行を開始できます。 これは、クエリを直ちに実行し、結果をキャッシュする場合に役に立ちます。 For more information about these methods, see [Converting Data Types](../../concepts/linq/converting-data-types.md).  
  
 For more information about query execution, see [Writing Your First LINQ Query](../../concepts/linq/writing-your-first-linq-query.md).  
  
## <a name="xml-in-visual-basic"></a>Visual Basic における XML  
 The XML features in Visual Basic include XML literals and XML axis properties, which enable you easily to create, access, query, and modify XML in your code. XML リテラルを使用すると、XML をコード内に直接記述できます。 Visual Basic コンパイラは、XML を、最初のクラスのデータ オブジェクトとして処理します。  
  
 次のコード例は、XML 要素を作成し、そのサブ要素と属性にアクセスし、LINQ を使用してその要素の内容を照会する方法を示しています。  
  
 [!code-vb[VbXmlSamples#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples3.vb#8)]  
  
 For more information, see [XML](../xml/index.md).  
  
## <a name="related-resources"></a>関連資料  
  
|トピック|説明|  
|---|---|  
|[XML](../../language-features/xml/index.md)|Describes the XML features in Visual Basic that can be queried and that enable you to include XML as first-class data objects in your Visual Basic code.|  
|[クエリ](../../../language-reference/queries/index.md)|Provides reference information about the query clauses that are available in Visual Basic.|  
|[統合言語クエリ (LINQ)](../../concepts/linq/index.md)|LINQ の概要、プログラミング ガイド、およびサンプルを示します。|  
|[LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)|LINQ to SQL の概要、プログラミング ガイド、およびサンプルを示します。|  
|[LINQ to Objects](../../concepts/linq/linq-to-objects.md)|LINQ to Objects の概要、プログラミング ガイド、およびサンプルを示します。|  
|[LINQ to ADO.NET (ポータル ページ)](../../concepts/linq/linq-to-adonet-portal-page.md)|Includes links to general information, programming guidance, and samples for LINQ to ADO.NET.|  
|[LINQ to XML](../../concepts/linq/linq-to-xml.md)|LINQ to XML の概要、プログラミング ガイド、およびサンプルを示します。|  
  
## <a name="how-to-and-walkthrough-topics"></a>How to and walkthrough topics
 [方法: データベースの照会](how-to-query-a-database-by-using-linq.md)  
  
 [方法 : ストアド プロシージャの呼び出し](how-to-call-a-stored-procedure-by-using-linq.md)  
  
 [方法: データベースのデータの変更](how-to-modify-data-in-a-database-by-using-linq.md)  
  
 [方法 : 結合を使用したデータの結合](how-to-combine-data-with-linq-by-using-joins.md)  
  
 [方法: クエリ結果を並べ替える](how-to-sort-query-results-by-using-linq.md)  
  
 [方法 : クエリ結果のフィルター処理](how-to-filter-query-results-by-using-linq.md)  
  
 [方法 : データの数、合計、または平均の算出](how-to-count-sum-or-average-data-by-using-linq.md)  
  
 [方法 : クエリ結果内の最小値と最大値の検索](how-to-find-the-minimum-or-maximum-value-in-a-query-result.md)  
  
 [方法: 更新、挿入、および削除を実行するストアド プロシージャを割り当てる (O/R デザイナー)](/visualstudio/data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer)  
  
## <a name="featured-book-chapters"></a>Featured book chapters  
 [Chapter 17: LINQ](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652502(v=orm.10)) in [Programming Visual Basic 2008](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/ff652504(v=orm.10))  
  
## <a name="see-also"></a>関連項目

- [統合言語クエリ (LINQ)](../../concepts/linq/index.md)
- [Visual Basic における LINQ to XML の概要](../../language-features/xml/overview-of-linq-to-xml.md)
- [LINQ to DataSet の概要](../../../../framework/data/adonet/linq-to-dataset-overview.md)
- [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)
- [Visual Studio の LINQ to SQL ツール](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)
- [DataContext メソッド (O/R デザイナー)](/visualstudio/data-tools/datacontext-methods-o-r-designer)
