---
title: '方法: (Visual Basic) パターンとの比較の文字列と一致します。'
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: 884c5ddf15deb49719915f10e107ba6a3431c4bc
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965944"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>方法: (Visual Basic) パターンとの比較の文字列と一致します。
式かどうかを検索する場合、[文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)を使用して、パターンを満たす、 [Like 演算子](../../../../visual-basic/language-reference/operators/like-operator.md)します。  
  
 `Like` 2 つのオペランドを受け取ります。 左のオペランドは、文字列式であり、右のオペランドが照合に使用するパターンを含む文字列。 `Like` 返します、`Boolean`文字列式が、パターンを満たすかどうかを示す値。  
  
 特定の文字、ワイルドカード文字、文字のリスト、または文字の範囲に対して文字列式内の各文字と一致することができます。 仕様パターン文字列内の位置は、文字列式に一致する文字の位置に対応します。  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>特定の文字の文字列式での文字と一致するには  
  
-   特定の文字をパターン文字列に直接配置します。 特定の特殊文字は、角かっこで囲む必要があります (`[ ]`)。 詳細については、次を参照してください。 [Like 演算子](../../../../visual-basic/language-reference/operators/like-operator.md)します。  
  
     次の例をテストするかどうか`myString`1 文字だけで構成されます`H`します。  
  
     [!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>ワイルドカード文字の文字列式の文字と一致するには  
  
-   疑問符 () の配置 (`?`) パターン文字列にします。 この位置に任意の有効な文字は、検索が成功します。  
  
     次の例のテストするかどうか`myString`1 文字から成る`W`の後ろに任意の値の 2 つの文字。  
  
     [!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>文字の一覧に対して、文字列式での文字と一致するには  
  
-   角かっこを配置 (`[ ]`) で、パターン文字列とかっこ文字の一覧に格納します。 コンマまたはその他の任意の区切り記号の文字を分離されません。 任意の 1 文字の一覧では、検索が成功します。  
  
     次の例のテストかどうか`myString`続く文字を 1 つの有効な任意の文字から成る`A`、 `C`、または`E`します。  
  
     [!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]  
  
     この照合の小文字が区別されるに注意してください。  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>文字の範囲に対して文字列式での文字と一致するには  
  
-   角かっこを配置 (`[ ]`) パターン文字列、および最低と最高の文字の範囲に、かっこ内では、ハイフンで区切られた (`–`)。 範囲内の任意の 1 文字では、成功した一致。  
  
     次の例のテストかどうか`myString`文字から成る`num`文字 1 個続く`i`、 `j`、 `k`、 `l`、 `m`、または`n`します。  
  
     [!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]  
  
     この照合の小文字が区別されるに注意してください。  
  
## <a name="matching-empty-strings"></a>空の文字列に一致します。  
 `Like` シーケンス処理`[]`長さ 0 の文字列として (`""`)。 使用することができます`[]`文字列全体の式が空では、文字列式で特定の位置が空かどうかを使用することはできないかどうかをテストします。 空の位置が、オプションのいずれかである場合は、テストするには、使用できる必要があります。 `Like` 2 回以上。  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>文字または文字の一覧に対して、文字列式での文字と一致するには  
  
1.  呼び出す、`Like`演算子を 2 回に同じ文字列式、および 2 つの呼び出しのいずれかで接続、[または演算子](../../../../visual-basic/language-reference/operators/or-operator.md)または[OrElse 演算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)します。  
  
2.  最初のパターン文字列に`Like`句では、角かっこで囲まれた、文字の一覧が含まれます (`[ ]`)。  
  
3.  2 つ目のパターン文字列内`Like`句では、配置しない任意の文字位置にある問題です。  
  
     次の例は、7 桁の電話番号をテスト`phoneNum`の 3 桁の数字の後にスペース、ハイフン (`–`)、ピリオド (`.`)、または文字、後ろにないに 4 桁の数値。  
  
     [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]  
  
## <a name="see-also"></a>関連項目
- [比較演算子](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [演算子および式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Like 演算子](../../../../visual-basic/language-reference/operators/like-operator.md)
- [String データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)
