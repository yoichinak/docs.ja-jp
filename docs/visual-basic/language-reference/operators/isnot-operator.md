---
title: IsNot 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: 0a83b48e5e415bd6ca0c777cef6d34f7127691b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966935"
---
# <a name="isnot-operator-visual-basic"></a>IsNot 演算子 (Visual Basic)
2つのオブジェクト参照変数を比較します。  
  
## <a name="syntax"></a>構文  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 `Boolean` 値。  
  
 `object1`  
 必須。 任意`Object`の変数または式。  
  
 `object2`  
 必須。 任意`Object`の変数または式。  
  
## <a name="remarks"></a>Remarks  
 演算子`IsNot`は、2つのオブジェクト参照が異なるオブジェクトを参照するかどうかを判断します。 ただし、値の比較は実行されません。 と`object1` `False`の両方`True`がまったく同じオブジェクトインスタンスを参照する`result`場合、はです。それ以外`result`の場合、はになります。 `object2`  
  
 `IsNot`は、 `Is`演算子の反対側です。 の`IsNot`利点は、とを使用`Not`すると`Is`、読みにくくなることがある、厄介な構文を避けることができることです。  
  
 `Is` および`IsNot`演算子を使用すると、事前バインディングオブジェクトと遅延バインディングオブジェクトの両方をテストできます。  
  
> [!NOTE]
> 演算子を使用して、 `TypeOf`演算子から返された式を比較することはできません。 `IsNot` 代わりに、演算子`Not`と`Is`演算子を使用する必要があります。  
  
## <a name="example"></a>例  
 次のコード例では、 `Is`演算子`IsNot`と演算子の両方を使用して、同じ比較を実行します。  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a>関連項目

- [Is 演算子](../../../visual-basic/language-reference/operators/is-operator.md)
- [TypeOf 演算子](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [2 つのオブジェクトが等しいかどうかをテストする方法](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
