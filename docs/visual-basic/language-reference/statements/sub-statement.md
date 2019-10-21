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
ms.openlocfilehash: 7dc0ea1f1b30f5ffb0db8917538adf440c5ef891
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583201"
---
# <a name="sub-statement-visual-basic"></a>Sub ステートメント (Visual Basic)

@No__t_0 プロシージャを定義する名前、パラメーター、およびコードを宣言します。

## <a name="syntax"></a>構文

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a>指定項目

- `attributelist`

  省略可能です。 「[属性リスト](attribute-list.md)」を参照してください。

- `Partial`

  省略可能です。 部分メソッドの定義を示します。 「[部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)」を参照してください。

- `accessmodifier`

  省略可能です。 次のいずれかの値を指定します。

  - [Public](../modifiers/public.md)

  - [Protected](../modifiers/protected.md)

  - [Friend](../modifiers/friend.md)

  - [Private](../modifiers/private.md)

  - [Protected Friend](../../language-reference/modifiers/protected-friend.md)

  - [Private Protected](../../language-reference/modifiers/private-protected.md)

  「 [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)」を参照してください。

- `proceduremodifiers`

  省略可能です。 次のいずれかの値を指定します。

  - [オーバーロード](../modifiers/overloads.md)

  - [Overrides](../modifiers/overrides.md)

  - [Overridable](../modifiers/overridable.md)

  - [NotOverridable](../modifiers/notoverridable.md)

  - [New](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  省略可能です。 「[共有](../modifiers/shared.md)」を参照してください。

- `Shadows`

  省略可能です。 「[シャドウ](../modifiers/shadows.md)」を参照してください。

- `Async`

  省略可能です。 「 [Async](../modifiers/async.md)」を参照してください。

- `name`

  必須です。 プロシージャの名前。 「 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)」を参照してください。 クラスのコンストラクタープロシージャを作成するには、`Sub` プロシージャの名前を `New` キーワードに設定します。 詳細については、「[オブジェクトの有効期間: オブジェクトの作成方法と破棄方法](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)」を参照してください。

- `typeparamlist`

  省略可能です。 ジェネリックプロシージャの型パラメーターのリスト。 [型リスト](type-list.md)を参照してください。

- `parameterlist`

  省略可能です。 このプロシージャのパラメーターを表すローカル変数名の一覧。 「[パラメーターリスト](parameter-list.md)」を参照してください。

- `Implements`

  省略可能です。 このプロシージャが1つ以上の `Sub` プロシージャを実装することを示します。各プロシージャは、このプロシージャのクラスまたは構造体を含むインターフェイスで定義されています。 「 [Implements ステートメント](implements-statement.md)」を参照してください。

- `implementslist`

  `Implements` を指定する場合は、必ず指定します。 実装される `Sub` プロシージャのリストです。

  `implementedprocedure [ , implementedprocedure ... ]`

  `implementedprocedure` の構文と指定項目は次のとおりです。

  `interface.definedname`

  |パーツ|説明|
  |---|---|
  |`interface`|必須です。 このプロシージャのクラスまたは構造体によって実装されるインターフェイスの名前。|
  |`definedname`|必須です。 `interface` の中でプロシージャを定義するために使用する名前。|

- `Handles`

  省略可能です。 このプロシージャが1つ以上の特定のイベントを処理できることを示します。 「[ハンドル](handles-clause.md)」を参照してください。

- `eventlist`

  `Handles` を指定する場合は、必ず指定します。 このプロシージャが処理するイベントの一覧です。

  `eventspecifier [ , eventspecifier ... ]`

  `eventspecifier` の構文と指定項目は次のとおりです。

  `eventvariable.event`

  |パーツ|説明|
  |---|---|
  |`eventvariable`|必須です。 イベントを発生させるクラスまたは構造体のデータ型で宣言されたオブジェクト変数。|
  |`event`|必須です。 このプロシージャが処理するイベントの名前。|

- `statements`

  省略可能です。 このプロシージャ内で実行するステートメントのブロック。

- `End Sub`

  このプロシージャの定義を終了します。

## <a name="remarks"></a>Remarks

すべての実行可能コードは、プロシージャ内になければなりません。 呼び出し元のコードに値を返さないようにする場合は、`Sub` プロシージャを使用します。 値を返す場合は、`Function` プロシージャを使用します。

## <a name="defining-a-sub-procedure"></a>Sub プロシージャの定義

@No__t_0 プロシージャは、モジュールレベルでのみ定義できます。 したがって、サブプロシージャの宣言コンテキストは、クラス、構造体、モジュール、またはインターフェイスにする必要があり、ソースファイル、名前空間、プロシージャ、またはブロックにすることはできません。 詳細については、「[宣言コンテキストと既定のアクセス レベル](declaration-contexts-and-default-access-levels.md)」を参照してください。

`Sub` プロシージャは、既定でパブリックアクセスになります。 アクセス修飾子を使用して、アクセスレベルを調整できます。

プロシージャが `Implements` キーワードを使用している場合、含んでいるクラスまたは構造体には、その `Class` または `Structure` ステートメントの直後にある `Implements` ステートメントが含まれている必要があります。 @No__t_0 ステートメントには、`implementslist` で指定されている各インターフェイスを含める必要があります。 ただし、インターフェイスが `Sub` (`definedname`) を定義する際には、このプロシージャの名前 (`name`) と一致する必要はありません。

