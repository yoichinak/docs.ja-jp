---
title: プロシージャのトラブルシューティング (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting Visual Basic, procedures
- procedures [Visual Basic], troubleshooting
- Visual Basic code, procedures
- troubleshooting procedures
- procedures [Visual Basic], about procedures
ms.assetid: 525721e8-2e02-4f75-b5d8-6b893462cf2b
ms.openlocfilehash: 492a7474a38a7e41b7e3b3f59dfa118c30256ea4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "58830137"
---
# <a name="troubleshooting-procedures-visual-basic"></a>プロシージャのトラブルシューティング (Visual Basic)
このページには、プロシージャを使用する場合に発生する可能性がある一般的な問題が一覧表示されます。  
  
## <a name="returning-an-array-type-from-a-function-procedure"></a>Function プロシージャから配列型を返す  
 場合、`Function`配列のデータ型を返し、使用することはできません、`Function`配列の要素の値を格納する名前。 これを実行しようとした場合、コンパイラによってへの呼び出し、`Function`します。 次の例では、コンパイラ エラーを生成します。  
  
 `Function allOnes(ByVal n As Integer) As Integer()`  
  
 `For i As Integer = 1 To n - 1`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `allOnes(i) = 1`  
  
 `Next i`  
  
 `' The following statement generates a`   `COMPILER ERROR`  `.`  
  
 `Return allOnes()`  
  
 `End Function`  
  
 ステートメント`allOnes(i) = 1`を呼び出す可能性があるため、コンパイラ エラーが発生`allOnes`で正しくないデータ型の引数 (シングルトン`Integer`の代わりに、`Integer`配列)。 ステートメント`Return allOnes()`を呼び出す可能性があるため、コンパイラ エラーが発生`allOnes`引数。  
  
 **正しいアプローチは:** 返される配列の要素を変更できるようにするには、ローカル変数として、内部配列を定義します。 次の例では、コンパイル エラーが発生します。  
  
 [!code-vb[VbVbcnProcedures#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#66)]  
  
## <a name="argument-not-being-modified-by-procedure-call"></a>引数は変更されていないプロシージャ コールによって  
 呼び出し元のコードで引数を基になるプログラミング要素を変更するプロシージャを許可する場合は、参照渡しで渡す必要があります。 値を値によって渡す場合でも、プロシージャが参照型の引数の要素をアクセスできます。  
  
-   **変数を基になる**します。 基になる変数要素自体の値を変更する手順は、プロシージャが、パラメーターを宣言する必要があります[ByRef](../../../../visual-basic/language-reference/modifiers/byref.md)します。 また、呼び出し元のコードいない引数は、かっこで囲んでくださいを上書きするため、`ByRef`メカニズムを渡します。  
  
-   **参照型の要素の**します。 パラメーターを宣言する場合[ByVal](../../../../visual-basic/language-reference/modifiers/byval.md)プロシージャは、基になる変数要素自体を変更できません。 ただし、引数が参照型の場合、変数の値を置き換えることができない場合でも、プロシージャは、ポイントをするには、オブジェクトのメンバー変更できます。 たとえば、引数が、配列変数の場合は、プロシージャは、新しい配列を割り当てることはできませんが、1 つまたは複数の要素を変更することができます。 変更された要素は、呼び出し元のコードで、基になる配列変数に反映されます。  
  
 次の例では、その要素を値で配列変数を受け取り、操作される 2 つの手順を定義します。 プロシージャ`increase`単に各要素に 1 つ追加します。 プロシージャ`replace`パラメーターに新しい配列を割り当てます`a()`し、各要素に 1 つを追加します。 ただし、再割り当てには影響しません、呼び出し元のコードで、基になる配列変数のため`a()`が宣言されている`ByVal`します。  
  
 [!code-vb[VbVbcnProcedures#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#35)]  
  
 [!code-vb[VbVbcnProcedures#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#38)]  
  
 次の例での呼び出しを`increase`と`replace`します。  
  
 [!code-vb[VbVbcnProcedures#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#37)]  
  
 最初の`MsgBox`呼び出しが表示されます"increase(n) 後。11, 21, 31, 41". `n` 、参照型では、`increase`渡される場合でも、そのメンバーを変更することができます`ByVal`します。  
  
 2 番目の`MsgBox`呼び出しが表示されます"目後。11, 21, 31, 41". `n`が渡される`ByVal`、`replace`変数を変更することはできません`n`を新しい配列を割り当てることで。 ときに`replace`新しい配列インスタンスを作成します`k`し、ローカル変数に代入`a`への参照が失われた`n`呼び出し元のコードで渡されます。 メンバーをインクリメントすると`a`、ローカルの配列のみ`k`が影響を受けます。  
  
 **正しいアプローチは:** 基になる変数要素自体を変更するには、参照によって渡します。 次の例では、変更を示しますの宣言で`replace`を呼び出し元のコードの別の 1 つの配列を置き換えるようになります。  
  
 [!code-vb[VbVbcnProcedures#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#64)]  
  
## <a name="unable-to-define-an-overload"></a>オーバー ロードを定義することができません。  
 プロシージャのオーバー ロードされたバージョンを定義する場合は、異なるシグネチャが同じ名前を使用する必要があります。 コンパイラは、同じシグネチャを持つオーバー ロードから宣言を区別することはできません、エラーが生成されます。  
  
 *署名*プロシージャのプロシージャ名とパラメーター リストによって決定されます。 各オーバー ロードは、同じ名前の他のすべてのオーバー ロードがありますが、署名の他のコンポーネントの少なくとも 1 つにそれらのすべての異なる必要があります。 詳細については、「 [Procedure Overloading](./procedure-overloading.md)」を参照してください。  
  
 次の項目に関連するパラメーターのリストもないプロシージャの署名のコンポーネント。  
  
-   プロシージャ修飾子キーワードなど`Public`、`Shared`と `Static`  
  
-   パラメーター名  
  
-   パラメーター修飾子キーワードなど`ByRef`と `Optional`  
  
-   (変換演算子) を除く、戻り値のデータ型  
  
 上記の項目の 1 つ以上のみ、プロシージャをオーバー ロードすることはできません。  
  
 **正しいアプローチは:** プロシージャのオーバー ロードを定義できるようにするには、するには、署名を変更する必要があります。 同じ名前を使用する必要があります、ために、数、順序、またはパラメーターのデータ型を変更しなければなりません。 ジェネリック プロシージャでは、型パラメーターの数を変更できます。 変換演算子で ([CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md))、戻り値の型を変えることができます。  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>オーバー ロード解決でオプションおよび ParamArray 引数  
 1 つまたは複数のプロシージャをオーバー ロードは場合[(省略可能)](../../../../visual-basic/language-reference/modifiers/optional.md)パラメーターまたは[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)パラメーター、複製のいずれかの回避する必要があります、*暗黙のオーバー ロード*します。 詳しくは、次を参照してください。[プロシージャのオーバー ロードに関する考慮事項](./considerations-in-overloading-procedures.md)します。  
  
## <a name="calling-a-wrong-version-of-an-overloaded-procedure"></a>オーバー ロードされたプロシージャの間違ったバージョンの呼び出し  
 プロシージャにいくつかのオーバー ロードされたバージョンがある場合は、すべてのパラメーター リストを使い慣れて、Visual Basic での通話を複数のオーバー ロードの解決方法を理解してください。 それ以外の場合、意図したものと異なるオーバー ロードを呼び出すことができます。  
  
 どのオーバー ロードを呼び出そうとするを決定するときは、次の規則に従うように注意してください。  
  
-   引数、および正しい順序で、正しい数を指定します。  
  
-   理想的には、引数には、対応するパラメーターとして、まったく同じデータ型が必要です。 いずれの場合も、各引数のデータ型は、対応するパラメーターに拡大変換する必要があります。 これは、true を使用しても、 [Option Strict ステートメント](../../../../visual-basic/language-reference/statements/option-strict-statement.md)設定`Off`します。 オーバー ロードをオーバー ロードする引数リストから任意の縮小変換が必要な場合は、呼び出される対象ではありません。  
  
-   拡大変換が必要な引数を指定する場合は、対応するパラメーターのデータ型にできるだけ近いデータ型を確認します。 2 つ以上のオーバー ロードは引数のデータ型を受け入れる場合、コンパイラは、最小限の拡大を呼び出して取得するオーバー ロードへの呼び出しを解決します。  
  
 使用してデータ型の不一致の可能性を低くことができます、 [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)引数を指定するとき、変換キーワード。  
  
### <a name="overload-resolution-failure"></a>オーバー ロードの解決エラー  
 オーバー ロードされたプロシージャを呼び出すと、コンパイラは、オーバー ロードの 1 つだけを削除しようとします。 成功すると、そのオーバー ロードの呼び出しを解決します。 すべてのオーバー ロードを排除または、オーバー ロードの 1 つの候補を減らすことができない場合は、エラーを生成します。  
  
 次の例は、オーバー ロードの解決プロセスを示しています。  
  
 [!code-vb[VbVbcnProcedures#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#62)]  
  
 [!code-vb[VbVbcnProcedures#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#63)]  
  
 ため、最初の呼び出しで、コンパイラが最初のオーバー ロードを排除最初の引数の型 (`Short`) と対応するパラメーターの型へ縮小変換 (`Byte`)。 次に除去 3 番目のオーバー ロードは、2 番目のオーバー ロードに各引数を入力 (`Short`と`Single`) 3 番目のオーバー ロードでは、対応する型に拡大変換されます (`Integer`と`Single`)。 2 番目のオーバー ロードが必要な拡大が少ないので、コンパイラは、呼び出しの使用します。  
  
 2 番目の呼び出しでは、コンパイラは縮小に基づいてオーバー ロードのいずれかを取り除くことはできません。 以下の引数の型の拡大と 2 番目のオーバー ロードを呼び出すことができますので、同じ理由で最初の呼び出しのように、3 番目のオーバー ロードを除外します。 ただし、コンパイラは、最初と 2 番目のオーバー ロードの解決できません。 それぞれが、それ以外の対応する型を拡張する 1 つの定義されているパラメーターの型 (`Byte`に`Short`が`Single`に`Double`)。 そのため、コンパイラは、オーバー ロードの解決エラーを生成します。  
  
 **正しいアプローチは:** あいまいさがないオーバー ロードされたプロシージャを呼び出すには、次のように使用します。 [CType Function](../../../../visual-basic/language-reference/functions/ctype-function.md)パラメーターの型に引数のデータ型と一致します。 次の例では、呼び出しを`z`を強制的に 2 つ目のオーバー ロードに解決します。  
  
 [!code-vb[VbVbcnProcedures#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#65)]  
  
### <a name="overload-resolution-with-optional-and-paramarray-arguments"></a>オーバー ロード解決でオプションおよび ParamArray 引数  
 最後のパラメーターを宣言する点を除いて、プロシージャの 2 つのオーバー ロードが同じシグネチャを持つ場合[(省略可能)](../../../../visual-basic/language-reference/modifiers/optional.md)で 1 つと[ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)コンパイラがそのプロシージャの呼び出しを解決して、その他に従って、最も近い一致します。 詳細については、「 [Overload Resolution](./overload-resolution.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [プロシージャ](./index.md)
- [Sub プロシージャ](./sub-procedures.md)
- [Function プロシージャ](./function-procedures.md)
- [Property プロシージャ](./property-procedures.md)
- [演算子プロシージャ](./operator-procedures.md)
- [プロシージャのパラメーターと引数](./procedure-parameters-and-arguments.md)
- [プロシージャのオーバーロード](./procedure-overloading.md)
- [プロシージャのオーバーロードに関する注意事項](./considerations-in-overloading-procedures.md)
- [オーバーロードの解決](./overload-resolution.md)
