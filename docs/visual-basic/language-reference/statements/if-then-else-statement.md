---
title: If...Then...Else ステートメント (Visual Basic)
ms.date: 04/16/2018
f1_keywords:
- vb.ElseIf
- vb.Then
- vb.If
- vb.EndIf
helpviewer_keywords:
- ElseIf statement [Visual Basic], If...Then...Else
- Then statement [Visual Basic], If...Then...Else
- control flow [Visual Basic], branching
- execution [Visual Basic], conditional
- TypeOf...Is expression, and If...Then...Else statements
- If...Then...Else statements
- If statement [Visual Basic], If...Then...Else
- If statement [Visual Basic]
- Is operator [Visual Basic], in If...Then...Else statements
- If Operator [Visual Basic]
- branching [Visual Basic], conditional
- If function [Visual Basic], and If...Then...Else statements
- Else statement [Visual Basic]
ms.assetid: 790068a2-1307-4e28-8a72-be5ebda099e9
ms.openlocfilehash: aeffdc842730a1be8160cd8db8e4c2aa849e94cc
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201730"
---
# <a name="ifthenelse-statement-visual-basic"></a>If...Then...Else ステートメント (Visual Basic)
式の値に応じてステートメント グループを条件付きで実行します。  
  
## <a name="syntax"></a>構文  
  
```  
' Multiline syntax:  
If condition [ Then ]  
    [ statements ]  
[ ElseIf elseifcondition [ Then ]  
    [ elseifstatements ] ]  
[ Else  
    [ elsestatements ] ]  
End If  
  
' Single-line syntax:  
If condition Then [ statements ] [ Else [ elsestatements ] ]  
```  

## <a name="quick-links-to-example-code"></a>コード例へのクイック リンク

この記事には、使用方法を示すいくつかの例が含まれています、 `If`.`Then`...`Else`ステートメント。

* [複数行の構文例](#multi-line)
* [入れ子になった構文の例](#nested)
* [単一行の構文例](#single-line)

## <a name="parts"></a>指定項目  
 `condition`  
 必須。 式。 評価される必要があります`True`または`False`、またはデータ型に暗黙的に変換できる`Boolean`します。  
  
 式の場合、 [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean`に評価される変数[Nothing](../../../visual-basic/language-reference/nothing.md)、式の場合と、条件が扱われます`False`と`Else`ブロックが実行されます。  
  
 `Then`  
 は単一行の構文で必要複数行の構文では省略可能です。  
  
 `statements`  
 任意。 1 つまたは複数のステートメントの次`If`.`Then`場合に実行されている`condition`に評価される`True`します。  
  
 `elseifcondition`  
 場合に、必ず`ElseIf`が存在します。 式。 評価される必要があります`True`または`False`、またはデータ型に暗黙的に変換できる`Boolean`します。  
  
 `elseifstatements`  
 任意。 1 つまたは複数のステートメントの次`ElseIf`.`Then`場合に実行されている`elseifcondition`に評価される`True`します。  
  
 `elsestatements`  
 任意。 ない場合に実行される 1 つまたは複数のステートメント`condition`または`elseifcondition`式に評価される`True`します。  
  
 `End If`  
 複数行のバージョンを終了する`If`.`Then`...`Else`ブロックします。  
  
## <a name="remarks"></a>Remarks  
  
### <a name="multiline-syntax"></a>複数行の構文  
 ときに、 `If`.`Then`...`Else`ステートメントが検出された`condition`をテストします。 場合`condition`は`True`、次のステートメント`Then`実行されます。 場合`condition`は`False`、それぞれ`ElseIf`ステートメント (存在する) 場合は、順番に評価します。 ときに、 `True` `elseifcondition`が見つかると、すぐに関連付けられている次のステートメント`ElseIf`実行されます。 ない場合は`elseifcondition`に評価される`True`がある場合、またはなし`ElseIf`ステートメント、次のステートメント`Else`実行されます。 次のステートメントを実行した後`Then`、 `ElseIf`、または`Else`、ステートメントに次の実行が続行されます`End If`します。  
  
 `ElseIf`と`Else`句は、どちらもオプションです。 多くすることが`ElseIf`としてする句が必要、 `If`.`Then`...`Else`ステートメントでは、ただし`ElseIf`後句、`Else`句。 `If`...`Then`...`Else`ステートメントは互いに入れ子にすることができます。  
  
 複数行の構文では、`If`ステートメントは、最初の行での唯一のステートメントである必要があります。 `ElseIf`、 `Else`、および`End If`ステートメントのみで、行ラベルを付けることができます。 `If`.`Then`...`Else`ブロックの最後に使用する必要があります、`End If`ステートメント。  
  
> [!TIP]
>  [を選択しています.Case ステートメント](../../../visual-basic/language-reference/statements/select-case-statement.md)をいくつかの値を持つ 1 つの式を評価するときにさらに便利な場合があります。  
  
### <a name="single-line-syntax"></a>単一行の構文  
 True の場合に実行するコードを 1 つの条件の単一行構文を使用できます。 ただし、複数行の構文は、詳細の構造と柔軟性を提供、読み取り、保守、およびデバッグする方が簡単です。  
  
 どのような次のように、`Then`ステートメントが単一行であるかどうかを決定するキーワードが調べられる`If`します。 後にコメント以外のものが表示された場合`Then`、同じ行には、ステートメントは単一行として扱われます`If`ステートメント。 場合`Then`が存在しない場合は、複数行の開始する必要があります`If`.`Then`...`Else`.  
  
 単一行の構文では、複数のステートメントの結果として実行することが、 `If`.`Then`意思決定します。 すべてのステートメントでは、同じ行に配置する必要があり、コロンで区切っています。  

## <a name="multiline-syntax-example"></a>複数行の構文例

<a name="multi-line"></a>
 
 次の例では、複数行の構文の使用、 `If`.`Then`...`Else`ステートメント。  
  
 [!code-vb[VbVbalrStatements#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#101)]

## <a name="nested-syntax-example"></a>入れ子になった構文の例

<a name="nested"></a>

 次の例を含む入れ子になった`If`.`Then`...`Else`ステートメント。  
  
 [!code-vb[VbVbalrStatements#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#102)]

## <a name="single-line-syntax-example"></a>単一行の構文例
  
<a name="single-line"></a> 次の例は、単一行の構文の使用を示しています。  
  
 [!code-vb[VbVbalrStatements#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class6.vb#103)]
  
## <a name="see-also"></a>関連項目
- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- <xref:Microsoft.VisualBasic.Interaction.Switch%2A>
- [#If...Then...#Else ディレクティブ](../../../visual-basic/language-reference/directives/if-then-else-directives.md)
- [Select...Case ステートメント](../../../visual-basic/language-reference/statements/select-case-statement.md)
- [入れ子になった制御構造](../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [条件判断構造](../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [Visual Basic での論理とビット処理演算子](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
- [If 演算子](../../../visual-basic/language-reference/operators/if-operator.md)
