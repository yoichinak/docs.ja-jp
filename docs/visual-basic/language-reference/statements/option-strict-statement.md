---
title: Option Strict Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Strict
- vb.OptionStrict
helpviewer_keywords:
- Strict keyword [Visual Basic]
- Option Strict statement [Visual Basic]
- conversions [Visual Basic], implicit
- late binding [Visual Basic]
- implicit conversions [Visual Basic]
ms.assetid: 5883e0c1-a920-4274-8e46-b0ff047eaee5
ms.openlocfilehash: a002526a107fdc6e8e02890d11db94a3d224c94b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353758"
---
# <a name="option-strict-statement"></a>Option Strict Statement
Restricts implicit data type conversions to only widening conversions, disallows late binding, and disallows implicit typing that results in an `Object` type.  
  
## <a name="syntax"></a>構文  
  
```vb  
Option Strict { On | Off }  
```  
  
## <a name="parts"></a>指定項目  
  
|用語|定義|  
|---|---|  
|`On`|省略可能です。 Enables `Option Strict` checking.|  
|`Off`|省略可能です。 Disables `Option Strict` checking.|  
  
## <a name="remarks"></a>Remarks  
 When `Option Strict On` or `Option Strict` appears in a file, the following conditions cause a compile-time error:  
  
- 暗黙的な縮小変換  
  
- 遅延バインディング  
  
- 結果が `Object` 型となる暗黙の型指定  
  
