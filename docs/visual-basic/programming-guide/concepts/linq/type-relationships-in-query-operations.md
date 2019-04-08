---
title: クエリ操作での型の関係 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- variable relationships [LINQ in Visual Basic]
- type information inferred [LINQ in Visual Basic]
- type relationships [LINQ in Visual Basic]
- queries [LINQ in Visual Basic], type relationships
- data sources [LINQ in Visual Basic], type relationships
- LINQ [Visual Basic], type relationships
- inferring type information [LINQ in Visual Basic]
- relationships [LINQ in Visual Basic]
ms.assetid: b5ff4da5-f3fd-4a8e-aaac-1cbf52fa16f6
ms.openlocfilehash: fd2bcfad0ae24288887500ae6286e6ac73fddac5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822337"
---
# <a name="type-relationships-in-query-operations-visual-basic"></a>クエリ操作での型の関係 (Visual Basic)
使用される変数[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]クエリ操作は、厳密に型指定し、相互に互換性がある必要があります。 厳密な型指定すると、データ ソース、クエリ自体、およびクエリの実行が使用されます。 次の図は、記述に使用される用語の識別、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ。 詳細については、クエリの部分は、[基本的なクエリ操作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)を参照してください。  
  
 ![強調表示されている要素を持つ擬似コード クエリを示すスクリーン ショット。](./media/type-relationships-in-query-operations/linq-query-description-terms.png)  
  
 クエリで範囲変数の型は、データ ソース内の要素の型と互換性のあるである必要があります。 クエリ変数の型で定義されたシーケンスの要素と互換性のある必要があります、`Select`句。 最後に、シーケンスの要素の型も必要がありますで使用されているループ コントロール変数の型と互換性のある、`For Each`クエリを実行するステートメント。 この厳密な型指定すると、コンパイル時に型のエラーの識別が容易になります。  
  
 Visual Basic により、厳密な型指定便利とも呼ばれるローカル型推論を実装することによって*暗黙の型指定*します。 機能は、前の例で使用して、全体で使用されることが表示されます、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]サンプルとドキュメントです。 Visual Basic でローカル型推論は使用するだけで実現を`Dim`ステートメントを除く、`As`句。 次の例では、`city`を文字列として厳密に型指定します。  
  
 [!code-vb[VbLINQTypeRels#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#1)]  
  
> [!NOTE]
>  ローカル型推論機能の場合にのみ`Option Infer`に設定されている`On`します。 詳細については、[Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)を参照してください。  
  
 ただし、クエリでローカル型推論を使用する場合でも、同じ型の関係は、データ ソース内の変数、クエリ変数、およびクエリの実行ループの間に存在します。 作成するときにこれらの型の関係の基本を理解すると便利ですが[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]クエリ、またはサンプルとドキュメントのコード例を使用します。  
  
 データ ソースから返される型に一致しない範囲変数の明示的な型を指定する必要があります。 範囲変数の型を使用して指定することができます、`As`句。 その結果、エラーに変換すると、[縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)と`Option Strict`に設定されている`On`します。 そのため、データ ソースから取得した値に変換を実行することをお勧めします。 明示的な範囲変数の型を使用して、データ ソースから値を変換できます、<xref:System.Linq.Enumerable.Cast%2A>メソッド。 選択した値をキャストすることも、`Select`範囲変数の型とは異なる、明示的な型の句。 これらのポイントは、次のコードに示します。  
  
 [!code-vb[VbLINQTypeRels#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#4)]  
  
## <a name="queries-that-return-entire-elements-of-the-source-data"></a>ソース データの全体の要素を返すクエリ  
 次の例は、[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]操作、ソース データから選択された要素のシーケンスを返すクエリを実行します。 ソース`names`文字列の配列が含まれていて、クエリの出力が文字 M で始まる文字列を含むシーケンス。  
  
 [!code-vb[VbLINQTypeRels#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#2)]  
  
 これは次のコードと同じですより短く、簡単に記述されます。 クエリでローカル型推論の依存は、Visual Basic での優先スタイルです。  
  
 [!code-vb[VbLINQTypeRels#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbLINQTypeRels/VB/Class1.vb#3)]  
  
 次のリレーションシップは、種類が暗黙的または明示的に決定されるかどうか、前のコード例の両方に存在します。  
  
1.  データ ソース内の要素の型`names`、範囲変数の型は、`name`クエリにします。  
  
2.  選択されているオブジェクトの型`name`、クエリ変数の種類を決定します`mNames`します。 ここで`name`は文字列、ので、クエリ変数は Visual Basic での IEnumerable (Of String)。  
  
3.  定義されているクエリ`mNames`で実行される、`For Each`ループします。 クエリの実行の結果に対して、ループが反復処理します。 `mNames`が実行されるときに、ループの反復変数、文字列のシーケンスを返す`nm`も文字列です。  
  
## <a name="queries-that-return-one-field-from-selected-elements"></a>選択した要素から 1 つのフィールドを返すクエリ  
 次の例は、[!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]クエリをデータ ソースから選択された各要素の一部だけを含むシーケンスを返す操作。 クエリのコレクションを受け取り`Customer`としてそのデータ ソース オブジェクトし、プロジェクトのみ、`Name`結果のプロパティ。 顧客名は文字列であるため、クエリは、出力として文字列のシーケンスを生成します。  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim custNames = From cust In customers   
                Where cust.City = "London"   
                Select cust.Name  
  
For Each custName In custNames  
    Console.WriteLine(custName)  
Next  
```  
  
 変数間のリレーションシップは、簡単な例のようです。  
  
1.  データ ソース内の要素の型`customers`、範囲変数の型は、`cust`クエリにします。 型である、この例では`Customer`します。  
  
2.  `Select`ステートメントから返される、`Name`の各プロパティ`Customer`オブジェクト全体ではなくオブジェクト。 `Name`文字列で、クエリ変数は、 `custNames`、もう一度されません IEnumerable (Of String) の`Customer`します。  
  
3.  `custNames` 、文字列のシーケンスを表し、`For Each`ループの反復変数、`custName`文字列である必要があります。  
  
 ローカル型推論、せず、前の例と詳細については、次の例のように記述する煩雑になります。  
  
```vb  
' Method GetTable returns a table of Customer objects.  
 Dim customers As Table(Of Customer) = db.GetTable(Of Customer)()  
 Dim custNames As IEnumerable(Of String) =  
     From cust As Customer In customers   
     Where cust.City = "London"   
     Select cust.Name  
  
 For Each custName As String In custNames  
     Console.WriteLine(custName)  
 Next  
```  
  
## <a name="queries-that-require-anonymous-types"></a>匿名型を必要とするクエリ  
 次の例より複雑な状況を示しています。 前の例では、すべての変数の型を明示的に指定するは便利でした。 この例では、ことはできません。 全体を選択する代わりに`Customer`データ ソース、または、各要素から 1 つのフィールドからの要素、`Select`句をこのクエリでは、元の 2 つのプロパティを返します`Customer`オブジェクト:`Name`と`City`します。 応答、`Select`句では、コンパイラはこれら 2 つのプロパティを含む匿名型を定義します。 実行結果`nameCityQuery`で、`For Each`ループは新しい匿名型のインスタンスのコレクションです。 種類を指定することはできません、匿名型に使用できる名前があるないため`nameCityQuery`または`custInfo`明示的にします。 匿名の型のない型の名前があるの代わりに使用する`String`で`IEnumerable(Of String)`します。 詳細については、「[匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)」を参照してください。  
  
```vb  
' Method GetTable returns a table of Customer objects.  
Dim customers = db.GetTable(Of Customer)()  
Dim nameCityQuery = From cust In customers   
                    Where cust.City = "London"   
                    Select cust.Name, cust.City  
  
For Each custInfo In nameCityQuery  
    Console.WriteLine(custInfo.Name)  
Next  
```  
  
 前の例では、すべての変数の型を指定することはありませんが、リレーションシップが同じになります。  
  
1.  データ ソース内の要素の型は、クエリで範囲変数の型ではもう一度です。 この例で`cust`のインスタンスである`Customer`します。  
  
2.  `Select`ステートメントは、クエリ変数、匿名型を生成`nameCityQuery`、匿名型として暗黙的に型指定する必要があります。 匿名型では、使用できる名前を持たず、したがって、明示的に指定することはできません。  
  
3.  反復変数の型、`For Each`ループは、手順 2. で作成された匿名型。 型に使用できる名前があるないために、ループの反復変数の型は暗黙的に決定する必要があります。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic の LINQ の概要](../../../../visual-basic/programming-guide/concepts/linq/getting-started-with-linq.md)
- [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [ローカル型の推論](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)
- [クエリ](../../../../visual-basic/language-reference/queries/index.md)
