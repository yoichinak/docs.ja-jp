---
title: パラメーター配列 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- parameter arrays [Visual Basic], about parameter arrays
- ParamArray keyword [Visual Basic], parameter arrays
- Visual Basic code, procedures
- parameters [Visual Basic], parameter arrays
- arguments [Visual Basic], parameter arrays
- procedures [Visual Basic], indefinite number of argument values
- arrays [Visual Basic], parameter arrays
ms.assetid: c43edfae-9114-4096-9ebc-8c5c957a1067
ms.openlocfilehash: 8ea4c77056701b8f61c1ed5a53cf20d98ae913bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58834165"
---
# <a name="parameter-arrays-visual-basic"></a>パラメーター配列 (Visual Basic)
通常、プロシージャ宣言の指定よりも多くの引数を持つプロシージャを呼び出すことはできません。 宣言することができます、不特定多数の引数を必要がある場合、*パラメーター配列*、プロシージャ パラメーターの値の配列をそのまま使用することができます。 プロシージャを定義するときに、パラメーター配列内の要素の数を把握する必要はありません。 配列のサイズは、各プロシージャの呼び出しによって個別に決まります。  
  
## <a name="declaring-a-paramarray"></a>ParamArray を宣言します。  
 使用する、 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーター リスト内のパラメーター配列を示すキーワードです。 次の規則が適用されます。  
  
-   プロシージャが 1 つだけのパラメーター配列を定義およびプロシージャの定義の最後のパラメーターがあります。  
  
-   パラメーター配列は、値を渡しする必要があります。 明示的に指定することをお勧め、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)プロシージャ定義内のキーワード。  
  
-   パラメーター配列は、自動的に省略可能です。 既定値は、パラメーター配列の要素の型の空の 1 次元配列です。  
  
-   前に、パラメーター配列のすべてのパラメーターは必須である必要があります。 パラメーター配列は、唯一のパラメーターである必要があります。  
  
## <a name="calling-a-paramarray"></a>ParamArray を呼び出す  
 パラメーター配列を定義するプロシージャを呼び出すときに、次の方法のいずれかで、引数を指定できます。  
  
-   Nothing-これは省略できます、 [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)引数。 この場合、空の配列は、プロシージャに渡されます。 渡すことも、 [Nothing](../../../../visual-basic/language-reference/nothing.md)キーワードは、同じ効果を持つ。  
  
-   任意の数の引数、コンマ区切りの一覧。 各引数のデータ型に暗黙的に変換できる必要があります、`ParamArray`要素の型。  
  
-   パラメーター配列の要素の型と同じ要素型の配列。  
  
 すべてのケースで、プロシージャ内のコード、パラメーターは配列として扱いますと同じデータ型の要素を持つ 1 次元配列、`ParamArray`データ型。  
  
> [!IMPORTANT]
>  無限に増大することができる配列を処理するたびに、アプリケーションの内部の容量を超過してしまう可能性があります。 パラメーター配列を受け取る場合は、呼び出し元のコードが渡された配列のサイズをテストする必要があります。 アプリケーションが大きすぎる場合は、適切な手順を実行します。 詳細については、次を参照してください。[配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)します。  
  
## <a name="example"></a>例  
 次の例を定義し、関数を呼び出す`calcSum`します。 `ParamArray`パラメーター修飾子`args`により、関数を可変個の引数を受け入れるようにできます。  
  
 [!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]  
  
 次の例は、パラメーター配列を持つプロシージャを定義し、パラメーター配列に渡されるすべての配列要素の値を出力します。  
  
 [!code-vb[VbVbcnProcedures#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#48)]  
  
 [!code-vb[VbVbcnProcedures#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#49)]  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [プロシージャ](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)
- [省略可能なパラメーター](./optional-parameters.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
- [配列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
- [Optional](../../../../visual-basic/language-reference/modifiers/optional.md)
