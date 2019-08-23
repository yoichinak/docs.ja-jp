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
ms.openlocfilehash: 59559f8775a5fd66a567897b009272df1727b1e8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953331"
---
# <a name="local-type-inference-visual-basic"></a>ローカル型の推論 (Visual Basic)
Visual Basic コンパイラは、*型の推定*を使用して、句を`As`使用せずに宣言されたローカル変数のデータ型を決定します。 コンパイラは、初期化式の型から変数の型を推測します。 これにより、次の例に示すように、明示的に型を指定せずに変数を宣言できます。 宣言の結果として、と`num1` `num2`の両方が整数として厳密に型指定されます。  
  
 [!code-vb[VbVbalrTypeInference#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#1)]  
 
> [!NOTE]
> 前の例を`Integer`として型指定しない場合は、または`Dim num4 As Double = 3`のような`Dim num3 As Object = 3`宣言を使用して別の型を指定できます。 `num2`  

> [!NOTE]
> 型の推定は、非静的ローカル変数に対してのみ使用できます。クラスフィールド、プロパティ、または関数の型を判断するために使用することはできません。
 
 ローカル型の推論はプロシージャレベルで適用されます。 モジュールレベルで変数を宣言するために使用することはできません (クラス、構造体、モジュール、またはインターフェイス内で、プロシージャまたはブロック内には含まれません)。 `Object` `Option Strict` `num2`前の例`Option Strict`では、プロシージャのローカル変数ではなく、クラスのフィールドを宣言すると、on のでエラーが発生し、が off のとして分類されます。 `num2` 同様に、ローカル型の推定は、として`Static`宣言されたプロシージャレベルの変数には適用されません。  
  
## <a name="type-inference-vs-late-binding"></a>型の推論と遅延バインディング  
 型の推定を使用するコードは、遅延バインディングに依存するコードに似ています。 ただし、型の推定では、変数はとして`Object`保持されるのではなく、厳密に型になります。 コンパイラは、コンパイル時に変数の初期化子を使用して、事前バインディングされたコードを生成します。 前の例`num2`では、の`num1`ように、がと`Integer`して型指定されています。  
  
 事前バインディングされた変数の動作は、遅延バインディングされた変数の動作とは異なり、型は実行時にのみ認識されます。 型を早期に把握すると、コンパイラは実行前に問題を特定し、メモリを正確に割り当て、その他の最適化を実行できます。 また、事前バインディングを使用すると、Visual Basic 統合開発環境 (IDE) で、オブジェクトのメンバーに関する IntelliSense のヘルプを提供することもできます。 事前バインディングは、パフォーマンスのためにも推奨されます。 これは、遅延バインディング変数に格納されているすべてのデータが型`Object`としてラップされる必要があり、実行時にその型のメンバーにアクセスするとプログラムの速度が低下するためです。  
  
## <a name="examples"></a>使用例  
 型の推定は、ローカル変数が`As`句なしで宣言され、初期化されるときに発生します。 コンパイラは、割り当てられた初期値の型を変数の型として使用します。 たとえば、次のコード行はそれぞれ、型`String`の変数を宣言しています。  
  
 [!code-vb[VbVbalrTypeInference#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#2)]  
  
 次のコードは、整数の配列を作成する2つの同等の方法を示しています。  
  
 [!code-vb[VbVbalrTypeInference#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#3)]  
  
 型の推定を使用して、ループコントロール変数の型を決定すると便利です。 次のコードで`number` `Integer`は、前の例からは整数`someNumbers2`の配列であるため、コンパイラはがであると推論します。  
  
 [!code-vb[VbVbalrTypeInference#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#4)]  
  
 次の例に示すように`Using` 、ローカル型の推定は、リソース名の型を設定するステートメントで使用できます。  
  
 [!code-vb[VbVbalrTypeInference#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#7)]  
  
 変数の型は、次の例に示すように、関数の戻り値から推論することもできます。 とは、プロセスの配列を`Process.GetProcesses`返すため、プロセスの配列です。 `pList2` `pList1`  
  
 [!code-vb[VbVbalrTypeInference#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTypeInference/VB/Class1.vb#5)]  
  
## <a name="option-infer"></a>オプションの推論  
 `Option Infer`ローカル型推論が特定のファイルで許可されるかどうかを指定できます。 オプションを有効または禁止するには、ファイルの先頭に次のいずれかのステートメントを入力します。  
  
 `Option Infer On`  
  
 `Option Infer Off`  
  
 コードでの`Option Infer`値を指定しない場合、コンパイラの既定値は`Option Infer On`になります。 
  
 ファイルの `Option Infer` に設定した値が IDE またはコマンド ラインに設定した値と競合した場合は、ファイルの値が優先されます。  
  
 詳細については、[[オプションの推論ステートメント]](../../../../visual-basic/language-reference/statements/option-infer-statement.md)と [[コンパイル] ページ (プロジェクトデザイナー) (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)を参照してください。  
  
## <a name="see-also"></a>関連項目

- [匿名型](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
- [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
- [For Each...Next ステートメント](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)
- [For...Next ステートメント](../../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Option Infer ステートメント](../../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [/optioninfer](../../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Visual Basic における LINQ の概要](../../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