> [!NOTE]
> In the warning configurations that you can set on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic), there are three settings that correspond to the three conditions that cause a compile-time error. For information about how to use these settings, see [To set warning configurations in the IDE](../../../visual-basic/language-reference/statements/option-strict-statement.md#conditions) later in this topic.  
  
 The `Option Strict Off` statement turns off error and warning checking for all three conditions, even if the associated IDE settings specify to turn on these errors or warnings. The `Option Strict On` statement turns on error and warning checking for all three conditions, even if the associated IDE settings specify to turn off these errors or warnings.  
  
 If used, the `Option Strict` statement must appear before any other code statements in a file.  
  
 When you set `Option Strict` to `On`, Visual Basic checks that data types are specified for all programming elements. Data types can be specified explicitly, or specified by using local type inference. Specifying data types for all your programming elements is recommended, for the following reasons:  
  
- It enables IntelliSense support for your variables and parameters. This enables you to see their properties and other members as you type code.  
  
- It enables the compiler to perform type checking. Type checking helps you find statements that can fail at run time because of type conversion errors. It also identifies calls to methods on objects that do not support those methods.  
  
- It speeds up the execution of code. One reason for this is that if you do not specify a data type for a programming element, the Visual Basic compiler assigns it the `Object` type. Compiled code might have to convert back and forth between `Object` and other data types, which reduces performance.  
  
## <a name="implicit-narrowing-conversion-errors"></a>Implicit Narrowing Conversion Errors  
 縮小変換する暗黙的なデータ型変換がある場合は、暗黙的な縮小変換エラーが発生します。  
  
 Visual Basic can convert many data types to other data types. Data loss can occur when the value of one data type is converted to a data type that has less precision or a smaller capacity. A run-time error occurs if such a narrowing conversion fails. `Option Strict` ensures compile-time notification of these narrowing conversions so that you can avoid them. For more information, see [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md) and [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).  
  
 Conversions that can cause errors include implicit conversions that occur in expressions. 詳細については、以下のトピックを参照してください。  
  
- [+ 演算子](../../../visual-basic/language-reference/operators/addition-operator.md)  
  
- [+= 演算子](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
  
- [\ Operator (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
  
- [/= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
  
- [Char データ型](../../../visual-basic/language-reference/data-types/char-data-type.md)  
  
 When you concatenate strings by using the [& Operator](../../../visual-basic/language-reference/operators/concatenation-operator.md), all conversions to the strings are considered to be widening. So these conversions do not generate an implicit narrowing conversion error, even if `Option Strict` is on.  
  
 When you call a method that has an argument that has a data type different from the corresponding parameter, a narrowing conversion causes a compile-time error if `Option Strict` is on. You can avoid the compile-time error by using a widening conversion or an explicit conversion.  
  
 Implicit narrowing conversion errors are suppressed at compile-time for conversions from the elements in a `For Each…Next` collection to the loop control variable. This occurs even if `Option Strict` is on. For more information, see the "Narrowing Conversions" section in [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).  
  
## <a name="late-binding-errors"></a>Late Binding Errors  
 `Object` 型として宣言された変数のプロパティまたはメソッドにオブジェクトを代入する場合は、そのオブジェクトは遅延バインディングされます。 For more information, see [Early and Late Binding](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md).  
  
## <a name="implicit-object-type-errors"></a>Implicit Object Type Errors  
 適切な型が宣言された変数を推論できない場合は暗黙的なオブジェクトの型エラーが発生するため、`Object` の型が推論されます。 これは主に、`As` 句を使用せず、`Option Infer` をオフにして、`Dim` ステートメントを使用して変数を宣言した場合に発生します。 For more information, see [Option Infer Statement](../../../visual-basic/language-reference/statements/option-infer-statement.md) and the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).  
  
 For method parameters, the `As` clause is optional if `Option Strict` is off. However, if any one parameter uses an `As` clause, they all must use it. If `Option Strict` is on, the `As` clause is required for every parameter definition.  
  
 If you declare a variable without using an `As` clause and set it to `Nothing`, the variable has a type of `Object`. No compile-time error occurs in this case when `Option Strict` is on and `Option Infer` is on. An example of this is `Dim something = Nothing`.  
  
### <a name="default-data-types-and-values"></a>既定のデータ型と値  
 The following table describes the results of various combinations of specifying the data type and initializer in a [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
|データ型が指定されているか|初期化子が指定されているか|例|結果|  
|---|---|---|---|  
|Ｘ|Ｘ|`Dim qty`|`Option Strict` がオフ (既定値) の場合、変数は `Nothing` に設定されます。<br /><br /> `Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|Ｘ|[はい]|`Dim qty = 5`|`Option Infer` がオン (既定値) の場合、変数は初期化子のデータ型になります。 See [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).<br /><br /> `Option Infer` がオフで、`Option Strict` がオフの場合、変数は `Object` のデータ型になります。<br /><br /> `Option Infer` がオフで、`Option Strict` がオンの場合、コンパイル時エラーが発生します。|  
|[はい]|Ｘ|`Dim qty As Integer`|変数は、データ型の既定値に初期化されます。 For more information, see [Dim Statement](../../../visual-basic/language-reference/statements/dim-statement.md).|  
|[はい]|[はい]|`Dim qty  As Integer = 5`|初期化子のデータ型を指定したデータ型に変換できない場合は、コンパイル時エラーが発生します。|  
  
## <a name="when-an-option-strict-statement-is-not-present"></a>When an Option Strict Statement Is Not Present  
 If the source code does not contain an `Option Strict` statement, the **Option strict** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used. The **Compile Page** has settings that provide additional control over the conditions that generate an error.  
  
 If you are using the command-line compiler, you can use the [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option to specify a setting for `Option Strict`.  
  
### <a name="to-set-option-strict-in-the-ide"></a>To set Option Strict in the IDE  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
1. **ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。  
  
2. On the **Compile** tab, set the value in the **Option Strict** box.  
  
### <a name="conditions"></a> To set warning configurations in the IDE  
 When you use the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) instead of an `Option Strict` statement, you have additional control over the conditions that generate errors. The **Warning configurations** section of the **Compile Page** has settings that correspond to the three conditions that cause a compile-time error when `Option Strict` is on. これらの設定を次に示します。  
  
- **暗黙的な変換**  
  
- **遅延バインディング、呼び出しが実行時に失敗する可能性があります**  
  
- **暗黙的な型、オブジェクトと見なされます**  
  
 **[Option Strict]** を **[オン]** に設定すると、これら 3 つの警告の構成設定のすべてが **[エラー]** に設定されます。 **[Option Strict]** を **[オフ]** に設定すると、3 つの設定すべてが **[なし]** に設定されます。  
  
 各警告の構成設定を個別に **[なし]** 、 **[警告]** 、または **[エラー]** に変更することができます。 3 つの警告の構成設定がすべて **[エラー]** に設定されている場合、`Option strict` ボックスに `On` が表示されます。 3 つすべてが **[なし]** に設定されている場合、このボックスには `Off` が表示されます。 これらの設定のその他の組み合わせに対しては、 **(カスタム)** が表示されます。  
  
### <a name="to-set-the-option-strict-default-setting-for-new-projects"></a>To set the Option Strict default setting for new projects  
 When you create a project, the **Option Strict** setting on the **Compile** tab is set to the **Option Strict** setting in the **Options** dialog box.  
  
 To set `Option Strict` in this dialog box, on the **Tools** menu, click **Options**. **[オプション]** ダイアログ ボックスの **[プロジェクトおよびソリューション]** を展開し、 **[VISUAL BASIC の既定値]** をクリックします。 The initial default setting in **VB Defaults** is `Off`.  
  
### <a name="to-set-option-strict-on-the-command-line"></a>To set Option Strict on the command line  
 Include the [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md) compiler option in the **vbc** command.  
  
## <a name="example"></a>例  
 The following examples demonstrate compile-time errors caused by implicit type conversions that are narrowing conversions. This category of errors corresponds to the **Implicit conversion** condition on the **Compile Page**.  
  
 [!code-vb[VbVbalrStatements#161](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#161)]  
  
## <a name="example"></a>例  
 The following example demonstrates a compile-time error caused by late binding. This category of errors corresponds to the **Late binding; call could fail at run time** condition on the **Compile Page**.  
  
 [!code-vb[VbVbalrStatements#162](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#162)]  
  
## <a name="example"></a>例  
 The following examples demonstrate errors caused by variables that are declared with an implicit type of `Object`. This category of errors corresponds to the **Implicit type; object assumed** condition on the **Compile Page**.  
  
 [!code-vb[VbVbalrStatements#163](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#163)]  
  
 [!code-vb[VbVbalrStatements#164](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class13.vb#164)]  
  
## <a name="see-also"></a>関連項目

- [拡大変換と縮小変換](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [暗黙の型変換と明示的な型変換](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [[コンパイル] ページ、プロジェクト デザイナー (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
- [Option Explicit ステートメント](../../../visual-basic/language-reference/statements/option-explicit-statement.md)
- [データ型変換関数](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [方法: オブジェクトのメンバーにアクセスする](../../../visual-basic/programming-guide/language-features/variables/how-to-access-members-of-an-object.md)
- [XML での埋め込み式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [厳密でないデリゲート変換](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Office ソリューションの遅延バインディング](/visualstudio/vsto/late-binding-in-office-solutions)
- [-optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [[Visual Basic の既定値] ([オプション] ダイアログ ボックス - [プロジェクト])](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
