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
ms.openlocfilehash: 65fcd10521742e287c7934080b3352a06668df7a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58835558"
---
# <a name="special-characters-in-code-visual-basic"></a>コード内の特殊文字 (Visual Basic)
アルファベットまたは数字ではない文字をコードでは、特殊文字を使用するがある場合があります。 区切り記号および Visual Basic の文字セット内の特殊文字は、コンパイラやコンパイル済みプログラムを実行するタスクの定義をプログラム テキストの整理から、さまざまな用途があります。 実行するオペレーションを指定するのには使用されません。  
  
## <a name="parentheses"></a>かっこ  
 など、プロシージャを定義するときに、かっこを使用して、`Sub`または`Function`します。 すべてのプロシージャの引数リストをかっこで囲んでください。 複雑な式で演算子の優先順位の既定の順序を上書きするには、特に論理グループは、変数または引数を配置するかっこを使用します。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#11)]  
  
 次のコードでは、値の実行`d`8.225 しの値は、`e`は 3 です。 計算`d`の既定の優先順位を使用して`/`経由で`+`と等価`d = b + (c / a)`します。 計算にかっこ`e`既定の優先順位をオーバーライドします。  
  
## <a name="separators"></a>[区切り記号]  
 区切り記号はその名前が示す: コードのセクションを区切ります。 Visual basic での区切り記号はコロン (`:`)。 別の行ではなく 1 つの行に複数のステートメントを追加する場合は、区切り記号を使用します。 これは、領域を節約し、コードの読みやすさが向上します。 次の例では、コロンで区切られた 3 つのステートメントを示します。  
  
 [!code-vb[VbVbcnConventions#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#12)]  
  
 詳細については、「[方法 :分割および連結コード内でステートメント](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)します。  
  
 コロン (`:`) 文字は、ステートメント ラベルを識別するためにも使用します。 詳細については、「[方法 :ステートメントにラベル付け](../../../visual-basic/programming-guide/program-structure/how-to-label-statements.md)します。  
  
## <a name="concatenation"></a>連結  
 使用して、`&`演算子*連結*、または文字列を一緒にリンクします。 混同しないでください、`+`演算子で、数値を加算します。 使用する場合、`+`数値の値を操作するときに連結する演算子が正しくない結果を取得することができます。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#13)]  
  
 次のコードでは、値の実行`resultA`21.01 しの値は、 `resultB` 「10.0111」です。  
  
## <a name="member-access-operators"></a>メンバー アクセス演算子  
 型のメンバーにアクセスするには、ドットを使用 (`.`)、または感嘆符 (`!`)、型名とメンバー名の間の演算子。  
  
### <a name="dot--operator"></a>ドット (.)演算子  
 使用して、`.`クラス、構造体、インターフェイス、または列挙体のメンバー アクセス演算子としての演算子。 メンバーは、フィールド、プロパティ、イベント、またはメソッドにできます。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#14)]  
  
### <a name="exclamation-point--operator"></a>感嘆符 (!)演算子  
 使用して、`!`ディクショナリ アクセス演算子としてクラスまたはインターフェイスでのみ演算子。 クラスまたはインターフェイスが既定のプロパティを 1 つを受け入れる必要`String`引数。 直後に続く識別子、`!`演算子に既定のプロパティを文字列として渡される引数値になります。 次に例を示します。  
  
 [!code-vb[VbVbcnConventions#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#15)]  
  
 3 つの出力行の`MsgBox`値を表示すべて`32856`します。 最初の行がプロパティには、従来のアクセスを使用して`index`、2 番目のという事実を利用する`index`クラスの既定のプロパティは、 `hasDefault`、し、3 番目のクラスへのディクショナリを使用して。  
  
 なお、2 番目のオペランドの`!`演算子は二重引用符で囲まれていない有効な Visual Basic 識別子である必要があります (`" "`)。 つまり、リテラル文字列または文字列変数を使用することはできません。 次の行を最後の変更、`MsgBox`ための呼び出しにエラーが生成されます`"X"`は、囲まれた文字列リテラル。  
  
 `"Dictionary access returns " & hD!"X")`  
  
> [!NOTE]
>  既定のコレクションへの参照を明示的にする必要があります。 具体的には、使用することはできません、`!`演算子に対して遅延バインディングされた変数。  
  
 `!`としても使用される文字、`Single`文字を入力します。  
  
## <a name="see-also"></a>関連項目

- [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [型文字](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
