---
title: '方法: 2 つのオブジェクトが等しいかどうかをテストする'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], reference
- Is operator [Visual Basic], comparing objects
- reference variables [Visual Basic]
- variables [Visual Basic], referring to same object
- objects [Visual Basic], variables referring to same
- Visual Basic code, operators
ms.assetid: f760e828-8704-4256-bc2d-c22a4c93b524
ms.openlocfilehash: 22e8e1e688d9e3bc3804899103ee78814aac235b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343618"
---
# <a name="how-to-test-whether-two-objects-are-the-same-visual-basic"></a>方法: 2 つのオブジェクトが等しいかどうかをテストする (Visual Basic)
オブジェクトを参照する 2 つの変数がある場合、`Is` または `IsNot` 演算子のいずれか、または両方を使用して、それらが同じインスタンスを参照するかどうかを判断できます。  
  
### <a name="to-test-whether-two-objects-are-the-same"></a>2 つのオブジェクトが等しいかどうかをテストするには  
  
- 2 つの変数をオペランドとして、[Is Operator](../../../../visual-basic/language-reference/operators/is-operator.md) または [IsNot Operator](../../../../visual-basic/language-reference/operators/isnot-operator.md) を使用します。  
  
     [!code-vb[VbVbalrOperators#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#69)]  
  
 2 つのオブジェクトが同じインスタンスを参照しているかどうかによって、特定のアクションを実行する場合があります。 前の例では、コントロール `c` をフォーム `f` のアクティブなコントロールと比較しています。 アクティブなコントロールがない場合、またはアクティブなコントロールはあるが `c` と同じコントロール インスタンスではない場合、`If` ステートメントは失敗し、プロシージャでは以降の処理を行わずに戻ります。  
  
 `Is` と `IsNot` のどちらを使用するかは、お客様の利便性の問題です。 指定された式について、読みやすいと思われる方とそうではない方がいるでしょう。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic における比較演算子](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
