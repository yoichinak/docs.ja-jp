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
ms.openlocfilehash: c4dd249620ba1bf445642ce4600498f6beb30461
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58827771"
---
# <a name="goto-statement"></a>GoTo ステートメント
プロシージャ内の指定した行に無条件に分岐します。  
  
## <a name="syntax"></a>構文  
  
```  
GoTo line  
```  
  
## <a name="part"></a>パーツ  
 `line`  
 必須。 任意の行のラベル。  
  
## <a name="remarks"></a>Remarks  
 `GoTo`のみが表示されるプロシージャ内の行にステートメントを分岐できます。 ラベルを 1 行が必要`GoTo`を参照できます。 詳細については、「[方法 :ステートメントにラベル付け](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)します。  
  
> [!NOTE]
>  `GoTo` ステートメントすると、コードが読み取りおよびメンテナンスを困難になります。 可能であれば、制御構造を使用します。 詳細については、次を参照してください。[制御フロー](../../../visual-basic/programming-guide/language-features/control-flow/index.md)します。  
  
 使用することはできません、`GoTo`外からの分岐にステートメントを`For`.`Next`, `For Each`...`Next`, `SyncLock`...`End SyncLock`, `Try`...`Catch`...`Finally`, `With`...`End With`、または`Using`.`End Using`内のラベルに構築します。  
  
## <a name="branching-and-try-constructions"></a>分岐と構築をお試しください  
 内で、 `Try`.`Catch`...`Finally`で分岐に、構築、次の規則の適用、`GoTo`ステートメント。  
  
|ブロックまたは地域|外部からへの分岐|外部への分岐からの内部|  
|---------------------|-------------------------------|-------------------------------|  
|`Try` ブロック|のみ、`Catch`同じ構築ブロック<sup>1</sup>|のみ、全体の構造の外部|  
|`Catch` ブロック|許可しません。|のみ、全体の構造の外部にまたは、`Try`同じ構築ブロック<sup>1</sup>|  
|`Finally` ブロック|許可しません。|許可しません。|  
  
 <sup>1</sup>場合`Try`.`Catch`...`Finally`構築が、別の入れ子になった、`Catch`ブロックに分岐、`Try`ブロックの他にコピーせずに、独自の入れ子のレベルにある`Try`ブロックします。 入れ子になった`Try`.`Catch`...`Finally`構築を完全に含める必要があります、`Try`または`Catch`ブロックを入れ子になってを作成します。  
  
 次の図では 1 つ`Try`別内で入れ子になった構築します。 2 つの構築ブロック間でさまざまな分岐は、有効または無効と表示されています。  
  
 ![Try 構造内の分岐のグラフィック ダイアグラム](./media/goto-statement/try-construction-branching.gif)  
  
## <a name="example"></a>例  
 次の例では、`GoTo`ステートメントをプロシージャ内の行ラベルに分岐します。  
  
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
