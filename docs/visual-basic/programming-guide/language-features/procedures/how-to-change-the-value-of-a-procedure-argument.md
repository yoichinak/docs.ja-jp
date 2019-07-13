---
title: '方法: (Visual Basic)、プロシージャ引数の値を変更します。'
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
- arguments [Visual Basic], ByRef
- arguments [Visual Basic], changing value
ms.assetid: 6fad2368-5da7-4c07-8bf8-0f4e65a1be67
ms.openlocfilehash: a56bdf888163c9559b87e857abb33522c547ed45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665833"
---
# <a name="how-to-change-the-value-of-a-procedure-argument-visual-basic"></a>方法: (Visual Basic)、プロシージャ引数の値を変更します。
プロシージャを呼び出すときに指定する各引数は、プロシージャで定義されたパラメーターのいずれかに対応します。 場合によっては、プロシージャのコードは呼び出し元のコードで引数を基になる値を変更できます。 それ以外の場合、プロシージャは、引数のローカル コピーだけを変更できます。  
  
 Visual Basic は、渡される引数はすべてのローカル コピーを作成して、プロシージャを呼び出すときに[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)します。 渡された各引数に対して[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、Visual Basic でプロシージャのコードは呼び出し元のコードで引数を基になるプログラミング要素への直接参照します。  
  
 呼び出し元のコードに基になる要素が変更可能な場合に、引数が渡された`ByRef`プロシージャのコードは、直接の参照を使用して、呼び出し元のコード要素の値を変更します。  
  
## <a name="changing-the-underlying-value"></a>基になる値を変更します。  
  
#### <a name="to-change-the-underlying-value-of-a-procedure-argument-in-the-calling-code"></a>呼び出し元のコードでプロシージャ引数の基になる値を変更するには  
  
1. プロシージャの宣言で指定[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)引数に対応するパラメーター。  
  
2. 呼び出し元のコードでは、変更可能なプログラミング要素を引数として渡します。  
  
3. 呼び出し元のコードでは囲まないで引数リストのかっこで囲まれた引数。  
  
4. プロシージャのコードで、パラメーター名を使用して、呼び出し元のコード内の基になる要素に値を代入します。  
  
 例を参照してください。 デモについてはさらにダウンします。  
  
## <a name="changing-local-copies"></a>ローカル コピーを変更します。  
 呼び出し元のコードで基になる要素が、変更不可能な要素である場合、または引数が渡された場合`ByVal`プロシージャが呼び出し元のコードでは、その値を変更できません。 ただし、プロシージャは、このような引数のローカル コピーを変更できます。  
  
#### <a name="to-change-the-copy-of-a-procedure-argument-in-the-procedure-code"></a>プロシージャのコードでプロシージャ引数のコピーを変更するには  
  
1. プロシージャの宣言で指定[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)引数に対応するパラメーター。  
  
     - または -  
  
     呼び出し元のコードで、引数、引数リストのかっこで囲みます。 これにより、対応するパラメーターが指定されている場合でも、Visual Basic での値で、引数を渡す`ByRef`します。  
  
2. プロシージャのコードで、パラメーター名を使用して、引数のローカル コピーに値を代入します。 呼び出し元のコードで基になる値は変更されません。  
  
## <a name="example"></a>例  
 次の例では、その要素の配列変数を受け取り、操作を 2 つの手順を示します。 `increase`プロシージャが単純に各要素に 1 つを追加します。 `replace`プロシージャ パラメーターに新しい配列を割り当てます`a()`し、各要素に 1 つを追加します。  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#36)]  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 最初の`MsgBox`呼び出しが表示されます"increase(n) 後。11, 21, 31, 41". 配列`n`、参照型では、`replace`引き渡し方法は、そのメンバーを変更することができます`ByVal`します。  
  
 2 番目の`MsgBox`呼び出しが表示されます"目後。101, 201, 301". `n`が渡される`ByRef`、`replace`変数を変更できます`n`呼び出し元のコードに割り当てる新しい配列。 `n` 、参照型では、`replace`そのメンバーを変更することもできます。  
  
 プロシージャ呼び出し元のコードでは、変数自体を変更することを防止できます。 「[方法:プロシージャ引数の値が変化しない](./how-to-protect-a-procedure-argument-against-value-changes.md)します。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 参照渡しで変数を渡す場合は、使用、`ByRef`このメカニズムを指定するキーワード。  
  
 Visual Basic では既定では、引数を値渡しです。 いずれかを指定することをお勧め、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。 これにより、コードが読みやすくなります。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 呼び出し元のコードで引数を基になる値を変更するプロシージャを許可するのには、潜在的なリスクがあります。 変更して、使用する前に有効性を確認するよう準備するのには、この値を期待することを確認します。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [変更できる引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [引数の値渡しと参照渡しの違い](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [方法: プロシージャ引数の値が変化しません。](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [方法: 引数の値渡しを強制します。](./how-to-force-an-argument-to-be-passed-by-value.md)
- [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
