---
title: '方法: (Visual Basic) の値によって渡される引数を強制します。'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], arguments
- procedures [Visual Basic], parameters
- procedure arguments
- Visual Basic code, procedures
- arguments [Visual Basic], ByVal
- arguments [Visual Basic], passing by value
- procedure parameters
- procedures [Visual Basic], calling
- arguments [Visual Basic], in parentheses
- procedure arguments [Visual Basic], in parentheses
- arguments [Visual Basic], changing value
ms.assetid: 77b4f2d2-1055-4c2f-a521-874d1db86946
ms.openlocfilehash: 497ae11b858b7d164ba3b5607ff2109254a154de
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842046"
---
# <a name="how-to-force-an-argument-to-be-passed-by-value-visual-basic"></a>方法: (Visual Basic) の値によって渡される引数を強制します。
プロシージャ宣言では、引き渡し方法を決定します。 パラメーターが宣言されている場合[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)、Visual Basic で参照によって、対応する引数を渡す必要があります。 これにより、呼び出し元のコードで引数を基になるプログラミングの要素の値を変更する手順です。 オーバーライドすることができます、基になる要素に対してこのような変更を保護する場合、`ByRef`引き渡し方法の手順では、引数名をかっこで囲んで呼び出し。 このかっこは、呼び出しの引数リストを囲むかっこだけでなく、します。  
  
 呼び出し元のコードがオーバーライドすることはできません、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)メカニズム。  
  
### <a name="to-force-an-argument-to-be-passed-by-value"></a>引数の値渡しを強制するには  
  
-   対応するパラメーターが宣言されている場合`ByVal`の手順では、追加の手順を実行する必要はありません。 Visual Basic は、既に、値渡しの引数が必要です。  
  
-   対応するパラメーターが宣言されている場合`ByRef`の手順で、プロシージャの呼び出しにかっこで囲まれた引数を囲みます。  
  
## <a name="example"></a>例  
 次の例では、上書き、`ByRef`パラメーター宣言します。 強制する呼び出しで`ByVal`かっこの 2 つのレベルに注意してください。  
  
 [!code-vb[VbVbcnProcedures#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#39)]  
  
 [!code-vb[VbVbcnProcedures#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#40)]  
  
 ときに`str`、引数リスト内の余分なかっこで囲まれた、`setNewString`プロシージャが呼び出し元のコードでは、その値を変更ことはできませんと`MsgBox`ByVal を渡された場合は、「を置き換えることができません」が表示されます。 ときに`str`囲まれていない追加のかっこでプロシージャを変更できますと`MsgBox`「inString 引数の新しい値がこれです」が表示されます。  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 参照渡しで変数を渡す場合は、使用、`ByRef`このメカニズムを指定するキーワード。  
  
 Visual Basic では既定では、引数を値渡しです。 いずれかを指定することをお勧め、 [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)または[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)キーワード パラメーターを宣言します。 これにより、コードが読みやすくなります。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 プロシージャ パラメーターを宣言する場合[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)コードの適切な実行、呼び出し元のコード内の基になる要素を変更できることに依存します。 呼び出し元のコードは、引数をかっこで囲んででこの呼び出し元のメカニズムをオーバーライドする場合、または変更できない引数を渡す場合は、プロシージャは、基になる要素を変更できません。 これにより、呼び出し元のコードで予期しない結果が生成する可能性があります。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 呼び出し元のコードで引数を基になる値を変更するプロシージャを許可するのには、潜在的なリスクがあります。 変更して、使用する前に有効性を確認するよう準備するのには、この値を期待することを確認します。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [方法: プロシージャに引数を渡す](./how-to-pass-arguments-to-a-procedure.md)
- [引数の値渡しと参照渡し](./passing-arguments-by-value-and-by-reference.md)
- [変更できる引数と変更できない引数の違い](./differences-between-modifiable-and-nonmodifiable-arguments.md)
- [引数の値渡しと参照渡しの違い](./differences-between-passing-an-argument-by-value-and-by-reference.md)
- [方法: プロシージャ引数の値を変更します。](./how-to-change-the-value-of-a-procedure-argument.md)
- [方法: プロシージャ引数の値が変化しません。](./how-to-protect-a-procedure-argument-against-value-changes.md)
- [位置と名前による引数渡し](./passing-arguments-by-position-and-by-name.md)
- [値型と参照型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
