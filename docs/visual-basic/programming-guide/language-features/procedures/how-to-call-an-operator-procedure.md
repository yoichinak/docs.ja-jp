---
title: '方法: 演算子プロシージャ (Visual Basic) を呼び出す'
ms.date: 07/20/2015
helpviewer_keywords:
- operator procedures [Visual Basic], calling
- procedures [Visual Basic], operator
- procedure calls [Visual Basic], operator overloading
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- overloaded operators [Visual Basic], calling
- operator overloading
ms.assetid: 0dce42cc-f0b0-4c14-9f62-018b21f33497
ms.openlocfilehash: d68781aa12ab7c1c717031ca252c5f3120649edc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59335486"
---
# <a name="how-to-call-an-operator-procedure-visual-basic"></a>方法: 演算子プロシージャ (Visual Basic) を呼び出す
演算子プロシージャを呼び出すには、式で演算子記号を使用します。 場合は、変換演算子を呼び出す、 [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)に値を別の 1 つのデータ型に変換します。  
  
 演算子プロシージャを明示的に呼び出すことはありません。 同様に、演算子を使用する、または`CType`代入ステートメントまたは式、演算子に通常使用する同じ方法での関数。 Visual Basic では、演算子プロシージャ呼び出しを行います。  
  
 クラスまたは構造体で演算子を定義が呼び出されますも*オーバー ロード*演算子。  
  
### <a name="to-call-an-operator-procedure"></a>演算子プロシージャを呼び出す  
  
1. 通常の方法で、式の中で演算子記号を使用します。  
  
2. オペランドのデータ型が演算子の場合、正しい順序で適切なであることを確認します。  
  
3. 演算子は、期待どおりに、式の値に作用します。  
  
### <a name="to-call-a-conversion-operator-procedure"></a>変換演算子プロシージャを呼び出す  
  
1. 使用`CType`式の内部。  
  
2. オペランドのデータ型は、変換して、正しい順序で適切なことを確認します。  
  
3. `CType` 変換演算子プロシージャを呼び出し、変換後の値を返します。  
  
## <a name="example"></a>例  
 次の例では、2 つ作成されます<xref:System.TimeSpan>構造体を一緒に追加し、3 つ目の結果を格納<xref:System.TimeSpan>構造体。 <xref:System.TimeSpan>構造がいくつかの標準的な演算子をオーバー ロードする演算子プロシージャを定義します。  
  
 [!code-vb[VbVbcnProcedures#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#29)]  
  
 <xref:System.TimeSpan> 、標準のオーバー ロード`+`演算子を前の例では演算子プロシージャの値を計算するとき`combinedSpan`します。  
  
 メッセージ交換演算子プロシージャの呼び出しの例は、次を参照してください。[方法。演算子を定義するクラスを使用して](./how-to-use-a-class-that-defines-operators.md)します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 必ず、クラスまたは構造体を使用しているが、使用する演算子を定義します。  
  
## <a name="see-also"></a>関連項目

- [演算子プロシージャ](./operator-procedures.md)
- [方法: 演算子を定義します。](./how-to-define-an-operator.md)
- [方法: 変換演算子を定義します。](./how-to-define-a-conversion-operator.md)
- [Operator ステートメント](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Widening](../../../../visual-basic/language-reference/modifiers/widening.md)
- [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md)
- [Structure ステートメント](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [方法: 構造体を宣言する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [暗黙の型変換と明示的な型変換](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [拡大変換と縮小変換](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
