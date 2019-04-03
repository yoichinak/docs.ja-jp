---
title: LINQ をサポートする Visual Basic の機能
ms.date: 07/20/2015
helpviewer_keywords:
- Visual Basic, LINQ features
- LINQ [Visual Basic], features supporting LINQ
ms.assetid: c821bb50-b6f6-4cf9-8aba-2717e465bd3a
ms.openlocfilehash: 155d5c36483accc12d066a5530fea20a563e1498
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814498"
---
# <a name="visual-basic-features-that-support-linq"></a>LINQ をサポートする Visual Basic の機能
名前[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]クエリ構文のサポートを言語で直接その他の言語を構築します、Visual Basic でのテクノロジを参照します。 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]、外部データ ソースに対してクエリを新しい言語を習得する必要はありません。 Visual Basic を使用してリレーショナル データベース、XML ストア、またはオブジェクト内のデータのクエリを行うことができます。 この統合言語クエリ機能の有効に構文エラーとタイプ セーフのコンパイル時にチェックします。 この統合は、Visual Basic での高度でさまざまなクエリを記述するために必要なほとんどを既に把握しているにも確認します。  
  
 次のセクションでは、入門ドキュメント、コード例については、およびサンプル アプリケーションの読み取りを開始するための十分な詳細で LINQ をサポートする言語構造について説明します。 統合言語クエリを有効にする言語機能がどのように一緒に付属のより詳細な説明を検索するリンクをクリックすることもできます。 開始点としては[チュートリアル。Visual Basic でクエリを記述](../../../../visual-basic/programming-guide/concepts/linq/walkthrough-writing-queries.md)します。  
  
## <a name="query-expressions"></a>クエリ式  
 Visual Basic でのクエリ式は、SQL や XQuery に似た宣言型の構文で表現できます。 コンパイル時に、クエリの構文は、標準クエリ演算子の拡張メソッドの LINQ プロバイダーの実装に対するメソッド呼び出しに変換されます。 標準クエリ演算子がスコープ内で適切な名前空間を指定することで、アプリケーション制御、`Imports`ステートメント。 Visual Basic のクエリ式の構文のようになります。  
  
 [!code-vb[VbLINQVbFeatures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#1)]  
  
 詳細については、次を参照してください。 [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)します。  
  
## <a name="implicitly-typed-variables"></a>暗黙的に型指定された変数  
 明示的に宣言し、変数を初期化するときに、型を指定する、代わりに、型をコンパイラを有効にできます。 呼ばれる*ローカル型推論*します。  
  
 型を明示的に指定した変数と同様、推論される型を持つ変数を厳密に入力します。 ローカル型推論は、メソッド本文内のローカル変数を定義する場合にのみ機能します。 詳細については、次を参照してください。 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)と[ローカル型推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)します。  
  
 次の例では、ローカル型推論を示しています。 この例を使用するに設定する必要があります`Option Infer`に`On`します。  
  
 [!code-vb[VbLINQVbFeatures#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#2)]  
  
 ローカル型推論では、このセクションで後で説明して、LINQ クエリのために必要な匿名型を作成することです。  
  
 場合は次の LINQ の例で型の推定が発生する`Option Infer`か`On`または`Off`します。 コンパイル時エラーが発生します`Option Infer`は`Off`と`Option Strict`は`On`します。  
  
 [!code-vb[VbLINQVbFeatures#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#3)]  
  
## <a name="object-initializers"></a>オブジェクト初期化子  
 オブジェクト初期化子は、クエリの結果を保持するために匿名型を作成するときに、クエリ式で使用されます。 クエリの外部で名前付きの型のオブジェクトを初期化するために使用することがことができます。 オブジェクト初期化子を使用すると、コンス トラクターを明示的に呼び出さずに、1 行でオブジェクトを初期化できます。 という名前のクラスがあると仮定`Customer`を持つパブリック`Name`と`Phone`プロパティ、その他のプロパティと共に、オブジェクト初期化子をこの方法で使用できます。  
  
 [!code-vb[VbLINQVbFeatures#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#4)]  
  
 詳細については、次を参照してください。[オブジェクト初期化子。名前付きの匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)します。  
  
## <a name="anonymous-types"></a>匿名型  
 匿名型は、クエリ結果に追加する要素にプロパティのセットを一時的にグループ化する便利な手段を提供します。 これにより、要素の名前付きのデータ型を定義することがなく、任意の順序でのクエリで使用可能なフィールドの任意の組み合わせを選択することができます。  
  
 *匿名型*はコンパイラによって動的に構築します。 型の名前は、コンパイラによって割り当てられ、新しいコンパイルのたびに変わる可能性があります。 そのため、名前を直接使用することはできません。 匿名型は、次のように初期化されます。  
  
 [!code-vb[VbLINQVbFeatures#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#5)]  
  
 詳細については、「[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
## <a name="extension-methods"></a>拡張メソッド  
 拡張メソッドを使用すると、データ型またはインターフェイスの定義の外部にメソッドを追加できます。 この機能では、実際には、実際には、型を変更することがなく既存の型に新しいメソッドを追加することができます。 標準クエリ演算子は、それ自体が提供する拡張メソッドのセットを[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ機能を実装する任意の型<xref:System.Collections.Generic.IEnumerable%601>します。 その他の拡張機能を<xref:System.Collections.Generic.IEnumerable%601>含める<xref:System.Linq.Enumerable.Count%2A>、<xref:System.Linq.Enumerable.Union%2A>と<xref:System.Linq.Enumerable.Intersect%2A>します。  
  
 次の拡張メソッドを print メソッドの追加、<xref:System.String>クラス。  
  
 [!code-vb[VbLINQVbFeatures#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#6)]  
  
 メソッドは通常のインスタンス メソッドのような<xref:System.String>:  
  
 [!code-vb[VbLINQVbFeatures#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#7)]  
  
 詳細については、「[拡張メソッド](../../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)」を参照してください。  
  
## <a name="lambda-expressions"></a>ラムダ式  
 ラムダ式は、計算して 1 つの値を返す名前のない関数です。 名前付きの関数とは異なり、ラムダ式の定義し、同時に実行します。 次の例では、4 が表示されます。  
  
 [!code-vb[VbLINQVbFeatures#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#8)]  
  
 変数名にラムダ式の定義を割り当てるし、名を使用して、関数を呼び出すことができます。 次の例では、4 も表示されます。  
  
 [!code-vb[VbLINQVbFeatures#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#12)]  
  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]ラムダ式の基本となる多くの標準クエリ演算子。 コンパイラなど、基本的なクエリ メソッドで定義されている計算をキャプチャするラムダ式を作成する`Where`、 `Select`、 `Order By`、 `Take While`、およびその他。  
  
 たとえば、次のコードは、受講者の一覧から上級のすべての学生を返すクエリを定義します。  
  
 [!code-vb[VbLINQVbFeatures#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#9)]  
  
 クエリの定義は次の例は、引数を指定する 2 つのラムダ式を使用して次のようなコードにコンパイル`Where`と`Select`します。  
  
 [!code-vb[VbLINQVbFeatures#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#10)]  
  
 使用していずれかのバージョンを実行することができます、`For Each`ループ。  
  
 [!code-vb[VbLINQVbFeatures#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQVbFeatures/VB/Class1.vb#11)]  
  
 詳細については、「[ラムダ式](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [統合言語クエリ (LINQ) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
- [Visual Basic の LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [LINQ と文字列 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-and-strings.md)
- [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
