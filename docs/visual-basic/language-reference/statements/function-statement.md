---
title: Function ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 3a6184164fdc6f2517caf45f7b5e1455c9299666
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754727"
---
# <a name="function-statement-visual-basic"></a>Function ステートメント (Visual Basic)

宣言名、パラメーター、および定義するコードを`Function`プロシージャ。

## <a name="syntax"></a>構文

```
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a>指定項目

- `attributelist`

  省略可能です。 参照してください[属性リスト](attribute-list.md)します。

- `accessmodifier`

  任意。 次のいずれかの値を指定します。

  - [Public](../../../visual-basic/language-reference/modifiers/public.md)

  - [Protected](../../../visual-basic/language-reference/modifiers/protected.md)

  - [Friend](../../../visual-basic/language-reference/modifiers/friend.md)

  - [Private](../../../visual-basic/language-reference/modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  「 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。

- `proceduremodifiers`

  省略可能です。 次のいずれかの値を指定します。

  - [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  省略可能です。 参照してください[共有](../../../visual-basic/language-reference/modifiers/shared.md)します。

- `Shadows`

  省略可能です。 参照してください[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)します。

- `Async`

  省略可能です。 参照してください[Async](../../../visual-basic/language-reference/modifiers/async.md)します。

- `Iterator`

  省略可能です。 参照してください[反復子](../../../visual-basic/language-reference/modifiers/iterator.md)します。

- `name`

  必須。 プロシージャの名前。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。

- `typeparamlist`

  省略可能です。 ジェネリック プロシージャの型パラメーターの一覧。 参照してください[一覧を入力する](type-list.md)します。

- `parameterlist`

  省略可能です。 このプロシージャのパラメーターを表すローカル変数名の一覧。 参照してください[パラメーター リスト](parameter-list.md)します。

- `returntype`

  場合に、必ず`Option Strict`は`On`します。 このプロシージャによって返される値のデータ型。

- `Implements`

  省略可能です。 この手順が 1 つまたは複数を実装することを示します`Function`手順、この手順の包含クラスまたは構造体によって実装されるインターフェイスで定義されている 1 つずつです。 参照してください[ステートメントを実装](implements-statement.md)します。

- `implementslist`

  `Implements` を指定する場合は、必ず指定します。 実装される `Function` プロシージャのリストです。

  `implementedprocedure [ , implementedprocedure ... ]`

  `implementedprocedure` の構文と指定項目は次のとおりです。

  `interface.definedname`

  |パーツ|説明|
  |---|---|
  |`interface`|必須。 このプロシージャによって実装されるインターフェイスの名前を含むクラスまたは構造体。|
  |`definedname`|必須。 `interface` の中でプロシージャを定義するために使用する名前。|

- `Handles`

  省略可能です。 この手順が 1 つまたは複数の特定のイベントを処理できることを示します。 参照してください[処理](handles-clause.md)します。

- `eventlist`

  `Handles` を指定する場合は、必ず指定します。 このプロシージャを処理するイベントの一覧です。

  `eventspecifier [ , eventspecifier ... ]`

  `eventspecifier` の構文と指定項目は次のとおりです。

  `eventvariable.event`

  |パーツ|説明|
  |---|---|
  |`eventvariable`|必須。 オブジェクト変数がクラスまたはイベントを発生させる構造体のデータ型で宣言されています。|
  |`event`|必須。 このプロシージャを処理するイベントの名前。|

- `statements`

  省略可能です。 この手順内で実行されるステートメントのブロックです。

- `End Function`

  このプロシージャの定義を終了します。

## <a name="remarks"></a>Remarks

プロシージャ内にあるすべての実行可能コードがある必要があります。 さらに、各手順では、クラス、構造体またはクラス、構造体、またはモジュールとして参照されるモジュール内で宣言されます。

呼び出し元のコードに値を返すには使用、`Function`プロシージャです。 それ以外の場合、使用、`Sub`プロシージャ。

## <a name="defining-a-function"></a>関数を定義します。

定義することができます、`Function`モジュール レベルでのみプロシージャ。 そのため、関数の宣言のコンテキストでは、クラス、構造体、モジュールの場合、またはインターフェイスである必要があり、ソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。

`Function` パブリック アクセスに既定のプロシージャ。 アクセス修飾子を使用してこれらのアクセス レベルを調整できます。

A`Function`プロシージャがプロシージャが返す値のデータ型を宣言できます。 任意のデータ型または列挙型、構造体、クラスまたはインターフェイスの名前を指定することができます。 指定しない場合、`returntype`パラメーター、プロシージャを返します`Object`します。

この手順で使用する場合、`Implements`キーワードを含むクラスまたは構造体があります、`Implements`直後に続くステートメント、`Class`または`Structure`ステートメント。 `Implements`ステートメントで指定されている各インターフェイスを含める必要があります`implementslist`します。 ただし、インターフェイスを定義する名前、 `Function` (で`definedname`) この手順の名前と一致する必要はありません (で`name`)。

> [!NOTE]
> 関数をインライン式を定義するのにラムダ式を使用することができます。 詳細については、次を参照してください。[関数式](../../../visual-basic/language-reference/operators/function-expression.md)と[ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)します。

## <a name="returning-from-a-function"></a>関数から戻る

ときに、`Function`プロシージャを呼び出したステートメントに続くステートメントを使用して、プロシージャは、呼び出し元のコードに返す、実行が続行します。

関数から値を返す、関数名に値を割り当てるか、含めることで、`Return`ステートメント。

`Return`ステートメントは、同時に戻り値を割り当てるし、として次の例は、関数を終了します。

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

次の例では、関数名に、戻り値を割り当てて`myFunction`しを使用して、`Exit Function`ステートメントに戻ります。

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

`Exit Function`と`Return`ステートメントからすぐに終了が発生する、`Function`プロシージャ。 任意の数の`Exit Function`と`Return`ステートメントは、手順では、どこでも表示でき、組み合わせることができます`Exit Function`と`Return`ステートメント。

使用する場合`Exit Function`値を割り当てることがなく`name`、プロシージャがで指定されているデータ型の既定値を返します`returntype`します。 場合`returntype`が指定されていない、プロシージャが返す`Nothing`の既定値は`Object`します。

## <a name="calling-a-function"></a>関数の呼び出し

呼び出す、`Function`プロシージャ名、式の中で、かっこで囲まれた引数のリストを使用してプロシージャ。 任意の引数を指定していない場合にのみかっこを省略することができます。 ただし、コードが常にかっこが含まれる場合より読みやすいです。

呼び出す、`Function`プロシージャなどの任意のライブラリを呼び出すことと同じ方法関数`Sqrt`、 `Cos`、または`ChrW`します。

使用して関数を呼び出すことも、`Call`キーワード。 その場合は、戻り値は無視されます。 使用、`Call`キーワードはほとんどの場合にお勧めしません。 詳細については、次を参照してください。 [Call ステートメント](call-statement.md)します。

Visual Basic では、算術式内部の効率を向上させることがあります再配置します。 そのため、使用しないでください、`Function`算術式、関数には、同じ式内の変数の値が変更されたときの手順。

## <a name="async-functions"></a>非同期関数

*Async*機能は、明示的なコールバックの使用や複数の関数またはラムダ式、コードを手動で分割せず、非同期関数を呼び出すことができます。

持つ関数をマークする場合、 [Async](../../../visual-basic/language-reference/modifiers/async.md)修飾子を使用できます、 [Await](../../../visual-basic/language-reference/operators/await-operator.md)関数に演算子。 コントロールに達すると、`Await`内の式、`Async`関数は、呼び出し元に制御が戻ります、関数の進行状況が待機中のタスクが完了するまで中断されます。 タスクが完了したら、関数の実行を再開できます。

> [!NOTE]
> `Async`がまだ完了していない最初の待機中のオブジェクトを検出するかとに、プロシージャが、呼び出し元に返すまたはの末尾に達して、`Async`プロシージャか早い方です。

`Async`関数の戻り値の型を持つことができます<xref:System.Threading.Tasks.Task%601>または<xref:System.Threading.Tasks.Task>します。 例、`Async`関数の戻り値の型を持つ<xref:System.Threading.Tasks.Task%601>以下に示します。

`Async`関数を宣言できません[ByRef](../../../visual-basic/language-reference/modifiers/byref.md)パラメーター。

A [Sub ステートメント](sub-statement.md)でもマークされることができます、`Async`修飾子。 これは主に使用、イベント ハンドラーの値を返すことができません。 `Async` `Sub`プロシージャを待機することはできませんし、呼び出し元の`Async``Sub`プロシージャによってスローされる例外をキャッチできません、`Sub`プロシージャ。

詳細については`Async`関数を参照してください[Async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)、[非同期プログラムにおける制御フロー](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)、および[Async 戻り値の型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="iterator-functions"></a>反復子関数

*反復子*関数は、リストや配列など、コレクションに対するカスタム イテレーションを実行します。 反復子関数を使用して、 [Yield](yield-statement.md)ステートメントを一度に 1 つの各要素を返します。 ときに、 [Yield](yield-statement.md)ステートメントに達すると、コード内の現在の場所が記憶されます。 次回、iterator 関数が呼び出されると、この位置から実行が再開されます。

使用して、クライアント コードから反復子を呼び出す、[For Each...Next](for-each-next-statement.md)ステートメント。

反復子関数の戻り値の型は、 <xref:System.Collections.IEnumerable>、 <xref:System.Collections.Generic.IEnumerable%601>、 <xref:System.Collections.IEnumerator>、または<xref:System.Collections.Generic.IEnumerator%601>します。

詳細については、「 [反復子](../../programming-guide/concepts/iterators.md)」を参照してください。

## <a name="example"></a>例

次の例では、`Function`宣言名、パラメーター、およびコードの本体を形成するステートメントを`Function`プロシージャ。 `ParamArray`修飾子により、可変個の引数を受け入れるように機能します。

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a>例

次の例では、前の例で宣言された関数を呼び出します。

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a>例

次の例では、`DelayAsync`は、 `Async` `Function`の戻り値の型を持つ<xref:System.Threading.Tasks.Task%601>します。 `DelayAsync` には、整数を返す `Return` ステートメントがあります。 そのため、関数の宣言の`DelayAsync`の戻り値の型を指定する必要があります`Task(Of Integer)`します。 戻り値の型である`Task(Of Integer)`の評価、`Await`式`DoSomethingAsync`整数が生成されます。 これはこのステートメントで示されています:`Dim result As Integer = Await delayTask`します。

`startButton_Click`プロシージャの例に示します、`Async Sub`プロシージャ。 `DoSomethingAsync`は、`Async`関数では、タスクへの呼び出しを`DoSomethingAsync`、次のステートメントに示す待機する必要があります:`Await DoSomethingAsync()`します。 `startButton_Click` `Sub`でプロシージャを定義する必要があります、`Async`修飾子があるため、`Await`式。

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>関連項目

- [Sub ステートメント](sub-statement.md)
- [Function プロシージャ](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [パラメーター リスト](parameter-list.md)
- [Dim ステートメント](dim-statement.md)
- [Call ステートメント](call-statement.md)
- [Of](of-clause.md)
- [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [方法: ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [プロシージャのトラブルシューティング](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [ラムダ式](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [Function 式](../../../visual-basic/language-reference/operators/function-expression.md)
