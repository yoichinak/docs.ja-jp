---
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: a96f871c6ce119f65ebbec54fdb1471ae105d504
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351595"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
呼び出されたプロシージャまたはプロパティによって、呼び出し元のコードの引数の基になる変数の値を変更できないように、引数を[値渡し](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)で渡すことを指定します。 修飾子が指定されない場合、ByVal が既定になります。

> [!NOTE]
> それは既定であるため、メソッド シグネチャに `ByVal` キーワードを明示的に指定する必要はありません。 それにより、ノイズが多いコードが生成される傾向があるため、既定でない `ByRef` キーワードが見落とされることが多くなります。

## <a name="remarks"></a>Remarks
 `ByVal` 修飾子は、次のコンテキストで使用できます。

 [Declare ステートメント](../../../visual-basic/language-reference/statements/declare-statement.md)

 [Function ステートメント](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [Operator ステートメント](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [Property ステートメント](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [Sub ステートメント](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a>例
 次の例では、参照型の引数を指定して `ByVal` パラメーターの引き渡し方法の使用を示します。 この例では、引数は、クラス `Class1` のインスタンスである `c1` です。 `ByVal` によって、プロシージャ内のコードが参照引数 `c1` の基になる値を変更しないようになりますが、`c1` のアクセス可能なフィールドとプロパティは保護されません。

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>関連項目

- [キーワード](../../../visual-basic/language-reference/keywords/index.md)
- [引数の値渡しと参照渡し](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
