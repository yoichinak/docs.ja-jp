---
title: '方法: 2 つのオブジェクトが同じです (Visual Basic) であるかどうかを確認します。'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: f1fdc5f69b8552ee10131c7408673457fffe16ae
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976851"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>方法: 2 つのオブジェクトが同じです (Visual Basic) であるかどうかを確認します。
Visual basic で 2 つの変数参照は同一と見なされます、ポインターが同じ場合、つまり、両方の変数がメモリ内と同じクラスのインスタンスを指している場合。 たとえば、Windows フォーム アプリケーションでたい判断する比較を行うことかどうか、現在のインスタンス (`Me`) など、特定のインスタンスと同じ`Form2`します。  
  
 Visual Basic では、ポインターを比較する 2 つの演算子を提供します。 [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)返します`True`オブジェクトが同じですが場合、 [IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)返します`True`それ以外の場合。  
  
## <a name="determining-if-two-objects-are-identical"></a>2 つのオブジェクトが同じかどうかを決定します。  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>2 つのオブジェクトが同じかどうかを判断するには  
  
1.  セットアップ、 `Boolean` 2 つのオブジェクトをテストする式。  
  
2.  テスト式で使用して、`Is`演算子のオペランドとして 2 つのオブジェクト。  
  
     `Is` 返します`True`場合は、オブジェクトが、同じクラスのインスタンスをポイントします。  
  
## <a name="determining-if-two-objects-are-not-identical"></a>2 つのオブジェクトが同一でないかどうかを決定します。  
 2 つのオブジェクトが異なると、結合にくいことができる場合、操作を実行する場合があります`Not`と`Is`、たとえば`If Not obj1 Is obj2`します。 このような場合に使用することができます、`IsNot`演算子。  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>2 つのオブジェクトが同一でないかどうかを判断するには  
  
1.  セットアップ、 `Boolean` 2 つのオブジェクトをテストする式。  
  
2.  テスト式で使用して、`IsNot`演算子のオペランドとして 2 つのオブジェクト。  
  
     `IsNot` 返します`True`場合は、オブジェクトが同じクラスのインスタンスを指していません。  
  
## <a name="example"></a>例  
 次の例では、テストのペア`Object`変数を同じクラスのインスタンスを指しているかを参照してください。  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 前の例では、次の出力が表示されます。  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>関連項目
- [Object 型](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [オブジェクト変数](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [オブジェクト変数の値](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Is 演算子](../../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 演算子](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [方法: 2 つのオブジェクトが関連するかどうかを判断します。](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Me、My、MyBase、および MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
