---
title: 部分式 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [Visual Basic], sub expression
- Sub Expression [Visual Basic]
- subroutines [Visual Basic], sub expressions
ms.assetid: 36b6bfd1-6539-4d8f-a5eb-6541a745ffde
ms.openlocfilehash: 5b26a091dc8eb7415702c3c2853a569324def7d5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824612"
---
# <a name="sub-expression-visual-basic"></a>部分式 (Visual Basic)
パラメーターとサブルーチンのラムダ式を定義するコードを宣言します。  
  
## <a name="syntax"></a>構文  
  
```  
Sub ( [ parameterlist ] ) statement  
- or -  
Sub ( [ parameterlist ] )  
  [ statements ]  
End Sub  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`parameterlist`|省略可能です。 プロシージャのパラメーターを表すローカル変数名の一覧。 かっこは、リストが空の場合にも存在である必要があります。 詳細については、「 [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md)」を参照してください。|  
|`statement`|必須。 1 つのステートメント。|  
|`statements`|必須。 ステートメントの一覧。|  
  
## <a name="remarks"></a>Remarks  
 A*ラムダ式*名前がないサブルーチンは、1 つまたは複数のステートメントを実行します。 ラムダ式を任意の場所に使用できるデリゲート型への引数としてを除き使用できます`RemoveHandler`します。 デリゲート、およびデリゲートとラムダ式の使用に関する詳細については、次を参照してください。 [Delegate ステートメント](../../../visual-basic/language-reference/statements/delegate-statement.md)と[厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)します。  
  
## <a name="lambda-expression-syntax"></a>ラムダ式の構文  
 標準的なサブルーチンのラムダ式の構文に似ています。 相違点は次のとおりです。  
  
-   ラムダ式の名前ではありません。  
  
-   ラムダ式はなどの修飾子を含めることはできません`Overloads`または`Overrides`します。  
  
-   単一行のラムダ式の本体は、ステートメント、式ではないである必要があります。 本文は、sub プロシージャへの呼び出しが、function プロシージャへの呼び出しではないので構成できます。  
  
-   ラムダ式でデータ型またはすべてのパラメーターを推論する必要がありますかすべてのパラメーターが指定する必要があります。  
  
-   省略可能なと`ParamArray`パラメーターはラムダ式で許可されていません。  
  
-   ジェネリック パラメーターはラムダ式で許可されていません。  
  
## <a name="example"></a>例  
 値をコンソールに出力するラムダ式の例を次に示します。 この例では、サブルーチンの両方の単一行および複数行のラムダ式構文を示します。 例については、次を参照してください。[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)します。  
  
 [!code-vb[VbVbalrLambdas#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrLambdas/VB/Class1.vb#15)]  
  
## <a name="see-also"></a>関連項目

- [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)
- [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [ステートメント](../../../visual-basic/programming-guide/language-features/statements.md)
- [厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
