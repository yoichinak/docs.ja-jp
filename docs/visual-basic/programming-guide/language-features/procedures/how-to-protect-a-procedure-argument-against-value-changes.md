---
title: '方法: プロシージャ引数の値の変更 (Visual Basic) を保護します。'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- arguments [Visual Basic], passing by reference
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: d2b7c766-ce16-4d2c-8d79-3fc0e7ba2227
ms.openlocfilehash: 70378b57c6d3af5a98e0ba9c6e3aebc319561b1b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58837781"
---
# <a name="how-to-protect-a-procedure-argument-against-value-changes-visual-basic"></a>方法: プロシージャ引数の値の変更 (Visual Basic) を保護します。
プロシージャ宣言のパラメーターとして場合[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、Visual Basic でプロシージャのコードは呼び出し元のコードで引数を基になるプログラミング要素への直接参照します。 これにより、プロシージャが呼び出し元のコードで引数を基になる値を変更します。 場合によってはの呼び出し元のコードは、このような変更から保護します。  
  
 対応するパラメーターを宣言することで、変更から引数を保護できます常に[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)の手順でします。 によって自動的に指定した引数を変更できる場合は、宣言できる`ByRef`呼び出し元のコードが各呼び出しで引き渡し方法を決定できるようにします。 これは、対応する引数を値で渡す括弧で囲むか、参照渡しするためにかっこで囲まないとで実行します。 詳細については、「[方法 :引数の値渡しを強制](./how-to-force-an-argument-to-be-passed-by-value.md)します。  
  
## <a name="example"></a>例  
 次の例では、その要素の配列変数を受け取り、操作を 2 つの手順を示します。 `increase`プロシージャが単純に各要素に 1 つを追加します。 `replace`プロシージャ パラメーターに新しい配列を割り当てます`a()`し、各要素に 1 つを追加します。 ただし、再割り当てでは、呼び出し元のコードで、基になる配列変数には影響しません。  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 最初の`MsgBox`呼び出しが表示されます"increase(n) 後。11, 21, 31, 41". 配列`n`、参照型では、`increase`引き渡し方法は、そのメンバーを変更することができます`ByVal`します。  
  
 2 番目の`MsgBox`呼び出しが表示されます"目後。11, 21, 31, 41". `n`が渡される`ByVal`、`replace`変数を変更することはできません`n`を新しい配列を割り当てることで、呼び出しコード。 ときに`replace`新しい配列インスタンスを作成します`k`し、ローカル変数に代入`a`への参照が失われた`n`呼び出し元のコードで渡されます。 メンバーが変更されたとき`a`、ローカルの配列のみ`k`が影響を受けます。 そのため、`replace`配列の値は増分されません`n`呼び出し元のコード。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 Visual Basic では既定では、引数を値渡しです。 いずれかを指定することをお勧め、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。 これにより、コードが読みやすくなります。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [変更できる引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [引数の値渡しと参照渡しの違い](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [方法: プロシージャ引数の値を変更します。](./how-to-change-the-value-of-a-procedure-argument.md)
- [方法: 引数の値渡しを強制します。](./how-to-force-an-argument-to-be-passed-by-value.md)
- [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
