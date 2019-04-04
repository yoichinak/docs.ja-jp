---
title: '方法: 演算子 (Visual Basic) を定義するクラスを使用して、'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedures [Visual Basic], calling
- examples [Visual Basic], CType
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 7ccce94a-6ca0-47d1-9f3f-13385d34f5d5
ms.openlocfilehash: bd512adf2f06ed0fbd3d36ed3175a0928bf1c57c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58829409"
---
# <a name="how-to-use-a-class-that-defines-operators-visual-basic"></a>方法: 演算子 (Visual Basic) を定義するクラスを使用して、
クラスまたは独自の演算子を定義する構造体を使用している場合は、これらの演算子を Visual Basic からアクセスできます。  
  
 クラスまたは構造体で演算子を定義が呼び出されますも*オーバー ロード*演算子。  
  
## <a name="example"></a>例  
 次の例では、SQL 構造<xref:System.Data.SqlTypes.SqlString>、変換演算子を定義する ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) SQL 文字列および Visual Basic の文字列間の双方向でします。 使用`CType(` *SQL 文字列式*、 `String)` SQL 文字列を Visual Basic の文字列に変換して`CType(` *Visual Basic の文字列式*、 <xref:System.Data.SqlTypes.SqlString> `)`に他の方向に変換します。  
  
 [!code-vb[VbVbcnProcedures#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#30)]  
  
 [!code-vb[VbVbcnProcedures#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#31)]  
  
 <xref:System.Data.SqlTypes.SqlString>構造体には、変換演算子が定義されています ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)) から`String`に<xref:System.Data.SqlTypes.SqlString>とから<xref:System.Data.SqlTypes.SqlString>に`String`します。 代入するステートメント`title`に`jobTitle`の最初の演算子を使用し、<xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>関数呼び出し、2 つ目の使用します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 必ず、クラスまたは構造体を使用しているが、使用する演算子を定義します。 クラスまたは構造体の定義がすべての演算子はオーバー ロード可能なことを前提としてはいません。 利用可能な演算子の一覧は、[Operator Statement](../../../../visual-basic/language-reference/statements/operator-statement.md)を参照してください。  
  
 含める、適切な`Imports`ソース ファイルの先頭にある SQL 文字列の文 (ここで<xref:System.Data.SqlTypes>)。  
  
 プロジェクトは、System.Data および System.XML への参照が必要です。  
  
## <a name="see-also"></a>関連項目

- [演算子プロシージャ](./operator-procedures.md)
- [方法: 演算子を定義します。](./how-to-define-an-operator.md)
- [方法: 変換演算子を定義します。](./how-to-define-a-conversion-operator.md)
- [方法: 演算子プロシージャを呼び出す](./how-to-call-an-operator-procedure.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [方法: 構造体を宣言する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
