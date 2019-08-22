---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: 1fa4c1fa0a2def02dd56fa3728a8df4b5ff16b7f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666859"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
引数が[値によって](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)渡されることを指定します。これにより、呼び出されたプロシージャまたはプロパティが、呼び出し元のコードの引数の基になる変数の値を変更できなくなります。 修飾子が指定されていない場合、ByVal が既定値になります。

> [!NOTE]
> これは既定であるため、メソッドシグネチャで`ByVal`キーワードを明示的に指定する必要はありません。 ノイズの多いコードが生成される傾向があり、多くの`ByRef`場合、既定以外のキーワードが見落とされてしまいます。

## <a name="remarks"></a>Remarks
 `ByVal` 修飾子は、次のコンテキストで使用できます。

 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)

 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a>例
 次の例では、参照型`ByVal`の引数を指定してパラメーター渡し機構を使用する方法を示します。 この例では、引数は`c1`クラス`Class1`のインスタンスです。 `ByVal`プロシージャ内のコードが参照引数`c1`の基になる値を変更できないようにします。ただし、のアクセス可能な`c1`フィールドとプロパティは保護されません。

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>関連項目

- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
- [引数の値渡しと参照渡し](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
