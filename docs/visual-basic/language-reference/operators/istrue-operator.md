---
title: IsTrue 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.istrue
helpviewer_keywords:
- IsTrue operator [Visual Basic]
- OrElse operator [Visual Basic]
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
ms.openlocfilehash: 1152f4b512a85ae183f8fc8d476b69685e2926ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966920"
---
# <a name="istrue-operator-visual-basic"></a>IsTrue 演算子 (Visual Basic)
式がで`True`あるかどうかを判断します。  
  
 コード内で`IsTrue`を明示的に呼び出すことはできませんが、Visual Basic コンパイラはそれ`OrElse`を使用して句からコードを生成できます。 クラスまたは構造体を定義し、その型の変数を`OrElse`句で使用する場合は、そのクラスまたは構造体でを定義`IsTrue`する必要があります。  
  
 コンパイラは、演算子`IsTrue`と`IsFalse`演算子を*一致するペア*と見なします。 これは、そのいずれかを定義する場合は、もう一方も定義する必要があることを意味します。  
  
## <a name="compiler-use-of-istrue"></a>IsTrue のコンパイラの使用  
 クラスまたは構造体を定義した場合は`For` `Else If`、 `If`、、、または`While`の各ステートメント`When`で、その型の変数を使用できます。 これを行う場合、コンパイラは、条件をテストできるように型を`Boolean`値に変換する演算子を必要とします。 適切な演算子を次の順序で検索します。  
  
1. クラスまたは構造体からへ`Boolean`の拡大変換演算子。  
  
2. クラスまたは構造体からへ`Boolean?`の拡大変換演算子。  
  
3. クラスまたは構造体の演算子。`IsTrue`  
  
4. からへの`Boolean`変換`Boolean?`を行わないへの縮小変換。 `Boolean?`  
  
5. クラスまたは構造体からへ`Boolean`の縮小変換演算子。  
  
 または`Boolean`演算子への変換を定義していない場合、コンパイラはエラーを通知します。 `IsTrue`  
  
> [!NOTE]
> 演算子はオーバーロードできます。つまり、クラスまたは構造体がそのクラスまたは構造体の型を持つ場合に、クラスまたは構造体がその動作を再定義できます。 `IsTrue` コードでこのようなクラスまたは構造体に対してこの演算子を使用する場合は、再定義された動作を理解していることを確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、演算子`IsFalse`と`IsTrue`演算子の定義を含む構造体のアウトラインを定義します。  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>関連項目

- [IsFalse 演算子](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [方法: 演算子を定義する](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [OrElse 演算子](../../../visual-basic/language-reference/operators/orelse-operator.md)
