---
title: '方法: 文字列をパターンと照合する (Visual Basic)'
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
ms.openlocfilehash: 0bac0869d9e319071abb31dd0576edf0450aa198
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71054152"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>方法: 文字列をパターンと照合する (Visual Basic)

[文字列データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)の式がパターンを満たすかどうかを確認するには、 [Like 演算子](../../../../visual-basic/language-reference/operators/like-operator.md)を使用します。

`Like`2つのオペランドを受け取ります。 左オペランドは文字列式で、右オペランドは照合に使用されるパターンを含む文字列です。 `Like`文字列式がパターンを満たすかどうかを示す値を返します。`Boolean`

文字列式の各文字は、特定の文字、ワイルドカード文字、文字リスト、または文字範囲に対して一致させることができます。 パターン文字列内の仕様の位置は、文字列式で一致する文字の位置に対応します。

## <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>文字列式の文字を特定の文字に一致させるには

特定の文字をパターン文字列に直接配置します。 特定の特殊文字は、角かっこ (`[ ]`) で囲む必要があります。 詳細については、「 [Like 演算子](../../../../visual-basic/language-reference/operators/like-operator.md)」を参照してください。

次の例では`myString` 、が単一の文字`H`で構成されているかどうかをテストします。

[!code-vb[VbVbalrOperators#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#70)]

## <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>文字列式の文字をワイルドカード文字に一致させるには

パターン文字列に疑問符 (`?`) を入力します。 この位置にある有効な文字によって、一致が成功します。

次の例では`myString` 、が1つの`W`文字で構成され、その後に値が2文字続くかどうかをテストします。

[!code-vb[VbVbalrOperators#71](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#71)]

## <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>文字列式の文字を文字の一覧に一致させるには

パターン文字列に`[ ]`角かっこ () を挿入し、角かっこ内に文字のリストを配置します。 文字をコンマまたは他の区切り記号で区切ることは避けてください。 リスト内の任意の1文字が、一致と見なされます。

次の例では`myString` 、が有効な文字で構成され、 `C`、、 `A`または`E`のいずれかの文字が続くかどうかをテストします。

[!code-vb[VbVbalrOperators#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#72)]

この照合では大文字と小文字が区別されることに注意してください。

## <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>文字列式の文字を文字の範囲に一致させるには

パターン文字列に`[ ]`角かっこ () を挿入し、角かっこ内には、ハイフン (`–`) で区切られた範囲内の最低文字と最高文字を指定します。 範囲内の任意の1文字が、一致と見なされます。

次の例では`myString` 、が、、 `num` 、、 `m`、 `j` `l` `i`のいずれ`k`かの文字が続く文字で構成されているかどうかをテストします。`n`

[!code-vb[VbVbalrOperators#73](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#73)]

この照合では大文字と小文字が区別されることに注意してください。

## <a name="matching-empty-strings"></a>一致 (空の文字列を)

`Like`シーケンス`[]`を長さ0の文字列 (`""`) として扱います。 を使用`[]`すると、文字列式全体が空であるかどうかをテストできますが、文字列式内の特定の位置が空かどうかをテストすることはできません。 空の位置が、テストする必要があるオプションの1つである場合は`Like` 、を複数回使用できます。

### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>文字列式の文字を文字のリストまたは文字の一覧と一致させるには

1. 同じ文字列式で`Like` 演算子を2回呼び出し、[or演算子](../../../../visual-basic/language-reference/operators/or-operator.md)または[OrElse演算子](../../../../visual-basic/language-reference/operators/orelse-operator.md)のいずれかを使用して2つの呼び出しを接続します。

2. 最初`Like`の句のパターン文字列には、文字リストを角かっこ (`[ ]`) で囲んで指定します。

3. 2番目`Like`の句のパターン文字列では、対象の位置に文字を入れないでください。

    次の例では、正確に3桁`phoneNum`の電話番号をテストし、その後にスペース、ハイフン (`–`)、ピリオド (`.`)、または文字をまったく4桁の数字で指定します。

    [!code-vb[VbVbalrOperators#74](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#74)]

## <a name="see-also"></a>関連項目

- [比較演算子](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [演算子および式](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Like 演算子](../../../../visual-basic/language-reference/operators/like-operator.md)
- [String データ型](../../../../visual-basic/language-reference/data-types/string-data-type.md)
