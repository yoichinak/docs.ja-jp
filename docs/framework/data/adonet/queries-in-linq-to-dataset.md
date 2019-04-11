---
title: LINQ to DataSet でのクエリ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c1a78fa8-9f0c-40bc-a372-5575a48708fe
ms.openlocfilehash: f4458639aa2c78e7c78bdae66fa2b20d5546743c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102545"
---
# <a name="queries-in-linq-to-dataset"></a>LINQ to DataSet でのクエリ
クエリは、データ ソースからデータを取得する式です。 一般に、クエリは専用のクエリ言語で表現されます。たとえば、リレーショナル データベースであれば SQL、XML であれば XQuery が使用されます。 そのため、開発者はクエリの対象となるデータ ソースやデータ形式ごとに新しいクエリ言語を習得する必要があります。 [!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)] データ ソースや形式のさまざまな種類のデータを操作するための単純化し、一貫性のあるモデルを提供します。 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] クエリでは、常にプログラミング オブジェクトを操作することになります。  
  
 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] のクエリ操作は、データ ソースを取得し、クエリを作成して、クエリを実行するという 3 つのアクションから成ります。  
  
 
  <xref:System.Collections.Generic.IEnumerable%601> を介したクエリは、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] ジェネリック インターフェイスを実装するデータ ソースに対して行うことができます。 呼び出す<xref:System.Data.DataTableExtensions.AsEnumerable%2A>上、<xref:System.Data.DataTable>ジェネリックを実装するオブジェクトを返します<xref:System.Collections.Generic.IEnumerable%601>のデータ ソースとして機能するインターフェイスを[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]クエリ。  
  
 クエリでは、データ ソースから取得する情報を正確に指定できます。 また、並べ替え、グループ化、整形方法を指定して情報を取得することもできます。 
  [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] では、クエリが変数に格納されます。 一連の値を返すようにクエリを設計する場合、クエリ変数そのものが列挙可能な型であることが必要です。 このクエリ変数は、クエリの情報を保存するだけで、なんらかのアクションを実行したり、データを返したりすることはありません。 クエリを作成した後、データを取得するには、そのクエリを実行する必要があります。  
  
 一連の値を返すクエリでは、クエリ変数そのものはクエリ結果を保持しません。クエリ変数には、クエリのコマンドが格納されるだけです。 クエリ変数が `foreach` ループまたは `For Each` ループで反復処理されるまで、クエリは実行されません。 これは呼び出されます*遅延実行*; は、クエリが実行が作成された、クエリは、しばらく時間が発生します。 これは、任意のタイミングでクエリを実行できるということを意味します。 これは、たとえば他のアプリケーションによって更新されるデータベースがある場合に便利です。 アプリケーションで、最新情報を取得するクエリを作成し、それを繰り返し実行することにより、更新のたびに最新の情報を取得できます。  
  
 遅延実行によって一連の値を返すクエリとは対照的に、シングルトン値を返すクエリは直ちに実行されます。 シングルトン クエリの例としては、<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Max%2A>、<xref:System.Linq.Enumerable.Average%2A>、<xref:System.Linq.Enumerable.First%2A> があります。 これらのシングルトン クエリは、結果を計算するためにはクエリ結果が必要であるため、直ちに実行されます。 たとえば、クエリ結果の平均を求めるためには、クエリを実行して、平均関数に入力データを与える必要があります。 シングルトン値を生成しないクエリでも、<xref:System.Linq.Enumerable.ToList%2A> メソッドまたは <xref:System.Linq.Enumerable.ToArray%2A> メソッドを使用することによって、即時実行を強制できます。 即時実行を強制するこの手法は、クエリの結果をキャッシュする場合などに使用すると効果的です。
  
## <a name="queries"></a>クエリ  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 2 つの異なる構文を使ってクエリを作成できます。 クエリ式の構文とメソッド ベースのクエリ構文。  
  
