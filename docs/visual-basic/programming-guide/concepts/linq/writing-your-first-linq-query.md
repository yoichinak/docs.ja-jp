---
title: 初めての LINQ クエリの作成 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: 6f6968713fdb1c0ec0ee9f9da3b199a649938de5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907479"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>初めての LINQ クエリの作成 (Visual Basic)
"*クエリ*" は、データ ソースからデータを取得する式です。 クエリは、専用のクエリ言語で表現されます。 時間の経過と共にさまざまな言語用に開発したさまざまな種類のデータ ソース、たとえば、SQL のリレーショナル データベースや XML 用の XQuery です。 これにより、必要なアプリケーション開発者はデータ ソースまたはサポートされているデータ形式の種類ごとに新しいクエリ言語について説明します。  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] データ ソースや形式のさまざまな種類のデータを操作するための一貫したモデルを提供することで、この状況を簡略化します。 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリでは、操作の対象は常にオブジェクトになります。 同じ基本的なコーディング パターンを使用して、クエリ対象の XML ドキュメント内のデータ、SQL データベース、ADO.NET データセットとエンティティ、.NET Framework コレクション、および任意の他のソースまたは形式を変換する、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]プロバイダーは使用できます。 このドキュメントは、作成の 3 つのフェーズと basic の使用について説明します。[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ。  
  
## <a name="three-stages-of-a-query-operation"></a>クエリ操作の 3 つの段階  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリ操作では、3 つのアクションで構成されます。  
  
1. データ ソースまたはソースを取得します。  
  
2. クエリを作成します。  
  
3. クエリを実行します。  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリの実行は、クエリの作成とは異なります。 クエリを作成するだけでは、すべてのデータは取得しません。 この点については、後で詳しく説明します。  
  
 次の例は、クエリ操作の 3 つの部分を示しています。 例では、デモンストレーションの便利なデータ ソースとして整数の配列を使用します。 ただし、同じ概念は、他のデータ ソースにも適用されます。  
  
> [!NOTE]
>  [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)、いることを確認**Option infer**に設定されている**で**します。  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Output:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>データ ソース  
 暗黙的にジェネリックをサポート、前の例では、データ ソースが配列であるため、<xref:System.Collections.Generic.IEnumerable%601>インターフェイス。 このファクトのデータ ソースとしての配列を使用することができますが、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ。 <xref:System.Collections.Generic.IEnumerable%601> をサポートする型や、ジェネリック <xref:System.Linq.IQueryable%601> などの派生インターフェイスは、*クエリ可能型*と呼ばれます。  
  
 暗黙的にクエリ可能な型として、配列は必要ありません変更や特別な処理として処理するために、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]データ ソース。 サポートする任意のコレクション型の場合も同様<xref:System.Collections.Generic.IEnumerable%601>、ジェネリックを含む<xref:System.Collections.Generic.List%601>、 <xref:System.Collections.Generic.Dictionary%602>、および、.NET Framework クラス ライブラリの他のクラス。  
  
 ソース データが既に実装しない場合<xref:System.Collections.Generic.IEnumerable%601>、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]の機能を実装するプロバイダーが必要な*標準クエリ演算子*そのデータ ソース。 たとえば、[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]に、クエリ可能な XML ドキュメントの読み込みの処理<xref:System.Xml.Linq.XElement>の次の例に示すように入力します。 標準クエリ演算子の詳細については、次を参照してください。[標準クエリ演算子の概要 (Visual Basic)](standard-query-operators-overview.md)します。  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]、オブジェクト リレーショナル マッピング、デザイン時に手動でまたはを使用して、作成する、 [LINQ to Visual Studio での SQL ツール](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)Visual Studio でします。 オブジェクトに対するクエリを記述すると、実行時には、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] によってデータベースとの通信が処理されます。 次の例では、 `customers` 、データベース内の特定のテーブルを表すと<xref:System.Data.Linq.Table%601>サポート ジェネリック<xref:System.Linq.IQueryable%601>します。  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 それぞれの種類のデータ ソースを作成する方法の詳細については、対応する [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] プロバイダーのドキュメントを参照してください。 (これらのプロバイダーの一覧は、次を参照してください[LINQ (Language-Integrated Query)](../../../../visual-basic/programming-guide/concepts/linq/index.md)。)。基本的な規則は単純です。 を[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]データ ソースは、ジェネリックをサポートする任意のオブジェクト<xref:System.Collections.Generic.IEnumerable%601>インターフェイス、またはこれを継承するインターフェイス。  
  
> [!NOTE]
>  などの型<xref:System.Collections.ArrayList>非ジェネリックをサポートする<xref:System.Collections.IEnumerable>としてインターフェイスを使用することができますも[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]データ ソース。 使用する例については、<xref:System.Collections.ArrayList>を参照してください[方法。LINQ (Visual Basic) の ArrayList を照会](how-to-query-an-arraylist-with-linq.md)します。  
  