## <a name="returning-from-a-sub-procedure"></a>Sub プロシージャからの戻り

@No__t_0 プロシージャが呼び出し元のコードに戻ると、ステートメントを呼び出したステートメントの後のステートメントで実行が続行されます。

次の例は、`Sub` プロシージャからの戻り値を示しています。

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

@No__t_0 ステートメントおよび `Return` ステートメントを行うと、`Sub` プロシージャからすぐに終了します。 プロシージャ内の任意の場所で任意の数の `Exit Sub` および `Return` ステートメントを使用できます。また、`Exit Sub` と `Return` のステートメントを混在させることができます。

## <a name="calling-a-sub-procedure"></a>Sub プロシージャの呼び出し

@No__t_0 プロシージャを呼び出すには、ステートメントでプロシージャ名を使用し、その名前の後にかっこで囲んだ引数リストを指定します。 かっこを省略できるのは、引数を指定しない場合のみです。 ただし、常にかっこを含めると、コードが読みやすくなります。

@No__t_0 プロシージャと `Function` プロシージャは、パラメーターを持つことができ、一連のステートメントを実行できます。 ただし、`Function` プロシージャは値を返し、`Sub` プロシージャは返しません。 したがって、式の中で `Sub` プロシージャを使用することはできません。

@No__t_1 プロシージャを呼び出すときに `Call` キーワードを使用することはできますが、ほとんどの場合、そのキーワードは推奨されません。 詳細については、「 [Call ステートメント](call-statement.md)」を参照してください。

Visual Basic は、内部効率を向上させるために算術式を再配置することがあります。 そのため、引数リストに他のプロシージャを呼び出す式が含まれている場合は、それらの式が特定の順序で呼び出されると想定しないでください。

## <a name="async-sub-procedures"></a>非同期サブプロシージャ

非同期機能を使用すると、明示的なコールバックを使用したり、複数の関数やラムダ式にコードを手動で分割したりせずに、非同期関数を呼び出すことができます。

プロシージャに[Async](../modifiers/async.md)修飾子を指定した場合は、プロシージャで[Await](../../../visual-basic/language-reference/operators/await-operator.md)演算子を使用できます。 コントロールが `Async` プロシージャ内の `Await` 式に到達すると、コントロールは呼び出し元に戻り、待機中のタスクが完了するまで、プロシージャの進行状況は中断されます。 タスクが完了すると、プロシージャで実行を再開できます。

> [!NOTE]
> @No__t_0 プロシージャは、まだ完了していない最初の待機中のオブジェクトが検出された場合、または `Async` プロシージャの最後に到達した場合に、呼び出し元に戻ります。

[関数ステートメント](function-statement.md)を `Async` 修飾子でマークすることもできます。 @No__t_0 関数は、<xref:System.Threading.Tasks.Task%601> または <xref:System.Threading.Tasks.Task> の戻り値の型を持つことができます。 このトピックの後半の例では、<xref:System.Threading.Tasks.Task%601> の戻り値の型を持つ `Async` 関数を示します。

`Async` の `Sub` プロシージャは、主に、値を返すことができないイベントハンドラーに使用されます。 @No__t_0 `Sub` プロシージャは待機できません。また、`Async` の `Sub` プロシージャの呼び出し元は、`Sub` プロシージャがスローする例外をキャッチできません。

@No__t_0 プロシージャで[ByRef](../modifiers/byref.md)パラメーターを宣言することはできません。

@No__t_0 の手順の詳細については、「 [async および Await を使用した非同期プログラミング](../../../visual-basic/programming-guide/concepts/async/index.md)」、「非同期[プログラムでの制御フロー](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)」、および「非同期の[戻り値の型](../../../visual-basic/programming-guide/concepts/async/async-return-types.md)」を参照してください。

## <a name="example"></a>例

次の例では、`Sub` ステートメントを使用して、`Sub` プロシージャの本体を形成する名前、パラメーター、およびコードを定義します。

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a>例

次の例では、`DelayAsync` は、戻り値の型が <xref:System.Threading.Tasks.Task%601> の `Async` `Function` です。 `DelayAsync` には、整数を返す `Return` ステートメントがあります。 したがって、`DelayAsync` の関数宣言には、`Task(Of Integer)` の戻り値の型を指定する必要があります。 戻り値の型が `Task(Of Integer)` ので、次のステートメントに `Dim result As Integer = Await delayTask` 示すように、`DoSomethingAsync` で `Await` 式を評価すると整数が生成されます。

@No__t_0 プロシージャは、`Async Sub` プロシージャの一例です。 @No__t_0 は `Async` 関数であるため、次のステートメントに示すように、`DoSomethingAsync` を呼び出すためのタスクを待機する必要があります。 `Await DoSomethingAsync()`。 @No__t_0 `Sub` プロシージャには `Await` 式があるため、`Async` 修飾子を使用して定義する必要があります。

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a>関連項目

- [Implements ステートメント](implements-statement.md)
- [Function ステートメント](function-statement.md)
- [パラメーター リスト](parameter-list.md)
- [Dim ステートメント](dim-statement.md)
- [Call ステートメント](call-statement.md)
- [Of](of-clause.md)
- [パラメーター配列](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [方法 : ジェネリック クラスを使用する](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [プロシージャのトラブルシューティング](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [部分メソッド](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
