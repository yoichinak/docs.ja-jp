---
title: コード内の特殊文字 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.)
- vb.(
- vb.colon
- vb.!
- vb..
- 'vb.:'
helpviewer_keywords:
- special characters [Visual Basic], in code
- parentheses [Visual Basic], using in code
- colons (:)
- period character in code
- dot operator (.)
- dictionary access operator [Visual Basic]
- concatenation operators [Visual Basic], special characters in code
- concatenation operators [Visual Basic], vs. addition operator
- '! operator'
- separators [Visual Basic], using in code
- operators [Visual Basic], dictionary access
- ': separator character'
- member access operator [Visual Basic]
- addition operator [Visual Basic]
- operators [Visual Basic], member access
- . operator
- exclamation points
- separators
- exclamation point operator (!)
- Visual Basic code, special characters
ms.assetid: 310dce0c-45b5-4e0d-83e9-32df258d2a3e
ms.openlocfilehash: 95bef937912e35cd828bf0090b4cf48ccb3290cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962474"
---
# <a name="special-characters-in-code-visual-basic"></a>コード内の特殊文字 (Visual Basic)
場合によっては、コードで特殊文字を使用する必要があります。つまり、アルファベットまたは数字以外の文字を使用する必要があります。 Visual Basic 文字セットの句読点と特殊文字には、プログラムテキストの整理から、コンパイラまたはコンパイル済みプログラムによって実行されるタスクの定義まで、さまざまな用途があります。 実行するオペレーションを指定するのには使用されません。  
  
## <a name="parentheses"></a>内側  
 やなどの`Sub`プロシージャを定義するときは`Function`、かっこを使用します。 すべてのプロシージャ引数リストをかっこで囲む必要があります。 また、変数または引数を論理グループに含めるためにかっこを使用します。特に、複合式での演算子の優先順位の既定の順序をオーバーライドします。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 前のコードの実行後、の`d`値は8.225 で、の`e`値は3です。 の`d`計算では、 `+`の既定の`/`優先順位が使用さ`d = b + (c / a)`れます。これはと同じです。 の`e`計算のかっこは、既定の優先順位よりも優先されます。  
  
## <a name="separators"></a>[区切り記号]  
 区切り記号は、コードのセクションを分離します。 Visual Basic では、区切り文字はコロン (`:`) です。 複数のステートメントを別々の行ではなく1行に含める場合は、区切り記号を使用します。 これにより、領域が節約され、コードの読みやすさが向上します。 次の例では、コロンで区切られた3つのステートメントを示します。  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 詳細については、「[方法 :コード](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)内のステートメントを分割し、結合します。  
  
 コロン (`:`) 文字は、ステートメントラベルを識別するためにも使用されます。 詳細については、「[方法 :ラベルステートメント](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)。  
  
## <a name="concatenation"></a>連結  
 *連結に*は演算子を使用し、文字列を連結するにはを使用し`&`ます。 数値を加算する`+`演算子と混同しないようにしてください。 数値を操作する`+`ときに演算子を使用して連結すると、不適切な結果を得ることができます。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 前のコードの実行後、の`resultA`値は21.01 で、の`resultB`値は "10.0111" です。  
  
## <a name="member-access-operators"></a>メンバーアクセス演算子  
 型のメンバーにアクセスするには、型名とメンバー`.`名の間にドット`!`() または感嘆符 () 演算子を使用します。  
  
### <a name="dot--operator"></a>ドット (.)演算子  
 メンバーアクセス演算子として、クラス、構造体、インターフェイス、または列挙体に対して演算子を使用します。`.` メンバーには、フィールド、プロパティ、イベント、またはメソッドを指定できます。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>感嘆符 (!)演算子  
 演算子は`!` 、クラスまたはインターフェイスでのみ、ディクショナリアクセス演算子として使用します。 クラスまたはインターフェイスには、1つ`String`の引数を受け取る既定のプロパティが必要です。 演算子の`!`直後にある識別子は、既定のプロパティに文字列として渡される引数の値になります。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 すべてのの3つ`MsgBox`の出力行に`32856`値が表示されます。 最初の行では、プロパティ`index`への従来のアクセスを使用します。2番目の行では、クラス`hasDefault`の既定のプロパティである`index`ファクトを使用し、3番目の行ではクラスへのディクショナリアクセスを使用します。  
  
 `!`演算子の2番目のオペランドは、二重引用符 (`" "`) で囲まれていない有効な Visual Basic 識別子である必要があることに注意してください。 つまり、文字列リテラルまたは文字列変数を使用することはできません。 `MsgBox`呼び出しの最後の行に次の変更を行うと、は`"X"`囲まれた文字列リテラルであるため、エラーが生成されます。  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
> 既定のコレクションへの参照は明示的に指定する必要があります。 特に、遅延バインディング変数に`!`対して演算子を使用することはできません。  
  
 文字は、 `Single`型文字としても使用されます。 `!`  
  
## <a name="see-also"></a>関連項目

- [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [型文字](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
