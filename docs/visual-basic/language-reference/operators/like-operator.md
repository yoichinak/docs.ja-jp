---
title: Like 演算子 (Visual Basic)
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
ms.openlocfilehash: f26cadc4f64626f2a79eb37352f4906cea9092bb
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979930"
---
# <a name="like-operator-visual-basic"></a>Like 演算子 (Visual Basic)
文字列をパターンと比較します。  

> [!IMPORTANT]
> `Like`演算子が .NET Core と .NET Standard プロジェクトでサポートされていません現在します。

## <a name="syntax"></a>構文  
  
```  
result = string Like pattern  
```  
  
## <a name="parts"></a>指定項目  
 `result`  
 必須。 すべて`Boolean`変数。 結果は、`Boolean`を示す値かどうか、`string`を満たす、`pattern`します。  
  
 `string`  
 必須。 任意のブール型 ( `String` ) の式を指定します。  
  
 `pattern`  
 必須。 すべて`String`「解説」で説明されているパターン一致規則に準拠している式。  
  
## <a name="remarks"></a>Remarks  
 場合の値`string`がパターンに含まれるを満たす`pattern`、`result`は`True`します。 文字列がパターンを満たさない場合`result`は`False`します。 両方`string`と`pattern`空の文字列には、結果は`True`します。  
  
## <a name="comparison-method"></a>比較メソッド  
 動作、`Like`演算子によって異なります、 [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)します。 各ソース ファイルの既定の文字列比較メソッドは`Option Compare Binary`します。  
  
## <a name="pattern-options"></a>パターンのオプション  
 組み込みのパターンに一致する文字列比較での多用途のツールを提供します。 内の各文字に一致することは、パターン マッチング機能`string`に対して特定の文字、ワイルドカード文字、文字のリスト、または文字の範囲。 次の表で使用できる文字`pattern`一致したとします。  
  
|内の文字 `pattern`|内の一致 `string`|  
|-----------------------------|-------------------------|  
|`?`|任意の 1 文字|  
|`*`|0 個以上の文字|  
|`#`|任意の 1 つの数字 (0 ~ 9)|  
|`[charlist]`|任意の 1 文字 `charlist`|  
|`[!charlist]`|内にない任意の 1 文字 `charlist`|  
  
## <a name="character-lists"></a>文字の一覧  
 1 つまたは複数の文字グループ (`charlist`) 角かっこで囲む (`[ ]`) 内の任意の 1 文字を一致させることができます`string`桁の数字を含む、ほぼすべての文字コードを含めることができます。  
  
 感嘆符 (`!`) の先頭に`charlist`内の文字を除く任意の文字の場合、一致が行われたことを意味`charlist`は`string`します。 角かっこの外側を使用する場合、感嘆符自体と一致します。  
  
## <a name="special-characters"></a>特殊文字  
 特殊文字の左角かっこの一致するように (`[`)、疑問符 (`?`)、シャープ記号 (`#`)、およびアスタリスク (`*`)、角かっこで囲みます。 右の角かっこ (`]`) 自体には、一致するように、グループ内で使用できませんが、グループ外で個別の文字として使用することができます。  
  
 文字シーケンス`[]`長さ 0 の文字列と見なされます (`""`)。 ただし、角かっこで囲まれた文字の一覧の一部にすることはできません。 内の位置かどうかを確認したい場合`string`1 つ含まれる使用できる一連の文字または文字の`Like`2 回です。 例については、「[方法: 文字列をパターンに一致](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)します。  
  
## <a name="character-ranges"></a>文字範囲  
 ハイフンを使用して (`–`) と、範囲の上限を設定する`charlist`文字の範囲を指定できます。 たとえば、`[A–Z]`結果と一致する場合は、対応する文字の位置で`string`範囲内の任意の文字が含まれています`A`–`Z`、および`[!H–L]`結果と一致する場合は、対応する文字の位置範囲外の任意の文字を含む`H`–`L`します。  
  
 文字の範囲を指定すると、昇順には、並べ替え順を昇順で現れる必要があります。 したがって、`[A–Z]`は有効なパターンが`[Z–A]`はありません。  
  
### <a name="multiple-character-ranges"></a>複数の文字範囲  
 同じ文字の位置に複数の範囲を指定するには、区切り記号は同じ角かっこ内に配置します。 たとえば、`[A–CX–Z]`結果と一致する場合は、対応する文字の位置で`string`いずれかの範囲内の任意の文字が含まれています`A`–`C`または範囲`X`–`Z`します。  
  
### <a name="usage-of-the-hyphen"></a>ハイフンの使用  
 ハイフン (`–`) (後に感嘆符、存在する場合) の先頭にあるかの最後に表示できる`charlist`自体を一致するようにします。 その他の任意の場所では、ハイフンは、ハイフンの両側の文字が区切り文字の範囲を識別します。  
  
## <a name="collating-sequence"></a>照合順序  
 指定した範囲の意味は、文字によって決定される、実行時に順序によって異なります。 `Option Compare` 、システムのロケール設定で、コードが実行されているとします。 `Option Compare Binary`、範囲`[A–E]`と一致する`A`、 `B`、 `C`、 `D`、および`E`します。 `Option Compare Text`、`[A–E]`と一致する`A`、 `a`、 `À`、 `à`、 `B`、 `b`、 `C`、 `c`、 `D`、 `d`、 `E`、および`e`します。 範囲と一致しません`Ê`または`ê`並べ替え順序でアクセントのない文字にアクセント記号付き文字を照合します。  
  
## <a name="digraph-characters"></a>Digraph 文字  
 一部の言語を表す 2 つの文字の英字があります。 たとえば、複数の言語が文字を使用して`æ`の文字を表す`a`と`e`まとめて表示されます。 `Like`演算子認識は、1 つ digraph 文字と 2 つの個別の文字を同等です。  
  
 Digraph 文字を使用する言語がシステムのロケール設定で指定した場合、いずれかで 1 つ digraph 文字のオカレンス`pattern`または`string`他の文字列で同等の 2 文字シーケンスと一致します。 同様に、digraph 文字`pattern`角かっこで囲む (単独で、リスト、または範囲内) で同等の 2 文字のシーケンスと一致`string`します。  
  
## <a name="overloading"></a>オーバーロード  
 `Like`演算子は、*オーバー ロードされた*、つまり、ことクラスまたは構造体を再定義できますその動作はそのクラスまたは構造体の型。 コードは、このようなクラスまたは構造体に、この演算子を使用する場合は、再定義された動作を確認ください。 詳細については、「 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)」を参照してください。  
  
## <a name="example"></a>例  
 この例では、`Like`をさまざまなパターン文字列を比較する演算子。 移動し、結果を`Boolean`各文字列がパターンを満たすかどうかを示す変数。  
  
 [!code-vb[VbVbalrOperators#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#30)]  
  
## <a name="see-also"></a>関連項目
- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [比較演算子](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Visual Basic における演算子の優先順位](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [機能別の演算子一覧](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Option Compare ステートメント](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [演算子および式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [方法: 文字列をパターンに一致します。](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-match-a-string-against-a-pattern.md)
