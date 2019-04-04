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
ms.openlocfilehash: f99db4f1dc224e5f75ee67ba94c3745f28438724
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814615"
---
# <a name="selectcase-statement-visual-basic"></a>Select...Case ステートメント (Visual Basic)
式の値に応じて、ステートメントのグループをいくつかのいずれかを実行します。  
  
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
|`testexpression`|必須。 式。 基本データ型のいずれかを評価する必要があります (`Boolean`、 `Byte`、 `Char`、 `Date`、 `Double`、 `Decimal`、 `Integer`、 `Long`、 `Object`、 `SByte`、 `Short`、`Single`、 `String`、 `UInteger`、 `ULong`、および`UShort`)。|  
|`expressionlist`|必要な`Case`ステートメント。 一致した値を表す式の句のリスト`testexpression`します。 複数の式の句は、コンマで区切られます。 各句には、次の形式のいずれかを実行できます。<br /><br /> -   *expression1* `To` *expression2*<br />-   [ `Is` ] *comparisonoperator* *expression*<br />-   *expression*<br /><br /> 使用して、`To`一致の範囲の境界を指定するキーワードの値を`testexpression`します。 値`expression1`の値未満でなければなりません`expression2`します。<br /><br /> 使用して、`Is`比較演算子でキーワード (`=`、 `<>`、 `<`、 `<=`、 `>`、または`>=`)、一致した値に制限を指定する`testexpression`します。 場合、`Is`キーワードが指定されていないが自動的にする前に挿入*comparisonoperator*します。<br /><br /> だけを指定してフォーム`expression`の特殊なケースとして扱われます、`Is`フォーム where *comparisonoperator*は等号 (=) (`=`)。 この形式は`testexpression`  = `expression`します。<br /><br /> 内の式`expressionlist`かの型に暗黙的に変換可能であれば、任意のデータ型のできる`testexpression`、適切な`comparisonoperator`はで使用されている 2 つの型に対して有効です。|  
|`statements`|省略可能です。 1 つまたは複数のステートメントの次`Case`実行されている場合`testexpression`で句と一致する`expressionlist`します。|  
|`elsestatements`|省略可能です。 1 つまたは複数のステートメントの次`Case Else`実行されている場合`testexpression`で句と一致しません、`expressionlist`のいずれかの`Case`ステートメント。|  
|`End Select`|定義を終了、 `Select`.`Case`構築します。|  
  
## <a name="remarks"></a>Remarks  
 場合`testexpression`と一致する`Case``expressionlist`句を次のステートメントでは、`Case`次ステートメントが実行`Case`、 `Case Else`、または`End Select`ステートメント。 次のステートメントのパスを制御し、`End Select`します。 場合`testexpression`と一致する、 `expressionlist` 1 つ以上の句`Case`句では、最初の一致の次のステートメントのみを実行します。  
  
 `Case Else`ステートメントを使用して、導入、`elsestatements`間で一致が見つからない場合に実行する、`testexpression`と`expressionlist`で他の句`Case`ステートメント。 良いアイデアですが必須ではありませんが、`Case Else`内のステートメント、`Select Case`の構築処理を予期しない`testexpression`値。 ない場合は`Case``expressionlist`句と一致する`testexpression`はない`Case Else`ステートメントでは、次のステートメントのコントロール パス`End Select`。  
  
 複数の式または範囲を使用するには各`Case`句。 たとえば、次の行は有効です。  
  
 `Case 1 To 4, 7 To 9, 11, 13, Is > maxNumber`  
  
> [!NOTE]
>  `Is`で使用されるキーワード、`Case`と`Case Else`ステートメントがないと同じ、 [Is 演算子](../../../visual-basic/language-reference/operators/is-operator.md)、オブジェクト参照の比較に使用されます。  
  
 範囲と文字の文字列の複数の式を指定できます。 次の例では、`Case`を"apples"に正確に一致、アルファベット順に「ナット」と「スープ」の間の値を持つ、またはの現在の値とまったく同じ値を格納する任意の文字列と一致する`testItem`します。  
  
 `Case "apples", "nuts" To "soup", testItem`  
  
 設定は、`Option Compare`文字列比較に影響を与えることができます。 `Option Compare Text`、Equal、として比較してが文字列"Apples"と"apples" `Option Compare Binary`、一致していないためです。  
  
> [!NOTE]
>  A`Case`句を指定して複数のステートメントと呼ばれる動作が発生することができます*ショート サーキット*します。 Visual Basic は、左から右への句を評価し、1 つの場合との一致を作成します。 `testexpression`、残りの句は評価されません。 ショート サーキットのパフォーマンスが向上するのすべての式が必要な場合、予期しない結果を生成できる`expressionlist`評価されます。 ショート サーキットの詳細については、[ブール式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/boolean-expressions.md)を参照してください。  
  
 場合内のコードを`Case`または`Case Else`ステートメント ブロックは、ブロックで以上のステートメントを実行する必要はありませんを使用して、ブロックを終了できますが、`Exit Select`ステートメント。 ステートメントに制御を直ちに転送この`End Select`します。  
  
 `Select Case` 構造を入れ子にすることができます。 入れ子になった`Select Case`構築の対応する必要がありますが`End Select`ステートメントを 1 回完全に含める必要があると`Case`または`Case Else`ステートメント ブロックの外側の`Select Case`構築を入れ子にします。  
  
## <a name="example"></a>例  
 次の例では、`Select Case`構造を使用して、変数の値に対応する行も記述`number`します。 2 番目の`Case`ステートメントには、現在の値に一致する値が含まれています。 `number`"6 から 8 の包括的な"ステートメントを書き込むため、実行します。  
  
 [!code-vb[VbVbalrStatements#54](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#54)]  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Interaction.Choose%2A>
- [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)
- [If...Then...Else ステートメント](../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)