## <a name="the-query"></a>クエリ  
 クエリでは、データ ソースまたはソースから取得する情報を指定します。 また、方法その情報は、別にグループ化、並べ替えたりするが返される前に構造化を指定するオプションがあります。 クエリの作成を有効にするには、Visual Basic は、言語に新しいクエリの構文を組み込まいます。  
  
 次の例のクエリが、整数の配列からすべての偶数を返しますが、実行時`numbers`します。  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 クエリ式には、3 つの句が含まれています: `From`、 `Where`、および`Select`します。 特定の関数と各クエリ式の句の目的は、後ほど[基本的なクエリ操作 (Visual Basic)](basic-query-operations.md)します。 詳細については、次を参照してください。[クエリ](../../../../visual-basic/language-reference/queries/index.md)します。 なお[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]、クエリ定義多くの場合は変数に格納し、後で実行します。 クエリ変数など、`evensQuery`前の例では、クエリ可能な型でなければなりません。 型`evensQuery`は`IEnumerable(Of Integer)`、ローカル型推論を使用して、コンパイラによって割り当てられています。  
  
 クエリ変数そのものは何も実行し、データは返されませんことに注意してください。 クエリの定義のみ格納されます。 前の例では、`For Each`クエリを実行するループします。  
  
## <a name="query-execution"></a>クエリの実行  
 クエリの実行は、クエリの作成とは別です。 クエリの作成、クエリを定義しますが、実行は、別のメカニズムによってトリガーされます。 定義されているとすぐにクエリを実行することができます (*即時実行*)、または定義を格納して、後でクエリを実行することができます (*遅延実行*)。  
  
### <a name="deferred-execution"></a>遅延実行  
 一般的な[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリに似ていますが、これで、前の例で`evensQuery`が定義されています。 クエリを作成しますが、そのすぐには実行されません。 クエリの定義をクエリ変数に格納する代わりに、`evensQuery`します。 クエリを実行した後で、通常を使用して、`For Each`またはなど、標準クエリ演算子を適用することで、値のシーケンスを返すには、ループ`Count`または`Max`します。 このプロセスと呼ばれます*遅延実行*します。  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 値のシーケンスの反復変数を使用して取得したデータにアクセスする、`For Each`ループ (`number`前の例)。 クエリ変数`evensQuery`クエリの結果ではなく、クエリの定義を保持して、クエリ変数を 1 つ以上の時間を使用すると、多くの場合、クエリを実行することができます。 たとえば、データベースを別のアプリケーションによって継続的に更新されているアプリケーションでがあります。 使用することがそのデータベースからデータを取得するクエリを作成した後、`For Each`たびに、最新のデータを取得するクエリを繰り返し実行するループします。  
  
 次の例では、遅延実行の動作します。 後`evensQuery2`が定義され、実行すると、`For Each`前の例のように、データ ソースの一部の要素をループ`numbers`変更されます。 2 つ目にし、`For Each`ループを実行`evensQuery2`もう一度です。 結果が異なる 2 つ目の時間のため、`For Each`ループ、クエリが再実行で新しい値を使用して`numbers`します。  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 Output:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>即時実行  
 クエリの遅延実行では、クエリの定義は、後で実行するクエリの変数に格納されます。 即時実行は、クエリがその定義の時点で実行されます。 クエリ結果の個々 の要素へのアクセスを必要とするメソッドを適用すると、実行がトリガーされます。 1 つの値を返す標準クエリ演算子のいずれかを使用して強制的に多くの場合、即時に実行されます。 例としては、 `Count`、 `Max`、 `Average`、および`First`します。 これらの標準クエリ演算子は、計算して単一の結果を返すために適用されるとすぐにクエリを実行します。 1 つの値を返す標準クエリ演算子の詳細については、次を参照してください。[集計操作](aggregation-operations.md)、[要素操作](element-operations.md)、および[量指定子操作](quantifier-operations.md)します。  
  
 次のクエリでは、整数の配列に偶数の数を返します。 クエリの定義は保存されず、および`numEvens`は、単純な`Integer`します。  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 使用して同じ結果を得ることができます、`Aggregate`メソッド。  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 呼び出すことによって、クエリの実行を強制することもできます、`ToList`または`ToArray`(即時) クエリまたは次のコードに示すように、(遅延)、クエリ変数のメソッド。  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 前の例で`evensQuery3`クエリ変数しますですが、`evensList`一覧と`evensArray`は配列です。  
  
 使用して`ToList`または`ToArray`強制的に即時に実行がすぐにクエリを実行し、1 つのコレクション オブジェクトで結果をキャッシュするシナリオに特に便利です。 これらのメソッドの詳細については、次を参照してください。[データ型の変換](converting-data-types.md)します。  
  
 使用して実行するクエリが発生することも、`IEnumerable`などのメソッド、<xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>メソッド。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic の LINQ の概要](getting-started-with-linq.md)
- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [標準クエリ演算子の概要 (Visual Basic)](standard-query-operators-overview.md)
- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
