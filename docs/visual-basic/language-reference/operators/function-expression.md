---
title: Function 式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- Function expression [Visual Basic]
- functions [Visual Basic], function expressions
- lambda expressions [Visual Basic], function expression
ms.assetid: e8a47a45-4b8a-4f45-a623-7653625dffbc
ms.openlocfilehash: 4bef609289cdbb192116469bac4fca66ee10fd09
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662518"
---
# <a name="function-expression-visual-basic"></a>Function 式 (Visual Basic)
パラメーターと、関数ラムダ式を定義するコードを宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
Function ( [ parameterlist ] ) expression  
- or -  
Function ( [ parameterlist ] )  
  [ statements ]  
End Function  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`parameterlist`|省略可能です。 このプロシージャのパラメーターを表すローカル変数名の一覧。 かっこは、リストが空の場合にも存在である必要があります。 参照してください[パラメーター リスト](../../../visual-basic/language-reference/statements/parameter-list.md)します。|  
|`expression`|必須。 1 つの式。 式の型は、関数の戻り値の型です。|  
|`statements`|必須。 使用して値を返すステートメントの一覧、`Return`ステートメント。 (を参照してください[Return ステートメント](../../../visual-basic/language-reference/statements/return-statement.md))。返される値の型は、関数の戻り値の型です。|  
  
## <a name="remarks"></a>Remarks  
 A*ラムダ式*を計算し、値を返します名のない関数です。 ラムダ式を使用することができますを引数としてを除く、デリゲート型を使用する任意の場所`RemoveHandler`します。 デリゲート、およびデリゲートとラムダ式の使用に関する詳細については、次を参照してください。 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)と[厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)します。  
  
## <a name="lambda-expression-syntax"></a>ラムダ式の構文  
 ラムダ式の構文では、標準的な関数に似ています。 相違点は次のとおりです。  
  
- ラムダ式の名前ではありません。  
  
- ラムダ式などで、修飾子を含めることはできません`Overloads`または`Overrides`します。  
  
- ラムダ式は使用しないでください、`As`関数の戻り値の型を指定する句。 代わりに、型は、1 行のラムダ式の本体が評価される値または複数行のラムダ式の戻り値から推論されます。 たとえば、1 行のラムダ式の本体が`Where cust.City = "London"`、戻り値の型は`Boolean`します。  
  
- 単一行のラムダ式の本体は、ステートメントではなく、式である必要があります。 本文は、関数、プロシージャの呼び出しが sub プロシージャへの呼び出しではないので構成できます。  
  
- すべてのパラメーターまたはすべてのデータ型を推論する必要があります指定する必要があります。  
  
- (省略可能) と Paramarray パラメーターは使用できません。  
  
- ジェネリック パラメーターを指定することはできません。  
  
## <a name="example"></a>例  
 次の例では、単純なラムダ式を作成する 2 つの方法を示します。 最初の使用、`Dim`関数の名前を指定します。 関数を呼び出すには、パラメーターの値で送信します。  
  
 [!code-vb[VbVbalrLambdas#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#1)]  
  
 [!code-vb[VbVbalrLambdas#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#2)]  
  
## <a name="example"></a>例  
 またはを宣言し、同時に、関数を実行します。  
  
 [!code-vb[VbVbalrLambdas#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#3)]  
  
## <a name="example"></a>例  
 引数をインクリメントし、値を返すラムダ式の例を次に示します。 この例では、単一行および複数行のラムダ式の両方の構文、関数を示します。 例については、次を参照してください。[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)します。  
  
 [!code-vb[VbVbalrLambdas#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#14)]  
  
## <a name="example"></a>例  
 ラムダ式では、多くのクエリ演算子の基本となる[!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]、メソッド ベースのクエリで明示的に使用できます。 次の例は、一般的な[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)]メソッドの形式に、クエリの変換後にクエリします。  
  
```vb  
Dim londonCusts = From cust In db.Customers  
                       Where cust.City = "London"  
                       Select cust  
  
' This query is compiled to the following code:  
Dim londonCusts = db.Customers.  
                  Where(Function(cust) cust.City = "London").  
                  Select(Function(cust) cust)  
```  
  
 クエリ メソッドの詳細については、次を参照してください。[クエリ](../../../visual-basic/language-reference/queries/index.md)します。 標準クエリ演算子の詳細については、次を参照してください。[標準クエリ演算子の概要](../../programming-guide/concepts/linq/standard-query-operators-overview.md)します。  
  
## <a name="see-also"></a>関連項目

- [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
- [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
- [値の比較](../../../visual-basic/programming-guide/language-features/operators-and-expressions/value-comparisons.md)
- [ブール式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)
- [If 演算子](../../../visual-basic/language-reference/operators/if-operator.md)
- [厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
