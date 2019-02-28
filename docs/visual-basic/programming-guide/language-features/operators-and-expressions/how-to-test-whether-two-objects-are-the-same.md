---
title: '方法: 2 つのオブジェクトが同じ (Visual Basic) であるかどうかをテストします。'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: d13671f284863fa7bf56964c2b9b963c25e8ea52
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977449"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>方法: 2 つのオブジェクトが同じ (Visual Basic) であるかどうかをテストします。
オブジェクトを参照する 2 つの変数があれば、いずれかを使用できる、`Is`または`IsNot`演算子、または両方を同じインスタンスを参照しているかどうかを判断します。  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>2 つのオブジェクトが等しいかどうかをテストするには  
  
-   使用して、 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)または[IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)オペランドとして 2 つの変数を使用します。  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 2 つのオブジェクトが同じインスタンスを参照するかどうかに応じて特定のアクションを実行する場合があります。 上記の例では、コントロール`c`フォーム上のアクティブ コントロールに対して`f`します。 作業中のコントロールがないかがある場合はこれ以上にできない場合と同じコントロール インスタンス`c`、`If`ステートメントが失敗し、手順をさらに処理することがなく返します。  
  
 使用するかどうか`Is`または`IsNot`に個人の利便性の問題です。 1 つは、指定された式で他よりも読みやすい可能性があります。  
  
## <a name="see-also"></a>関連項目
- [Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
