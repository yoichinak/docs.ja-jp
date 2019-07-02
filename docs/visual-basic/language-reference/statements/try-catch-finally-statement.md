---
title: お試しください.キャッチしてください.最後にステートメント - Visual Basic
description: Visual Basic Try、Catch、Finally ステートメントでの例外処理を使用することについて説明します。
ms.date: 12/07/2018
f1_keywords:
- vb.Try...Catch...Finally
- vb.when
- vb.Finally
- vb.Catch
- vb.Try
helpviewer_keywords:
- Try...Catch...Finally statements
- Try statement [Visual Basic]
- try-catch exception handling, Try...Catch...Finally statements
- error handling, while running code
- Try statement [Visual Basic], Try...Catch...Finally
- Finally keyword [Visual Basic], Try...Catch...Finally
- Catch statement [Visual Basic]
- When keyword [Visual Basic]
- Visual Basic code, handling errors while running
- structured exception handling, Try...Catch...Finally statements
ms.assetid: d6488026-ccb3-42b8-a810-0d97b9d6472b
ms.custom: seodec18
ms.openlocfilehash: 126f20c86bb47e8002382e069ce6236600394aba
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638773"
---
# <a name="trycatchfinally-statement-visual-basic"></a>Try...Catch...Finally ステートメント (Visual Basic)

コードの実行中に、コードの特定のブロックで発生する可能性があります一部またはすべての可能なエラーを処理する方法を提供します。

## <a name="syntax"></a>構文

```vb
Try
    [ tryStatements ]
    [ Exit Try ]
[ Catch [ exception [ As type ] ] [ When expression ]
    [ catchStatements ]
    [ Exit Try ] ]
[ Catch ... ]
[ Finally
    [ finallyStatements ] ]
End Try
```

## <a name="parts"></a>指定項目

|用語|定義|
|---|---|
|`tryStatements`|任意。 ステートメントは、エラーが発生できます。 複合ステートメントにすることもできます。|
|`Catch`|任意。 複数`Catch`ブロックを許可します。 処理するときに例外が発生した場合、`Try`ブロックする場合に、各`Catch`ステートメントがかどうかと、例外を処理するテキストの順序で調べられる`exception`がスローされた例外を表します。|
|`exception`|任意。 任意の変数名を指定します。 `exception` の初期値は、スローされたエラーの値です。 併用`Catch`キャッチ、エラーを指定します。 省略した場合は、`Catch`ステートメントはすべての例外をキャッチします。|
|`type`|任意。 クラスのフィルターの種類を指定します。 場合の値`exception`で指定された型の`type`か、派生型の識別子は、例外オブジェクトにバインドになります。|
|`When`|任意。 A`Catch`ステートメントを`When`句は例外をキャッチする場合にのみ`expression`に評価される`True`します。 A`When`句は、例外の種類を確認後にのみ適用されると`expression`が例外を表す識別子を参照してください。|
|`expression`|任意。 暗黙的に変換できる必要があります`Boolean`します。 汎用フィルターを記述する任意の式。 通常、エラー番号でフィルター処理に使用されます。 併用`When`エラーがキャッチされる状況を指定するキーワード。|
|`catchStatements`|任意。 関連付けられているで発生するエラーを処理するステートメント`Try`ブロックします。 複合ステートメントにすることもできます。|
|`Exit Try`|任意。 抜けキーワード、`Try...Catch...Finally`構造体。 すぐに次のコードで実行が再開される、`End Try`ステートメント。 `Finally`ステートメントが実行されます。 許可されていません`Finally`ブロックします。|
|`Finally`|任意。 A`Finally`ブロックは常に実行がの一部を離れるときに実行、`Try...Catch`ステートメント。|
|`finallyStatements`|任意。 他のすべてのエラー処理が行われた後に実行されるステートメントです。|
|`End Try`|終了、`Try...Catch...Finally`構造体。|

## <a name="remarks"></a>コメント

コードの特定のセクションで、特定の例外が発生することを期待する場合のコードを配置、`Try`をブロックし、使用、`Catch`コントロールを保持し、これが発生した場合、例外の処理をブロックします。

