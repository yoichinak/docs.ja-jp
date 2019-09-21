---
title: IsFalse 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 49b8493575685a220808df1522ce16835b3ce0ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917156"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse 演算子 (Visual Basic)
式がで`False`あるかどうかを判断します。  
  
 コード内で`IsFalse`を明示的に呼び出すことはできませんが、Visual Basic コンパイラはそれ`AndAlso`を使用して句からコードを生成できます。 クラスまたは構造体を定義し、その型の変数を`AndAlso`句で使用する場合は、そのクラスまたは構造体でを定義`IsFalse`する必要があります。  
  
 コンパイラは、演算子`IsFalse`と`IsTrue`演算子を*一致するペア*と見なします。 これは、そのいずれかを定義する場合は、もう一方も定義する必要があることを意味します。  
  
> [!NOTE]
> 演算子はオーバーロードできます。つまり、クラスまたは構造体がそのクラスまたは構造体の型を持つ場合に、クラスまたは構造体がその動作を再定義できます。 `IsFalse` コードでこのようなクラスまたは構造体に対してこの演算子を使用する場合は、再定義された動作を理解していることを確認してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、演算子`IsFalse`と`IsTrue`演算子の定義を含む構造体のアウトラインを定義します。  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>関連項目

- [IsTrue 演算子](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [演算子を定義する方法](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso 演算子](../../../visual-basic/language-reference/operators/andalso-operator.md)
