---
title: IsFalse 演算子
ms.date: 07/20/2015
f1_keywords:
- vb.isfalse
helpviewer_keywords:
- AndAlso operator [Visual Basic]
- IsFalse operator [Visual Basic]
ms.assetid: 37fc9dbf-e5cc-4570-b93f-7213447974df
ms.openlocfilehash: 51b7bfb2cf5301a39818e6566b408ee0677689f2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349529"
---
# <a name="isfalse-operator-visual-basic"></a>IsFalse 演算子 (Visual Basic)
式が `False` かどうかを判別します。  
  
 コード内で `IsFalse` を明示的に呼び出すことはできませんが、Visual Basic コンパイラはそれを使用して `AndAlso` 句からコードを生成できます。 クラスまたは構造体を定義し、その型の変数を `AndAlso` 句で使用する場合は、そのクラスまたは構造体で `IsFalse` を定義する必要があります。  
  
 コンパイラは、`IsFalse` と `IsTrue` の演算子を "*対応するペア*" と見なします。 つまり、そのいずれかを定義する場合は、もう一方も定義する必要があります。  
  
> [!NOTE]
> `IsFalse` 演算子は "*オーバーロード*" できます。つまり、オペランドがあるクラスまたは構造体の型を持っているときに、そのクラスまたは構造体はその動作を再定義できます。 コードで、そのようなクラスまたは構造体に対してこの演算子が使用される場合は、再定義された動作を必ず理解してください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 次のコード例では、`IsFalse` および `IsTrue` 演算子の定義を含む構造体のアウトラインを定義しています。  
  
 [!code-vb[VbVbalrOperators#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>関連項目

- [IsTrue 演算子](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [方法: 演算子を定義する](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [AndAlso 演算子](../../../visual-basic/language-reference/operators/andalso-operator.md)
