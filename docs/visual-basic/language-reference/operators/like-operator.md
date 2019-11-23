---
title: Like 演算子
ms.date: 07/20/2015
f1_keywords:
- Like
- vb.Like
helpviewer_keywords:
- similar to
- pattern matching
- Like operator [Visual Basic]
- '? symbol, wildcard character'
- string comparison [Visual Basic], Like operator
- strings [Visual Basic], comparing
- comparison operators [Visual Basic]
- symbols, wildcard
- wildcards, Like operator
- strings [Visual Basic], matching
- string comparison [Visual Basic], sorting data
- data [Visual Basic], sorting
- text [Visual Basic], comparing
- operators [Visual Basic], pattern-matching
- data [Visual Basic], string comparisons
- string comparison [Visual Basic], Like operators
ms.assetid: 966283ec-80e2-4294-baa8-c75baff804f9
ms.openlocfilehash: 5db9488bbec716156a3ab464042c0853241a82b1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350946"
---
# <a name="like-operator-visual-basic"></a>Like 演算子 (Visual Basic)
Compares a string against a pattern.  

> [!IMPORTANT]
> The `Like` operator is currently not supported in .NET Core and .NET Standard projects.

## <a name="syntax"></a>構文  
  
```vb  
result = string Like pattern  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須です。 Any `Boolean` variable. The result is a `Boolean` value indicating whether or not the `string` satisfies the `pattern`.  
  
 `string`  
 必須です。 任意のブール型 ( `String` ) の式を指定します。  
  
 `pattern`  
 必須です。 Any `String` expression conforming to the pattern-matching conventions described in "Remarks."  
  
## <a name="remarks"></a>Remarks  
 If the value in `string` satisfies the pattern contained in `pattern`, `result` is `True`. If the string does not satisfy the pattern, `result` is `False`. If both `string` and `pattern` are empty strings, the result is `True`.  
  
## <a name="comparison-method"></a>Comparison Method  
 The behavior of the `Like` operator depends on the [Option Compare Statement](../../../visual-basic/language-reference/statements/option-compare-statement.md). The default string comparison method for each source file is `Option Compare Binary`.  
  
## <a name="pattern-options"></a>Pattern Options  
 Built-in pattern matching provides a versatile tool for string comparisons. The pattern-matching features allow you to match each character in `string` against a specific character, a wildcard character, a character list, or a character range. The following table shows the characters allowed in `pattern` and what they match.  
  
|Characters in `pattern`|Matches in `string`|  
|-----------------------------|-------------------------|  
|`?`|任意の 1 文字|  
|`*`|Zero or more characters|  
|`#`|Any single digit (0–9)|  
|`[charlist]`|Any single character in `charlist`|  
|`[!charlist]`|Any single character not in `charlist`|  
  
## <a name="character-lists"></a>Character Lists  
 A group of one or more characters (`charlist`) enclosed in brackets (`[ ]`) can be used to match any single character in `string` and can include almost any character code, including digits.  
  
 An exclamation point (`!`) at the beginning of `charlist` means that a match is made if any character except the characters in `charlist` is found in `string`. When used outside brackets, the exclamation point matches itself.  
  
## <a name="special-characters"></a>特殊文字  
 To match the special characters left bracket (`[`), question mark (`?`), number sign (`#`), and asterisk (`*`), enclose them in brackets. The right bracket (`]`) cannot be used within a group to match itself, but it can be used outside a group as an individual character.  
  
 The character sequence `[]` is considered a zero-length string (`""`). However, it cannot be part of a character list enclosed in brackets. If you want to check whether a position in `string` contains one of a group of characters or no character at all, you can use `Like` twice. For an example, see [How to: Match a String against a Pattern](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md).  
  
## <a name="character-ranges"></a>Character Ranges  
 By using a hyphen (`–`) to separate the lower and upper bounds of the range, `charlist` can specify a range of characters. For example, `[A–Z]` results in a match if the corresponding character position in `string` contains any character within the range `A`–`Z`, and `[!H–L]` results in a match if the corresponding character position contains any character outside the range `H`–`L`.  
  
 When you specify a range of characters, they must appear in ascending sort order, that is, from lowest to highest. Thus, `[A–Z]` is a valid pattern, but `[Z–A]` is not.  
  
### <a name="multiple-character-ranges"></a>Multiple Character Ranges  
 To specify multiple ranges for the same character position, put them within the same brackets without delimiters. For example, `[A–CX–Z]` results in a match if the corresponding character position in `string` contains any character within either the range `A`–`C` or the range `X`–`Z`.  
  
### <a name="usage-of-the-hyphen"></a>Usage of the Hyphen  
 A hyphen (`–`) can appear either at the beginning (after an exclamation point, if any) or at the end of `charlist` to match itself. In any other location, the hyphen identifies a range of characters delimited by the characters on either side of the hyphen.  
  
## <a name="collating-sequence"></a>Collating Sequence  
 The meaning of a specified range depends on the character ordering at run time, as determined by `Option Compare` and the locale setting of the system the code is running on. With `Option Compare Binary`, the range `[A–E]` matches `A`, `B`, `C`, `D`, and `E`. With `Option Compare Text`, `[A–E]` matches `A`, `a`, `À`, `à`, `B`, `b`, `C`, `c`, `D`, `d`, `E`, and `e`. The range does not match `Ê` or `ê` because accented characters collate after unaccented characters in the sort order.  
  
## <a name="digraph-characters"></a>Digraph Characters  
 In some languages, there are alphabetic characters that represent two separate characters. For example, several languages use the character `æ` to represent the characters `a` and `e` when they appear together. The `Like` operator recognizes that the single digraph character and the two individual characters are equivalent.  
  
 When a language that uses a digraph character is specified in the system locale settings, an occurrence of the single digraph character in either `pattern` or `string` matches the equivalent two-character sequence in the other string. Similarly, a digraph character in `pattern` enclosed in brackets (by itself, in a list, or in a range) matches the equivalent two-character sequence in `string`.  
  
## <a name="overloading"></a>オーバーロード  
 The `Like` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure. If your code uses this operator on such a class or structure, be sure you understand its redefined behavior. 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 This example uses the `Like` operator to compare strings to various patterns. The results go into a `Boolean` variable indicating whether each string satisfies the pattern.  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [方法 : 文字列がパターンに一致するかを調べる](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