### <a name="query-expression-syntax"></a>クエリ式の構文  
 クエリ式は宣言型のクエリ構文です。 開発者は SQL に似た構文形式を C# または Visual Basic で用いてクエリを作成できます。 クエリ式の構文を使用することにより、フィルター、並べ替え、グループ化など、データ ソースに対するきわめて複雑な処理を最小限のコードで実行できます。 詳細については、次を参照してください。 [LINQ クエリ式](../../../csharp/linq/index.md#query-expression-overview)と[基本的なクエリ操作 (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)します。
  
 クエリ式の構文は、C# 3.0 および [!INCLUDE[vb_orcas_long](../../../../includes/vb-orcas-long-md.md)] で新たに導入されたものです。 ただし、[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] の共通言語ランタイム (CLR) は、クエリ式の構文そのものを理解することはできません。 そのため、クエリ式はコンパイル時に、CLR が理解できる形式 (メソッド呼び出し) へと変換されます。 これらのメソッドとして参照されます、*標準クエリ演算子*します。 開発者は、クエリ構文を使う代わりに、メソッド構文を使ってそれらを直接呼び出すこともできます。 詳細については、「[LINQ でのクエリ構文とメソッド構文](~/docs/csharp/programming-guide/concepts/linq/query-syntax-and-method-syntax-in-linq.md)」を参照してください。 標準クエリ演算子の詳細については、次を参照してください。[標準クエリ演算子の概要](../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md)します。  
  
 次の例では、<xref:System.Linq.Enumerable.Select%2A> を使用して `Product` テーブルからすべての行を取得し、製品名を表示しています。  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectsimple1)]
 [!code-vb[DP LINQ to DataSet Examples#SelectSimple1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectsimple1)]  
  
### <a name="method-based-query-syntax"></a>メソッド ベースのクエリ構文  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] クエリを作成するもう 1 つの方法として、メソッド ベースのクエリがあります。 メソッド ベースのクエリ構文は、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] の演算子メソッドを、ラムダ式をパラメーターとして直接順次呼び出すものです。 詳細については、「[ラムダ式](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)」を参照してください。  
  
 次の例では、<xref:System.Linq.Enumerable.Select%2A> を使用して `Product` テーブルからすべての行を取得し、製品名を表示しています。  
  
 [!code-csharp[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#selectanonymoustypes_mq)]
 [!code-vb[DP LINQ to DataSet Examples#SelectAnonymousTypes_MQ](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#selectanonymoustypes_mq)]  
  
## <a name="composing-queries"></a>クエリの作成  
 前述したように、一連の値を返すように設計されたクエリでは、クエリ変数自体にはクエリ コマンドのみが格納されます。 クエリに即時実行を促すメソッドが含まれていなければ、`foreach` ループまたは `For Each` ループでクエリ変数を反復処理するまで、実際にはクエリは実行されません。 遅延実行により、複数のクエリを組み合わせたり、クエリを拡張したりすることが可能となります。 クエリを拡張して新しい操作を追加すると、その変更が最終的な実行時に反映されます。 次の例の最初のクエリでは、すべての製品が返されます。 2 つ目のクエリでは、サイズが "L" のすべての製品を返すように、`Where` を使って 1 つ目のクエリを拡張しています。  
  
 [!code-csharp[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#composing)]
 [!code-vb[DP LINQ to DataSet Examples#Composing](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#composing)]  
  
 クエリを拡張した後は、追加のクエリを作成することはできません。それ以降のすべてのクエリでは、インメモリの [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 演算子が使用されます。 クエリ変数を反復処理するときに、クエリの実行が発生、`foreach`または`For Each`ステートメント、またはのいずれかを呼び出して、[!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)]即時実行を発生させる変換演算子。 即時実行を促す演算子としては、<xref:System.Linq.Enumerable.ToList%2A>、<xref:System.Linq.Enumerable.ToArray%2A>、<xref:System.Linq.Enumerable.ToLookup%2A>、<xref:System.Linq.Enumerable.ToDictionary%2A> などがあります。  
  
 次の例の最初のクエリは、すべての製品を表示価格で並べ替えて返します。 
  <xref:System.Linq.Enumerable.ToArray%2A> メソッドを使用して、クエリの即時実行を強制しています。  
  
 [!code-csharp[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#toarray2)]
 [!code-vb[DP LINQ to DataSet Examples#ToArray2](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#toarray2)]  
  
## <a name="see-also"></a>関連項目

- [プログラミング ガイド](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
- [DataSet のクエリ](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [C# の LINQ の概要](~/docs/csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Visual Basic の LINQ の概要](~/docs/visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
