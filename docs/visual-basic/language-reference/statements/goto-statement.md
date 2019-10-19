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
ms.openlocfilehash: 4b7a5cce56dfdd2bdc7e068aadbc18b92bba269d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581814"
---
# <a name="goto-statement"></a>GoTo ステートメント
プロシージャ内の指定された行に無条件に分岐します。  
  
## <a name="syntax"></a>構文  
  
```vb  
GoTo line  
```  
  
## <a name="part"></a>パーツ  
 `line`  
 必須です。 任意の行ラベル。  
  
## <a name="remarks"></a>Remarks  
 @No__t_0 ステートメントは、そのステートメントが出現するプロシージャ内の行にのみ分岐できます。 線には、`GoTo` が参照できる行ラベルが必要です。 詳細については、「 [How to: Label ステートメント](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)」を参照してください。  
  
> [!NOTE]
> `GoTo` ステートメントを使用すると、コードの読み取りと保守が困難になる場合があります。 可能な限り、代わりに制御構造を使用してください。 詳細については、「[制御フロー](../../../visual-basic/programming-guide/language-features/control-flow/index.md)」を参照してください。  
  
 @No__t_0 ステートメントを使用して `For` の外部から分岐することはできません...`Next`、`For Each`...`Next`、`SyncLock`...`End SyncLock`、`Try`...`Catch`...`Finally`、0...1、または 2...内のラベルに構築 3 ます。  
  
## <a name="branching-and-try-constructions"></a>分岐と Try の構造  
 @No__t_0 内...`Catch`...`Finally` 構築では、次の規則が `GoTo` ステートメントを使用した分岐に適用されます。  
  
|ブロックまたはリージョン|外部からの分岐|内部からの分岐|  
|---------------------|-------------------------------|-------------------------------|  
|`Try` ブロック|同じ構築の `Catch` ブロックからのみ<sup>1</sup>|構築全体の外側にのみ|  
|`Catch` ブロック|許可しない|構築全体の外側、または<sup>同じ構造体</sup>の `Try` ブロックにのみ|  
|`Finally` ブロック|許可しない|許可しない|  
  
 1 `Try` の場合は<sup>1</sup>`Catch`...`Finally` 構築は別の構造体に入れ子になっています。 `Catch` ブロックは、独自の入れ子レベルで `Try` ブロックに分岐できますが、他の `Try` ブロックには分岐できません。 入れ子になった `Try`...`Catch`...`Finally` の構築は、入れ子になっている構築の `Try` または `Catch` ブロックに完全に含まれている必要があります。  
  
 次の図は、別の `Try` 構築を入れ子にしたものを示しています。 2つの構造のブロック間のさまざまな分岐は、有効または無効として示されます。  
  
 ![Try 構造内の分岐のグラフィック ダイアグラム](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>例  
 次の例では、`GoTo` ステートメントを使用して、プロシージャ内の行ラベルに分岐します。  
  
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
