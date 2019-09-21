---
title: Is 演算子 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: a5481a9bce01e84ce4f078335c8cd15a747a3c51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917217"
---
# <a name="is-operator-visual-basic"></a>Is 演算子 (Visual Basic)
2つのオブジェクト参照変数を比較します。  
  
## <a name="syntax"></a>構文  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 任意`Boolean`の値。  
  
 `object1`  
 必須。 任意`Object`の名前。  
  
 `object2`  
 必須。 任意`Object`の名前。  
  
## <a name="remarks"></a>Remarks  
 演算子`Is`は、2つのオブジェクト参照が同じオブジェクトを参照するかどうかを判断します。 ただし、値の比較は実行されません。 と`object1` `True`の両方`False`がまったく同じオブジェクトインスタンスを参照する`result`場合、はです。それ以外`result`の場合、はになります。 `object2`  
  
 `Is``TypeOf` キーワード`TypeOf`と共に使用することもできます...`Is`式。オブジェクト変数がデータ型と互換性があるかどうかをテストします。  
  
> [!NOTE]
> `Is`キーワードは[Select...Case ステートメント](../../../visual-basic/language-reference/statements/select-case-statement.md)でも使用されます。  
  
## <a name="example"></a>例  
 次の例では`Is` 、演算子を使用して、オブジェクト参照のペアを比較しています。 結果は、2つの`Boolean`オブジェクトが同一かどうかを表す値に割り当てられます。  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 前の例で示したように、 `Is`演算子を使用すると、事前バインディングオブジェクトと遅延バインディングオブジェクトの両方をテストできます。  
  
## <a name="see-also"></a>関連項目

- [TypeOf 演算子](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [IsNot 演算子](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Visual Basic の比較演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
