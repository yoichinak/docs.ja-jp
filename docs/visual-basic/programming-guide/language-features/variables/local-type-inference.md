---
title: ローカル型の推論 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- local type inference
- vb.TypeInfer
helpviewer_keywords:
- Option Infer statement [Visual Basic]
- local type inference [Visual Basic]
- implicitly-typed local variables [Visual Basic]
- variables [Visual Basic], type inference
- inference [Visual Basic]
- type inference [Visual Basic]
ms.assetid: b8307f18-2e56-4ab3-a45a-826873f400f6
ms.openlocfilehash: e6214938262b987a1bae4a9ca1d5c945f8b7fe6e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052587"
---
# <a name="local-type-inference-visual-basic"></a>ローカル型の推論 (Visual Basic)
Visual Basic コンパイラを使用して*型推論*なしで宣言されたローカル変数のデータの種類を決定する、`As`句。 コンパイラでは、初期化式の型から変数の型を推測します。 これにより、次の例に示すように、型を明示的に指定せず変数を宣言することができます。 宣言では、結果として両方`num1`と`num2`整数として厳密に型指定します。  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
>  たくない場合`num2`として型指定するのには、前の例で、`Integer`のような宣言を使用して別の型を指定することができます`Dim num3 As Object = 3`または`Dim num4 As Double = 3`します。  

> [!NOTE]
>  型の推論は、非静的ローカル変数に対してのみ使用できます。これは、クラスのフィールド、プロパティ、または関数の種類の決定に使用できません。
 
 ローカル型推論は、プロシージャ レベルで適用されます。 (クラス、構造体、モジュール、またはインターフェイス内では、プロシージャまたはブロック内ではなく)、モジュール レベルで変数の宣言には使用できません。 場合`num2`前の例では、プロシージャでローカル変数の代わりに、クラスのフィールドは、宣言でエラーが発生すると`Option Strict`、および分類は`num2`として、`Object`で`Option Strict`オフします。 同様に、ローカル型推論に該当するプロシージャ レベルの変数として宣言されている`Static`します。  
  
## <a name="type-inference-vs-late-binding"></a>型の推論と遅延バインディング  
 コードでは、推論をタイプには、遅延バインディングに依存するコードに似ています。 ただし、型の推論型を厳密としてそのままではなく変数`Object`します。 コンパイラでは、変数の初期化子を使用して、事前バインディングされたコードを生成するために、コンパイル時に、変数の型を調べます。 前の例では、`num2`と同様に、 `num1`、として型指定された、`Integer`します。  
  
 事前バインディングされた変数の動作は、遅延バインディングされた変数は、対象の実行時にのみ、型が不明の動作とは異なります。 種類を事前に知ることにより、実行する前に問題を特定、正確には、メモリの割り当てし、その他の最適化を実行するコンパイラ。 事前バインディングは、Visual Basic の統合開発環境 (IDE) のオブジェクトのメンバーについて IntelliSense のヘルプを提供するようにできます。 事前バインディングは、パフォーマンスの推奨もあります。 これは、遅延バインディングされた変数に格納されているすべてのデータを型としてラップする必要があるため`Object`、低速のプログラムは、実行時に、型のメンバーにアクセスするとします。  
  
## <a name="examples"></a>使用例  
 型の推定が発生せず、ローカル変数が宣言されている場合、`As`句と初期化します。 コンパイラは、変数の型として割り当てられた初期値の型を使用します。 たとえば、型の変数を宣言次のコード行の各`String`します。  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 次のコードでは、整数の配列を作成する 2 つの同等の方法を示します。  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 ループ コントロール変数の種類を決定する型の推定を使用すると便利です。 次のコードでコンパイラが推論される`number`は、`Integer`ため`someNumbers2`前の例は、整数の配列。  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 ローカル型推論を使用できる`Using`ステートメントを次の例に示すように、リソースの名前の型を確立します。  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 次の例に示すように、変数の型を関数の戻り値から推論もできます。 両方`pList1`と`pList2`プロセスの配列であるため、`Process.GetProcesses`プロセスの配列を返します。  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a>Option Infer します。  
 `Option Infer` ローカル型推論が、特定のファイルで許可されているかどうかを指定できます。 有効または、オプションをブロックするファイルの先頭に次のステートメントのいずれかを入力します。  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 値を指定しない場合`Option Infer`コンパイラの既定値は、コードで、`Option Infer On`します。 アップグレードされたプロジェクトの[!INCLUDE[vb_orcas_long](~/includes/vb-orcas-long-md.md)]コンパイラの既定値は、前に、または`Option Infer Off`します。  
  
 ファイルの `Option Infer` に設定した値が IDE またはコマンド ラインに設定した値と競合した場合は、ファイルの値が優先されます。  
  
 詳細については、次を参照してください。 [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)と[[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)します。  
  
## <a name="see-also"></a>関連項目

- [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next ステートメント](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