A`Try…Catch`ステートメントには、`Try`ブロックでは、1 つまたは複数続く`Catch`句で、さまざまな例外のハンドラーを指定します。 例外をスローするときに、`Try`ブロック、Visual Basic を検索、`Catch`例外を処理するステートメント。 一致する場合`Catch`ステートメントが見つからない場合は、Visual Basic は、コール スタックまで、現在のメソッドを呼び出したメソッドを調べます。 ない場合は`Catch`ブロックが見つかると、Visual Basic のユーザーにハンドルされない例外メッセージを表示およびプログラムの実行を停止します。

1 つ以上を使用することができます`Catch`内のステートメントを`Try…Catch`ステートメント。 この順序の場合、`Catch`句は重要では順序がチェックされるためです。 例外は、特殊性の高い順にキャッチしてください。

次`Catch`ステートメントの条件が少なくとも固有であり、キャッチ オールから派生した例外、<xref:System.Exception>クラス。 前回通常これらのバリエーションの 1 つ使用する必要があります`Catch`ブロック、`Try...Catch...Finally`期待するすべての特定の例外をキャッチした後、構造体。 制御フローに到達できることはありません、`Catch`これらのバリエーションのいずれかに依存してブロックします。

- `type`は`Exception`など。 `Catch ex As Exception`

- ステートメントが no`exception`例については、変数。 `Catch`

ときに、`Try…Catch…Finally`別のステートメントが入れ子になった`Try`ブロック、Visual Basic が最初に各検証`Catch`最も内側のステートメント`Try`ブロックします。 一致する場合`Catch`ステートメントが見つかると、検索が実行する、`Catch`の外側のステートメント`Try…Catch…Finally`ブロックします。

ローカル変数、`Try`ブロックでは使用できません、`Catch`の別のブロックであるためにをブロックします。 1 つ以上のブロックで変数を使用する場合は、外部変数を宣言、`Try...Catch...Finally`構造体。

> [!TIP]
> `Try…Catch…Finally`ステートメントは、IntelliSense コード スニペットとして利用できます。 コード スニペット マネージャーで、展開**コード パターン - If、For Each、Try Catch、プロパティなど**、し**エラー処理 (例外)** します。 詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。

## <a name="finally-block"></a>Finally ブロック

1 つまたは複数のステートメントを終了する前に実行する必要がある場合、`Try`構造体を使用して、`Finally`ブロックします。 制御が移ります、`Finally`ブロックだけの out を渡す前に、`Try…Catch`構造体。 これは内で例外が発生した場合でも、`Try`構造体。

A`Finally`ブロックは、例外がある場合でも実行する必要がありますすべてのコードを実行しているに便利です。 制御が渡される、`Finally`関係なくブロック`Try...Catch`ブロックが終了します。

内のコードを`Finally`ブロックが実行されますが、コードが発生した場合でも、`Return`内のステートメントを`Try`または`Catch`ブロックします。 コントロールから渡しません、`Try`または`Catch`、対応するブロック`Finally`ブロックで、次の場合。

- [End ステートメント](end-statement.md)で発生した、`Try`または`Catch`ブロックします。

- A<xref:System.StackOverflowException>でスローされたが、`Try`または`Catch`ブロックします。

実行を明示的に転送することはできません、`Finally`ブロックします。 転送の実行、`Finally`ブロックが例外を除いて有効でないです。

場合、`Try`ステートメントが少なくとも 1 つ含まれていない`Catch`ブロックを含める必要があります、`Finally`ブロックします。

> [!TIP]
> 場合は、特定の例外をキャッチする必要はありません、`Using`ステートメントの動作を`Try…Finally`ブロックとブロックを終了する方法に関係なく、リソースの破棄を保証します。 これはハンドルされない例外にも当てはまります。 詳細については、「[Using ステートメント](using-statement.md)」を参照してください。

## <a name="exception-argument"></a>引数の例外

`Catch`ブロック`exception`引数のインスタンスである、<xref:System.Exception>クラスまたはクラスから派生した、`Exception`クラス。 `Exception`クラスのインスタンスで発生したエラーに対応して、`Try`ブロックします。

プロパティ、`Exception`原因と、例外の場所を識別するためにヘルプをオブジェクトします。 たとえば、<xref:System.Exception.StackTrace%2A>プロパティを検索、コードでエラーが発生すれば、例外の原因と呼ばれるメソッドの一覧します。 <xref:System.Exception.Message%2A> 例外を説明するメッセージが返されます。 <xref:System.Exception.HelpLink%2A> 関連付けられているヘルプ ファイルへのリンクを返します。 <xref:System.Exception.InnerException%2A> 返します、`Exception`または現在の例外の原因となったオブジェクトを返します`Nothing`元が存在しない場合`Exception`します。

