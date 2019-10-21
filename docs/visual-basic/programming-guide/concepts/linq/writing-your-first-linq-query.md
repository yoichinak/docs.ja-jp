---
title: 初めての LINQ クエリの作成 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- queries [LINQ in Visual Basic], writing
- LINQ queries [Visual Basic]
- LINQ [Visual Basic], writing queries
ms.assetid: 4affb732-3e9b-4479-aa31-1f9bd8183cbe
ms.openlocfilehash: 5c83d888f65ce5c216327e94c5d4d1267fb93c29
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952010"
---
# <a name="writing-your-first-linq-query-visual-basic"></a>初めての LINQ クエリの作成 (Visual Basic)
"*クエリ*" は、データ ソースからデータを取得する式です。 クエリは専用のクエリ言語で表現されます。 時間の経過と共に、さまざまな種類のデータソースに対してさまざまな言語が開発されています。たとえば、リレーショナルデータベース用の SQL や XML 用の XQuery などです。 これにより、アプリケーション開発者は、サポートされているデータソースの種類やデータ形式ごとに新しいクエリ言語を習得する必要があります。  
  
 [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]では、さまざまな種類のデータソースと形式でデータを操作するための一貫したモデルを提供することで、状況を簡単にすることができます。 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] クエリでは、操作の対象は常にオブジェクトになります。 同じ基本的なコーディングパターンを使用して、XML ドキュメント、SQL データベース、ADO.NET データセットとエンティティ、.NET Framework コレクション、および[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]プロバイダーが使用可能なその他のソースまたは形式のデータのクエリと変換を行います。 このドキュメントでは、基本的な[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリの作成と使用に関する3つのフェーズについて説明します。  
  
## <a name="three-stages-of-a-query-operation"></a>クエリ操作の3つの段階  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ操作は、次の3つのアクションで構成されます。  
  
1. データソースを取得します。  
  
2. クエリを作成します。  
  
3. クエリを実行します。  
  
 で[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]は、クエリの実行はクエリの作成とは異なります。 クエリを作成するだけでは、データを取得しません。 この点については、後で詳しく説明します。  
  
 次の例では、クエリ操作の3つの部分について説明します。 この例では、デモンストレーション用の便利なデータソースとして整数の配列を使用します。 ただし、同じ概念が他のデータソースにも適用されます。  
  
> [!NOTE]
> [[コンパイル] ページのプロジェクトデザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)で、[**推定]** が **[オン**] に設定されていることを確認します。  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 Output:  
  
 `0 2 4 6`  
  
## <a name="the-data-source"></a>データ ソース  
 前の例のデータソースは配列であるため、暗黙的にジェネリック<xref:System.Collections.Generic.IEnumerable%601>インターフェイスがサポートされます。 これは、 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリのデータソースとして配列を使用できるようにするためのものです。 <xref:System.Collections.Generic.IEnumerable%601> をサポートする型や、ジェネリック <xref:System.Linq.IQueryable%601> などの派生インターフェイスは、*クエリ可能型*と呼ばれます。  
  
 暗黙的にクエリ可能な型として、配列は[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]データソースとして機能する変更や特別な処理を必要としません。 をサポート<xref:System.Collections.Generic.IEnumerable%601>する任意のコレクション型に対しても同じことが当て<xref:System.Collections.Generic.Dictionary%602>はまります。これには、ジェネリック<xref:System.Collections.Generic.List%601>、、および .NET Framework クラスライブラリ内のその他のクラスが含まれます。  
  
 ソースデータにまだが実装<xref:System.Collections.Generic.IEnumerable%601>されていない場合は[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 、そのデータソースの*標準クエリ演算子*の機能を実装するためにプロバイダーが必要です。 たとえば、は[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 、次の例に示すように、クエリ<xref:System.Xml.Linq.XElement>可能な型に XML ドキュメントを読み込む作業を処理します。 標準クエリ演算子の詳細については、「[標準クエリ演算子の概要 (Visual Basic)](standard-query-operators-overview.md)」を参照してください。  
  
 [!code-vb[VbLINQFirstQuery#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#2)]  
  
 では、まず、デザイン時に、手動で、または visual studio の[visual studio の LINQ to SQL ツール](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2)を使用して、オブジェクトリレーショナルマッピングを作成します。 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] オブジェクトに対するクエリを記述すると、実行時には、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] によってデータベースとの通信が処理されます。 次の例では`customers` 、はデータベース内の特定のテーブルを<xref:System.Data.Linq.Table%601>表し、 <xref:System.Linq.IQueryable%601>ジェネリックをサポートしています。  
  
```vb  
' Create a data source from a SQL table.  
Dim db As New DataContext("C:\Northwind\Northwnd.mdf")  
Dim customers As Table(Of Customer) = db.GetTable(Of Customer)  
```  
  
 それぞれの種類のデータ ソースを作成する方法の詳細については、対応する [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] プロバイダーのドキュメントを参照してください。 (これらのプロバイダーの一覧については、[LINQ (統合言語クエリ)](../../../../visual-basic/programming-guide/concepts/linq/index.md)に関するページを参照してください)基本的な規則は単純です。 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]データソースは、ジェネリック<xref:System.Collections.Generic.IEnumerable%601>インターフェイスをサポートする任意のオブジェクト、またはそれを継承するインターフェイスです。  
  
> [!NOTE]
> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]非ジェネリック<xref:System.Collections.IEnumerable>インターフェイスをサポートするなどの型は、データソースとしても<xref:System.Collections.ArrayList>使用できます。 を使用<xref:System.Collections.ArrayList>する例については[、「方法:LINQ (Visual Basic)](how-to-query-an-arraylist-with-linq.md)を使用して ArrayList に対してクエリを実行します。  
  
## <a name="the-query"></a>クエリ  
 このクエリでは、データソースから取得する情報を指定します。 また、返される前に、その情報を並べ替え、グループ化、または構造化する方法を指定することもできます。 クエリの作成を有効にするために、Visual Basic は新しいクエリ構文を言語に組み込みました。  
  
 次の例のクエリを実行すると、整数配列`numbers`のすべての偶数が返されます。  
  
 [!code-vb[VbLINQFirstQuery#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#1)]  
  
 クエリ式には`From`、、 `Where`、および`Select`の3つの句が含まれています。 各クエリ式句の特定の関数と目的については、 [「基本的なクエリ操作 (Visual Basic)](basic-query-operations.md)」で説明されています。 詳細については、「[クエリ](../../../../visual-basic/language-reference/queries/index.md)」を参照してください。 で[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]は、多くの場合、クエリ定義は変数に格納され、後で実行されることに注意してください。 前の例のなどの`evensQuery`クエリ変数は、クエリ可能な型である必要があります。 の`evensQuery`型は`IEnumerable(Of Integer)`で、ローカル型推論を使用してコンパイラによって割り当てられます。  
  
 クエリ変数自体は何も処理を行わず、データを返さないことに注意する必要があります。 クエリ定義だけが格納されます。 前の例では、クエリを`For Each`実行するループになっています。  
  
## <a name="query-execution"></a>クエリの実行  
 クエリの実行は、クエリの作成とは別のものです。 クエリの作成ではクエリを定義しますが、実行は別のメカニズムによってトリガーされます。 クエリは、定義直後 (*即時実行*) に実行することも、定義を保存し、後でクエリを実行することもできます (*遅延実行*)。  
  
### <a name="deferred-execution"></a>遅延実行  
 一般的[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]なクエリは、 `evensQuery`が定義されている前の例のクエリに似ています。 クエリは作成されますが、すぐには実行されません。 代わりに、クエリ定義はクエリ変数`evensQuery`に格納されます。 後でクエリを実行します。通常は`For Each` 、値のシーケンスを返すループを使用するか、標準のクエリ演算子 ( `Count`や`Max`など) を適用します。 このプロセスを*遅延実行*と呼びます。  
  
 [!code-vb[VbLINQFirstQuery#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#7)]  
  
 値のシーケンスの場合は、ループの`For Each`繰り返し変数 (`number`前の例では) を使用して、取得したデータにアクセスします。 クエリ変数`evensQuery`はクエリの結果ではなくクエリ定義を保持するので、クエリ変数を複数回使用して、必要な頻度でクエリを実行できます。 たとえば、アプリケーション内に、別のアプリケーションによって継続的に更新されるデータベースがあるとします。 そのデータベースからデータを取得するクエリを作成したら、ループを`For Each`使用してクエリを繰り返し実行し、毎回最新のデータを取得することができます。  
  
 次の例は、遅延実行のしくみを示しています。 前の例のように、 `For Each` `numbers` `evensQuery2`を定義してループで実行すると、データソース内の一部の要素が変更されます。 次に、 `For Each` 2 番`evensQuery2`目のループが再び実行されます。 `For Each` の`numbers`新しい値を使用して、ループによってクエリが再実行されるため、結果は2回目に異なります。  
  
 [!code-vb[VbLINQFirstQuery#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#3)]  
  
 Output:  
  
 `Evens in original array:`  
  
 `0  2  4  6`  
  
 `Evens in changed array:`  
  
 `0  10  2  22  8`  
  
### <a name="immediate-execution"></a>即時実行  
 クエリの遅延実行では、クエリ定義は、後で実行するためにクエリ変数に格納されます。 即時実行では、クエリは定義時に実行されます。 クエリ結果の個々の要素へのアクセスを必要とするメソッドを適用すると、実行がトリガーされます。 即時実行は、通常、単一の値を返す標準クエリ演算子の1つを使用することによって強制されます。 例と`Count`して`Average` `Max` 、`First`、、、があります。 これらの標準クエリ演算子は、シングルトンの結果を計算して返すために、適用されるとすぐにクエリを実行します。 単一の値を返す標準クエリ演算子の詳細については、「[集計操作](aggregation-operations.md)、[要素の操作](element-operations.md)、および[量指定子の操作](quantifier-operations.md)」を参照してください。  
  
 次のクエリでは、整数の配列に含まれる偶数の数が返されます。 クエリ定義は保存`numEvens`されず、単純`Integer`なです。  
  
 [!code-vb[VbLINQFirstQuery#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#4)]  
  
 `Aggregate`メソッドを使用すると、同じ結果を得ることができます。  
  
 [!code-vb[VbLINQFirstQuery#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#5)]  
  
 `ToList`また、次のコードに示すように、クエリ (イミディエイト) またはクエリ変数 (遅延) に対してメソッドまたは`ToArray`メソッドを呼び出すことによって、クエリの実行を強制することもできます。  
  
 [!code-vb[VbLINQFirstQuery#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQFirstQuery/VB/Class1.vb#6)]  
  
 前の例では`evensQuery3` 、はクエリ変数ですが`evensList` 、はリスト`evensArray`で、は配列です。  
  
 また`ToList` は`ToArray`を使用して即時実行を強制するのは、クエリをすぐに実行し、結果を単一のコレクションオブジェクトにキャッシュする場合に特に便利です。 これらのメソッドの詳細については、「[データ型の変換](converting-data-types.md)」を参照してください。  
  
 メソッドなどの`IEnumerable` <xref:Microsoft.VisualBasic.Collection.System%23Collections%23IEnumerable%23GetEnumerator%2A>メソッドを使用して、クエリを実行することもできます。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic の LINQ の概要](getting-started-with-linq.md)
- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [標準クエリ演算子の概要 (Visual Basic)](standard-query-operators-overview.md)
- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
