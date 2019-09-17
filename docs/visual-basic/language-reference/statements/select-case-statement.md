---
title: Select...Case ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Select
- vb.Case
helpviewer_keywords:
- Select statement [Visual Basic]
- Case statement [Visual Basic]
- Select...Case statements
- conditional statements [Visual Basic], Select Case
- control flow [Visual Basic], branching
- Else keyword [Visual Basic], in Select...Case statements
- execution [Visual Basic], conditional
- To keyword [Visual Basic], in Select...Case statements
- Select Case statement [Visual Basic], Select...Case
- Select statement [Visual Basic], Select...Case
- Is operator [Visual Basic], in Select...Case statements
- branching [Visual Basic], conditional
- Case Else statement [Visual Basic], Select...Case
- End keyword [Visual Basic], Select Case statements
- Case statement [Visual Basic], Select...Case
ms.assetid: 68877b65-5419-4bf0-a465-20cd0e4c7d44
ms.openlocfilehash: 627318677270ba4ffa8ee430febea7ddf83bd245
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957660"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case ステートメント (Visual Basic)
式の値に応じて、いくつかのステートメントグループのうちの1つを実行します。  
  
## <a name="syntax"></a>構文  
  
```  
Select [ Case ] testexpression  
    [ Case expressionlist  
        [ statements ] ]  
    [ Case Else  
        [ elsestatements ] ]  
End Select  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`testexpression`|必須。 条件. は、基本`Boolean`データ型 ( 、`Decimal`、、 `Date` `Char` `Double` 、、`Long`、、、、、 、)のいずれかに評価される必要があります。`Short` `Integer` `Byte` `Object` `SByte``Single` 、`String`、 、`ULong`、および)`UShort`。 `UInteger`|  
|`expressionlist`|`Case`ステートメント内で必要です。 の`testexpression`一致値を表す式の句の一覧。 複数の式句は、コンマで区切ります。 各句には、次のいずれかの形式を使用できます。<br /><br /> -   *expression1* `To` *expression2*<br />-   [ `Is` ] *comparisonoperator* *expression*<br />-   *条件*<br /><br /> キーワードを使用して、の`testexpression`一致値の範囲の境界を指定します。 `To` の`expression1`値は、の`expression2`値以下である必要があります。<br /><br /> `=`比較演算子`<>`(、 `Is` `testexpression`、、 、、また`>=`は) でキーワードを使用して、の一致値に制限を指定します。 `>` `<=` `<` キーワードが指定されていない場合は、comparisonoperator の前に自動的に挿入されます。 `Is`<br /><br /> のみ`expression`を指定するフォームは、 `Is`フォームの特殊なケースとして扱われます。ここ`=`で、 *comparisonoperator*は等号 () です。 このフォームはとし`testexpression`て =  `expression`評価されます。<br /><br /> の式`expressionlist`は、任意のデータ型にすることができます。その場合、の`testexpression`型に暗黙的`comparisonoperator`に変換可能で、適切なが使用されている2つの型に対して有効です。|  
|`statements`|省略可能です。 が内の句に`Case` `expressionlist`一致する場合`testexpression` 、を実行する1つ以上のステートメントを実行します。|  
|`elsestatements`|省略可能です。 に続く`Case Else` 1 つ以上のステートメントが`testexpression` 、 `Case`ステートメントの内`expressionlist`の句と一致しない場合に実行されます。|  
|`End Select`|`Select`... の定義を終了します。`Case`構築。|  
  
## <a name="remarks"></a>Remarks  
 が`testexpression` any `Case` `Case Else` `Case` `End Select`句と一致する場合、そのステートメントの後に続くステートメントは、次の、、またはステートメントまで実行されます。 `Case` `expressionlist` その後、制御は次`End Select`のステートメントに渡されます。 が`testexpression`複数の`expressionlist` `Case`句の句と一致する場合、最初の一致の後に続くステートメントだけが実行されます。  
  
 `expressionlist` `elsestatements` `testexpression`ステートメントを使用すると、他の`Case`どのステートメントでも句と句の間に一致が検出されなかった場合に、実行するが導入されます。 `Case Else` 必須ではありませんが、予期`Case Else` `testexpression`しない値を処理する`Select Case`ためのステートメントを構築に含めることをお勧めします。 に一致`Case`する`expressionlist` `Case Else`句がなく、ステートメントがない場合は、次`End Select`のステートメントに制御が渡されます。 `testexpression`  
  
 各`Case`句では、複数の式または範囲を使用できます。 たとえば、次の行は有効です。  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
> `Case`ステートメントおよびステートメント`Case Else`で使用されるキーワードは、オブジェクト参照の比較に使用される [is 演算子](../../../visual-basic/language-reference/operators/is-operator.md)と同じではありませ`Is`ん。  
  
 文字列の範囲と複数の式を指定できます。 次の例では`Case` 、は "りんご" と完全に等価な任意の文字列を、アルファベット順で "ナット" と "スープ" の間の値を持ちます。または、の現在`testItem`の値とまったく同じ値を含んでいます。  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 の`Option Compare`設定は、文字列比較に影響を与える可能性があります。 では、文字列 "りんご" と "りんご" は等しいものとして`Option Compare Binary`比較されますが、ではこれらの文字列は比較されません。 `Option Compare Text`  
  
> [!NOTE]
> 複数`Case`の句を持つステートメントでは、*ショートサーキット*と呼ばれる動作を使用できます。 Visual Basic は、句を左から右に評価し、一方がと`testexpression`一致する場合、残りの句は評価されません。 ショートサーキットはパフォーマンスを向上させることができますが、のすべての`expressionlist`式を評価する必要がある場合は、予期しない結果が生じる可能性があります。 ショートサーキットの詳細については、「[ブール式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)」を参照してください。  
  
 `Case`また`Exit Select`は`Case Else`ステートメントブロック内のコードが、ブロック内のステートメントを実行する必要がない場合は、ステートメントを使用してブロックを終了できます。 これは、次`End Select`のステートメントに制御を直ちに転送します。  
  
 `Select Case`構造は入れ子にすることができます。 入れ子に`Select Case`なった各構築は`End Select` 、一致するステートメントを持つ必要があり`Case` 、入れ子になっている`Select Case`外側の構造体の1つまたは`Case Else`複数のステートメントブロック内に完全に含める必要があります。  
  
## <a name="example"></a>例  
 次の例では`Select Case` 、構築を使用して、変数`number`の値に対応する行を書き込みます。 2番`Case`目のステートメントには、の現在の`number`値と一致する値が含まれています。そのため、"Between 6" ~ "8" を含むステートメントを実行します。  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)
- [If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)
