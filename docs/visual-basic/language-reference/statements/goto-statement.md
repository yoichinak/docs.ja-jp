---
title: GoTo ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GoTo
helpviewer_keywords:
- GoTo statement [Visual Basic]
- control flow [Visual Basic], branching
- unconditional branching [Visual Basic]
- branching [Visual Basic]
- branching [Visual Basic], unconditional
- branching [Visual Basic], conditional
- conditional statements [Visual Basic], GoTo statement
- GoTo statement [Visual Basic], syntax
ms.assetid: 313274c2-8ab3-4b9c-9ba3-0fd6798e4f6d
ms.openlocfilehash: 3034c84684e94dfe8c334107a16df8cbd227c4d4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69912450"
---
# <a name="goto-statement"></a>GoTo ステートメント
プロシージャ内の指定された行に無条件に分岐します。  
  
## <a name="syntax"></a>構文  
  
```  
GoTo line  
```  
  
## <a name="part"></a>パーツ  
 `line`  
 必須。 任意の行ラベル。  
  
## <a name="remarks"></a>Remarks  
 ステートメント`GoTo`は、そのステートメントが出現するプロシージャ内の行にのみ分岐できます。 線には、を参照`GoTo`できる行ラベルが必要です。 詳細については、「[方法 :ラベルステートメント](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)。  
  
> [!NOTE]
> `GoTo`ステートメントを使用すると、コードの読み取りと保守が困難になる場合があります。 可能な限り、代わりに制御構造を使用してください。 詳細については、「[制御フロー](../../../visual-basic/programming-guide/language-features/control-flow/index.md)」を参照してください。  
  
 `GoTo` の`For`外部から分岐するためにステートメントを使用することはできません。`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...、、 `Using`または... `End With``End Using`内のラベルに構築します。  
  
## <a name="branching-and-try-constructions"></a>分岐と Try の構造  
 `Try`内部`Catch`...構築では、 `GoTo`ステートメントを使用した分岐に次の規則が適用されます。 `Finally`  
  
|ブロックまたはリージョン|外部からの分岐|内部からの分岐|  
|---------------------|-------------------------------|-------------------------------|  
|`Try`帯|同じ構築の`Catch`ブロックからのみ<sup>1</sup>|構築全体の外側にのみ|  
|`Catch`帯|許可しない|構築全体の外側、または同じ構造体`Try`のブロックに対して<sup></sup>のみ|  
|`Finally`帯|許可しない|許可しない|  
  
 <sup>1</sup> (存在`Try`する場合)`Catch`...構築は別の構造体に`Catch`入れ子になってい`Try`ます。ブロックは独自の入れ子レベルでブロックに分岐`Try`できますが、他のブロックには分岐できません。 `Finally` 入れ子に`Try`なった...`Catch`...構築は、入れ子になって`Try`いる`Catch`構造体のまたはブロック内に完全に含まれている必要があります。 `Finally`  
  
 次の図は、 `Try`別の構造に入れ子になった1つの構造を示しています。 2つの構造のブロック間のさまざまな分岐は、有効または無効として示されます。  
  
 ![Try 構造内の分岐のグラフィック ダイアグラム](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>例  
 次の例では`GoTo` 、ステートメントを使用して、プロシージャ内の行ラベルに分岐します。  
  
 [!code-vb[VbVbalrStatements#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#31)]  
  
## <a name="see-also"></a>関連項目

- [Do...Loop ステートメント](../../../visual-basic/language-reference/statements/do-loop-statement.md)
- [For...Next ステートメント](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [For Each...Next ステートメント](../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Select...Case ステートメント](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [While...End While ステートメント](../../../visual-basic/language-reference/statements/while-end-while-statement.md)
- [With...End With ステートメント](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
