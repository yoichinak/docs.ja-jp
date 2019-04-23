---
title: 条件判断構造 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- statements [Visual Basic], control flow
- If statement [Visual Basic], decision structures
- If statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], decision structures
- decision structures [Visual Basic]
- conditional statements [Visual Basic], decision structures
ms.assetid: 2e2e0895-4483-442a-b17c-26aead751ec2
ms.openlocfilehash: 4a76b2565c343e69ac3c11441035a7682a8f08ec
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59318937"
---
# <a name="decision-structures-visual-basic"></a>条件判断構造 (Visual Basic)
Visual Basic では、条件をテストし、そのテストの結果に応じてさまざまな操作を実行することができます。 true または false の場合、さまざまな値の式、または一連のステートメントを実行するときに生成された例外のさまざまな条件をテストできます。  
  
 次の図は、条件が真のテストが true か false かどうかに応じて異なるアクションを受け取っている意思決定構造を示します。  
  
 ![If のフロー チャート.そうしたら。。。Else 構文。](./media/decision-structures/if-then-else-construction.gif)  
  
## <a name="ifthenelse-construction"></a>If...Then...Else 構造  
 `If...Then...Else` 構造では、1 つまたは複数の条件をテストし、各条件に応じて 1 つまたは複数のステートメントを実行できます。 条件をテストし、次の方法でアクションを実行できます。  
  
-   条件の場合は、1 つまたは複数のステートメントを実行します。 `True`  
  
-   条件の場合は、1 つまたは複数のステートメントを実行します。 `False`  
  
-   条件の場合は、いくつかのステートメントを実行`True`や他のユーザーである場合 `False`  
  
-   前の条件の場合、追加の条件をテストします。 `False`  
  
 これらすべての可能性を提供する制御構造が、[If ... Then ... Else ステートメント](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)です。 1 つのテストと 1 つのステートメントを実行する必要がある場合は、単一行のバージョンを使用できます。 複雑な一連の条件とアクションがある場合は、複数行のバージョンを使用することができます。  
  
## <a name="selectcase-construction"></a>Select...Case 構造  
 `Select...Case`構築では、1 つに式を評価し、異なる一連の別の使用可能な値に基づくステートメントを実行することができます。 詳細については、[Select...Case ステートメント](../../../../visual-basic/language-reference/statements/select-case-statement.md)を参照してください。  
  
## <a name="trycatchfinally-construction"></a>Try...Catch...Finally 構造  
 `Try...Catch...Finally` 構造では、一連のステートメント、ステートメントのいずれかの例外が発生した場合は、コントロールを保持する環境でを実行できます。 さまざまな例外の別のアクションを実行することができます。 必要に応じて、全体を終了する前に実行されるコードのブロックを指定することができます`Try...Catch...Finally`どうなるかに関係なく、構築します。 詳細については、[Try...Catch...Finally ステートメント](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)を参照してください。  
  
> [!NOTE]
>  多くの制御構造のキーワードをクリックすると、すべての構造のキーワードが強調表示されます。 クリックすると、`If`で、`If...Then...Else`構築のすべてのインスタンス`If`、 `Then`、 `ElseIf`、 `Else`、および`End If`構築では強調表示されます。 次または前の強調表示されているキーワードに移動するには、CTRL と shift キーを押しながら下方向キーまたは CTRL + SHIFT キーを押しながら上方向キーを押します。  
  
## <a name="see-also"></a>関連項目

- [制御フロー](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [ループ構造](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [その他の制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [入れ子になった制御構造](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [If 演算子](../../../../visual-basic/language-reference/operators/if-operator.md)
