---
title: '方法: 変数 (Visual Basic) のスコープを制御します。'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: 7f1d671f6657c7810ec605533493a340baac39c9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610340"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>方法: 変数 (Visual Basic) のスコープを制御します。
変数が、通常、*スコープ*、または宣言をリージョン全体での参照を表示します。 場合によっては、変数の*アクセス レベル*そのスコープに影響を与えることができます。  
  
 詳細については、「 [Scope in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)」を参照してください。  
  
## <a name="scope-at-block-or-procedure-level"></a>ブロックまたはプロシージャ レベルのスコープ  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>変数をブロック内でのみ表示されるようにするには  
  
- 場所、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)の開始との間など、そのブロックの宣言ステートメントの終了の間、変数、`For`と`Next`のステートメントを`For`ループします。  
  
     ブロック内からのみ、変数を参照することができます。  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>変数をプロシージャ内でのみ表示されるようにするには  
  
- 場所、`Dim`変数、プロシージャ内では、ブロックの外側のステートメント (など、 `With`.`End With`ブロック)。  
  
     プロシージャに含まれる各ブロックの内部を含むプロシージャ内からのみ、変数を参照することができます。  
  
## <a name="scope-at-module-or-namespace-level"></a>モジュールまたは Namespace レベルのスコープ  
 便宜上、1 つの用語*モジュール レベル*モジュール、クラス、および構造に当てはまります。 モジュール レベル変数のアクセス レベルは、そのスコープを決定します。 モジュール、クラスまたは構造体を含む名前空間スコープにも影響します。  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>変数をモジュール、クラスまたは構造体全体にわたって表示されるようにするには  
  
1. 場所、`Dim`変数ではなく、プロシージャの外部モジュール、クラス、または構造体には、内部のステートメント。  
  
2. 含める、[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)キーワード、`Dim`ステートメント。  
  
3. なく、モジュール、クラス、または構造内で任意の場所から変数を参照できる外です。  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>変数を名前空間全体で表示されるようにするには  
  
1. 場所、`Dim`変数ではなく、プロシージャの外部モジュール、クラス、または構造体には、内部のステートメント。  
  
2. 含める、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)または[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)キーワード、`Dim`ステートメント。  
  
3. 任意の場所から変数を参照できるモジュール、クラスまたは構造体を含む名前空間内で。  
  
## <a name="example"></a>例  
 次の例では、モジュール レベル変数を宣言し、モジュール内のコードをその可視性を制限します。  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 前の例では、すべてのプロシージャはモジュールで定義されている`demonstrateScope`できますを参照してください、`String`変数`strMsg`します。 ときに、`usePrivateVariable`プロシージャが呼び出されると、文字列変数の内容を表示`strMsg` ダイアログ ボックス。  
  
 上記の例では、文字列変数に次の変更と`strMsg`宣言の名前空間内のすべてのコードで参照できます。  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 同じ名前の別の変数の代わりに誤って参照することがある可能性は少なく、変数より狭いスコープ 参照の対応付けの問題を最小限に抑えることができますも。  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 変数のスコープが狭い悪意のあるコードが不正に、小さい方の可能性は、その使用します。  
  
## <a name="see-also"></a>関連項目

- [Visual Basic におけるスコープ](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Visual Basic での有効期間](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [変数](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [変数宣言](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)
