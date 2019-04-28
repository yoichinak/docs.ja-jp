---
title: Sub ステートメント (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: ab94865f4881b40b38f67eb40d2f9fa2e1982af8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783839"
---
# <a name="sub-statement-visual-basic"></a>Sub ステートメント (Visual Basic)

宣言名、パラメーター、および定義するコードを`Sub`プロシージャ。

## <a name="syntax"></a>構文

```
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a>指定項目

- `attributelist`

  省略可能です。 参照してください[属性リスト](attribute-list.md)します。

- `Partial`

  省略可能です。 部分メソッドの定義を示します。 参照してください[部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)します。

- `accessmodifier`

  省略可能です。 次のいずれかの値を指定します。

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  「 [Visual Basic でのアクセス レベル](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。

- `proceduremodifiers`

  省略可能です。 次のいずれかの値を指定します。

  - [Overloads](../modifiers/overloads.md)

  - [Overrides](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [MustOverride](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  省略可能です。 参照してください[共有](../modifiers/shared.md)します。

- `Shadows`

  省略可能です。 参照してください[Shadows](../modifiers/shadows.md)します。

- `Async`

  省略可能です。 参照してください[Async](../modifiers/async.md)します。

- `name`

  必須。 プロシージャの名前。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。 クラスのコンス トラクターのプロシージャを作成するには、設定の名前、`Sub`する手順、`New`キーワード。 詳細については、次を参照してください。[オブジェクトの有効期間。オブジェクトの作成し、破棄方法](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)します。

- `typeparamlist`

  省略可能です。 ジェネリック プロシージャの型パラメーターの一覧。 参照してください[一覧を入力する](type-list.md)します。

- `parameterlist`

  省略可能です。 このプロシージャのパラメーターを表すローカル変数名の一覧。 参照してください[パラメーター リスト](parameter-list.md)します。

- `Implements`

  省略可能です。 この手順が 1 つまたは複数を実装することを示します`Sub`手順、この手順の包含クラスまたは構造体によって実装されるインターフェイスで定義されている 1 つずつです。 参照してください[ステートメントを実装](implements-statement.md)します。

- `implementslist`

  `Implements` を指定する場合は、必ず指定します。 実装される `Sub` プロシージャのリストです。

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

  省略可能です。 このプロシージャ内で実行するステートメントのブロック。

- `End Sub`

  このプロシージャの定義を終了します。

## <a name="remarks"></a>Remarks

プロシージャ内にあるすべての実行可能コードがある必要があります。 使用して、`Sub`呼び出し元のコードに値を返すしたくない場合、プロシージャ。 使用して、`Function`値を取得する場合のプロシージャです。

## <a name="defining-a-sub-procedure"></a>Sub プロシージャの定義

定義することができます、`Sub`モジュール レベルでのみプロシージャ。 Sub プロシージャの宣言のコンテキストでは、クラス、構造体、モジュールの場合、またはインターフェイスにする必要があります、そのため、およびソース ファイル、名前空間、プロシージャ、またはブロックすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。

`Sub` パブリック アクセスに既定のプロシージャ。 アクセス修飾子を使用して、そのアクセス レベルを調整できます。

プロシージャで使用する場合、`Implements`キーワードを含むクラスまたは構造体があります、`Implements`直後に続くステートメント、`Class`または`Structure`ステートメント。 `Implements`ステートメントで指定されている各インターフェイスを含める必要があります`implementslist`します。 ただし、インターフェイスを定義する名前、 `Sub` (で`definedname`) この手順の名前と一致する必要はありません (で`name`)。

## <a name="returning-from-a-sub-procedure"></a>Sub プロシージャから戻る

ときに、`Sub`ステートメントを呼び出した後のステートメントと、プロシージャは、呼び出し元のコードに返す、実行が継続します。

次の例からの戻り値を示しています、`Sub`プロシージャ。

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

`Exit Sub`と`Return`ステートメントからすぐに終了が発生する、`Sub`プロシージャ。 任意の数の`Exit Sub`と`Return`ステートメントは、手順では、どこでも表示でき、組み合わせることができます`Exit Sub`と`Return`ステートメント。

## <a name="calling-a-sub-procedure"></a>Sub プロシージャの呼び出し

呼び出す、`Sub`ステートメントでは、プロシージャ名を使用し、その引数リストをかっこで使用してその名前でプロシージャ。 引数を指定しない場合にのみかっこを省略することができます。 ただし、コードが常にかっこが含まれる場合より読みやすいです。

A`Sub`プロシージャと`Function`プロシージャがパラメーターを指定して、一連のステートメントを実行します。 ただし、`Function`値、およびプロシージャを返します。`Sub`プロシージャがありません。 そのため、使用することはできません、`Sub`式の中でプロシージャ。

使用することができます、`Call`を呼び出すときに、キーワード、`Sub`プロシージャが、そのキーワードが、ほとんどの用途についてはお勧めしません。 詳細については、次を参照してください。 [Call ステートメント](call-statement.md)します。

Visual Basic では、算術式内部の効率を向上させることがあります再配置します。 そのため、引数リストには、他のプロシージャを呼び出す式が含まれている場合とは考えないでくださいの式が特定の順序で呼び出されることです。

## <a name="async-sub-procedures"></a>Async Sub プロシージャ

非同期機能を使用すると、明示的なコールバックの使用や複数の関数またはラムダ式、コードを手動で分割することがなく非同期関数を呼び出すことができます。

プロシージャを設定する場合、 [Async](../modifiers/async.md)修飾子を使用できます、 [Await](../../../visual-basic/language-reference/operators/await-operator.md)プロシージャ内の演算子。 コントロールに達すると、`Await`内の式、`Async`プロシージャは、呼び出し元に制御が戻ります、待機中のタスクが完了するまでの手順で進行状況が中断されます。 タスクが完了したら、プロシージャの実行を再開できます。

> [!NOTE]
> `Async`プロシージャ行末またはか最初待機中のオブジェクトはまだ完了が発生した場合、呼び出し元に返す、`Async`プロシージャに達すると、どちらが最初に発生します。

マークすることも、[関数ステートメント](function-statement.md)で、`Async`修飾子。 `Async`関数の戻り値の型を持つことができます<xref:System.Threading.Tasks.Task%601>または<xref:System.Threading.Tasks.Task>します。 たとえば後でこのトピックでは、`Async`関数の戻り値の型を持つ<xref:System.Threading.Tasks.Task%601>します。

`Async` `Sub` プロシージャは、主に、値を返すことができない、イベント ハンドラーを使用します。 `Async` `Sub`プロシージャを待機できません、呼び出し元の`Async``Sub`プロシージャは、例外をキャッチできませんが、`Sub`プロシージャがスローされます。

`Async`プロシージャは、いずれかを宣言できません[ByRef](../modifiers/byref.md)パラメーター。

詳細については`Async`手順についてを参照してください[Async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)、[非同期プログラムにおける制御フロー](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)、および[Async 戻り値の型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

## <a name="example"></a>例

次の例では、`Sub`名、パラメーター、およびの本体を形成するコードを定義するステートメントを`Sub`プロシージャ。

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a>例

次の例では、`DelayAsync`は、 `Async` `Function`の戻り値の型を持つ<xref:System.Threading.Tasks.Task%601>します。 `DelayAsync` には、整数を返す `Return` ステートメントがあります。 したがって、関数宣言の`DelayAsync`の戻り値の型があります。`Task(Of Integer)`します。 戻り値の型である`Task(Of Integer)`の評価、`Await`式`DoSomethingAsync`として次のステートメントに示す、整数が生成されます:`Dim result As Integer = Await delayTask`します。

`startButton_Click`プロシージャの例に示します、`Async Sub`プロシージャ。 `DoSomethingAsync`は、`Async`関数では、タスクへの呼び出しを`DoSomethingAsync`として次のステートメントの表示を待機する必要があります:`Await DoSomethingAsync()`します。 `startButton_Click` `Sub`でプロシージャを定義する必要があります、`Async`修飾子があるため、`Await`式。

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>関連項目

- [Implements ステートメント](implements-statement.md)
- [Function ステートメント](function-statement.md)
- [パラメーター リスト](parameter-list.md)
- [Dim ステートメント](dim-statement.md)
- [Call ステートメント](call-statement.md)
- [Of](of-clause.md)
- [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [方法: ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [プロシージャのトラブルシューティング](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