## <a name="considerations-when-using-a-trycatch-statement"></a>Try…Catchステートメントを使用に関する注意点

使用して、`Try…Catch`ステートメントがプログラムの異常なまたは予期しないイベントの発生を知らせるだけです。 この理由から、次のとおりです。

- 実行時に例外をキャッチすると、追加のオーバーヘッドを作成し、例外を回避するために事前に確認するよりも低下する可能性があります。

- 場合、`Catch`ブロックが正しく処理されませんが、例外がユーザーに正しく報告されましていない可能性があります。

- 例外処理より複雑なプログラムをによりします。

常に必要はありません、`Try…Catch`発生する可能性がある条件を確認するステートメント。 次の例では、ファイルを開こうとする前に存在するかどうかを確認します。 これによってスローされる例外をキャッチする必要性が軽減、<xref:System.IO.File.OpenText%2A>メソッド。

[!code-vb[VbVbalrStatements#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#94)]

内のコードを確認します。`Catch`ブロックがまたは適切なメッセージのログ記録をスレッド セーフであるかどうかを、ユーザーに例外を正しく報告できます。 それ以外の場合、例外は、不明な残る可能性があります。

## <a name="async-methods"></a>非同期メソッド

持つメソッドをマークする場合、 [Async](../modifiers/async.md)修飾子を使用できます、 [Await](../operators/await-operator.md)メソッド内の演算子。 ステートメントを`Await`演算子は、待機中のタスクが完了するまでに、メソッドの実行を中断します。 このタスクは、進行中の作業を表します。 ときに関連付けられているタスク、`Await`演算子が終了すると、同じメソッド内で実行が再開されます。 詳細については、次を参照してください。[非同期プログラムにおける制御フロー](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)します。

非同期のメソッドによって返されるタスクは、ハンドルされない例外が完了したことを示すエラーが発生した状態になる可能性があります。 タスクがその結果、取り消された状態になる可能性がありますも、 `OperationCanceledException` await 式からスローされます。 どちらの種類の例外をキャッチするには、配置、`Await`式内のタスクに関連付けられている、`Try`で例外をキャッチして、ブロック、`Catch`ブロックします。 このトピックで後述する例が提供されます。

複数の例外がそのエラーの前に行うために、タスクは faulted 状態にできます。 たとえば、タスクは <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> の呼び出しの結果になることがあります。 このようなタスクを待機して例外をキャッチしましたが、例外の 1 つだけどの例外がキャッチされるかを予測することはできません。 このトピックで後述する例が提供されます。

`Await`内で式が使用できない、`Catch`ブロックまたは`Finally`ブロックします。

## <a name="iterators"></a>反復子

反復子メソッドまたは`Get`アクセサーは、コレクションに対するカスタム イテレーションを実行します。 反復子は[Yield](yield-statement.md)ステートメントを使用して、コレクションの各要素を一度に 1 つずつ返します。 [For Each...Next ステートメント](for-each-next-statement.md)を使用して反復子メソッドを呼び出します。

`Yield`は`Try`ブロック内に置くことができます。 `Yield`ステートメントを含む`Try`ブロックは、`Catch`ブロックを持つことができ、そして、`Finally`ブロックを持つことができます。 例については、[反復子](../../programming-guide/concepts/iterators.md)の`Try`ブロックを参照してください。

`Yield`ステートメントは、`Catch`ブロックまたは`Finally`ブロック内で使用できません。

`For Each`本体 (反復子メソッドの外側)が例外をスローした場合、反復子メソッド内の`Catch`ブロックは実行されませんが、反復子メソッド内の`Finally`ブロックは実行されます。 反復子メソッド内の`Catch`ブロックは、反復子メソッド内で発生する例外のみをキャッチします。

## <a name="partial-trust-situations"></a>部分的に信頼された状況

ネットワーク共有でホストされるアプリケーションなど、部分的に信頼された状況で`Try...Catch...Finally`呼び出しを含むメソッドが呼び出される前に発生するセキュリティ例外をキャッチしません。 次の例では、サーバー共有に配置し、そこから、実行するときは、エラーを生成します"System.Security.SecurityException:要求が失敗しました。" セキュリティ例外の詳細については、次を参照してください。、<xref:System.Security.SecurityException>クラス。

[!code-vb[VbVbalrStatements#85](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#85)]

このような部分的に信頼された状況で配置する必要がある、`Process.Start`個別のステートメント`Sub`します。 最初の呼び出し、`Sub`は失敗します。 これにより、`Try...Catch`する前にそれをキャッチする、`Sub`を格納している`Process.Start`が開始し、セキュリティ例外が生成します。

## <a name="examples"></a>使用例

### <a name="the-structure-of-trycatchfinally"></a>Try の構造をしています.キャッチしてください.最終的に

次の例の構造を示しています、`Try...Catch...Finally`ステートメント。

[!code-vb[VbVbalrStatements#86](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#86)]  

### <a name="exception-in-a-method-called-from-a-try-block"></a>Try ブロックから呼び出されるメソッドで例外

次の例では、`CreateException`メソッドがスローされます、`NullReferenceException`します。 例外を生成するコードが、`Try`ブロックします。 そのため、`CreateException`メソッドが例外を処理できません。 `RunSample`ため、例外の処理はメソッドの呼び出し、`CreateException`メソッドが、`Try`ブロック。

例では、含まれています`Catch`からいくつかの種類の例外、ステートメントの順序に最も一般的な固有性の高い。

[!code-vb[VbVbalrStatements#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#91)]

### <a name="the-catch-when-statement"></a>キャッチとステートメント

次の例は、使用する方法を示します、`Catch When`条件式でフィルター処理するステートメント。 条件式の評価が場合`True`、コードでは、`Catch`ブロックが実行されます。

[!code-vb[VbVbalrStatements#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#92)]

### <a name="nested-try-statements"></a>入れ子になった Try ステートメント

次の例は、`Try…Catch`ステートメントに含まれている、`Try`ブロックします。 内部`Catch`ブロックがある例外をスロー、`InnerException`プロパティが、元の例外に設定します。 外側`Catch`ブロックが、独自の例外と内部例外を報告します。

[!code-vb[VbVbalrStatements#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#93)]

### <a name="exception-handling-for-async-methods"></a>非同期メソッドの例外処理

次の例では、非同期メソッドの例外処理を示します。 非同期タスクに適用される例外をキャッチする、`Await`式が、`Try`でブロック、呼び出し元の例外がキャッチされました、`Catch`ブロックします。

例外処理を示すために、この例の `Throw New Exception` 行のコメントを解除します。 例外がキャッチされました、`Catch`ブロック、タスクの`IsFaulted`プロパティに設定されて`True`、およびタスクの`Exception.InnerException`プロパティは、例外を設定します。

`Throw New OperationCancelledException` 行のコメントを解除して、非同期処理を取り消したときに何が起こるかを示します。 例外がキャッチされました、`Catch`ブロック、およびタスクの`IsCanceled`プロパティに設定されて`True`します。 ただし、条件によって、この例に適用されない`IsFaulted`に設定されている`True`と`IsCanceled`に設定されている`False`します。

[!code-vb[csAsyncExceptions#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#1)]

### <a name="handling-multiple-exceptions-in-async-methods"></a>非同期のメソッドで複数の例外の処理

次の例では、複数のタスクで複数の例外が発生する可能性がある例外処理について説明します。 `Try`ブロックには、`Await`タスクの式を<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>が返されます。 3 つのタスクと、タスクが完了<xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType>適用が完了します。

3 つのタスクでそれぞれ例外が発生します。 `Catch`ブロックがであると、例外を反復処理、`Exception.InnerExceptions`タスクのプロパティを`Task.WhenAll`が返されます。

[!code-vb[csAsyncExceptions#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncexceptions/vb/class1.vb#3)]

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:System.Exception>
- [Exit ステートメント](exit-statement.md)
- [On Error ステートメント](on-error-statement.md)
- [コード スニペットを使用するためのベスト プラクティス](/visualstudio/ide/best-practices-for-using-code-snippets)
- [例外処理](../../../standard/parallel-programming/exception-handling-task-parallel-library.md)
- [Throw ステートメント](throw-statement.md)
