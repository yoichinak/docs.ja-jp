---
title: On Error ステートメント (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.OnError
helpviewer_keywords:
- Visual Basic code, control flow
- Resume Next statement [Visual Basic]
- errors [Visual Basic], trapping
- error handling, On Error statement
- Next statement [Visual Basic], On Error
- control flow [Visual Basic], branching
- Error keyword [Visual Basic]
- execution [Visual Basic], conditional
- Resume statement [Visual Basic], and On Error statement
- Error statement [Visual Basic], and On Error statement
- GoTo statement [Visual Basic], and On Error statement
- branching [Visual Basic], on error
- conditional statements [Visual Basic], On Error
- On Error statement [Visual Basic], syntax
- On keyword [Visual Basic]
- run-time errors [Visual Basic], handling
- On Error statement [Visual Basic]
ms.assetid: ff947930-fb84-40cf-bd66-1ea219561d5c
ms.openlocfilehash: 4474b217147aca74f2c6e5376c8f55318a05bf4a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046514"
---
# <a name="on-error-statement-visual-basic"></a>On Error ステートメント (Visual Basic)
エラー処理ルーチンを有効にし、プロシージャ内でルーチンの場所を指定します。は、エラー処理ルーチンを無効にするためにも使用できます。 ステートメント`On Error`は、構造化されていないエラー処理で使用され、構造化例外処理の代わりに使用できます。 [構造化例外処理](../../../standard/exceptions/index.md)は .net に組み込まれているので、一般に効率が向上するため、アプリケーションで実行時エラーを処理する場合に推奨されます。

 エラー処理または例外処理を使用しない場合、発生したすべての実行時エラーは致命的なエラーであり、エラーメッセージが表示され、実行が停止します。

> [!NOTE]
> キーワードは、旧バージョンとの互換性のためにサポートされている[Error ステートメント](../../../visual-basic/language-reference/statements/error-statement.md)でも使用されます。 `Error`

## <a name="syntax"></a>構文

```vb
On Error { GoTo [ line | 0 | -1 ] | Resume Next }
```

## <a name="parts"></a>指定項目

|用語|定義|
|---|---|
|`GoTo`*行*|必須の*line*引数で指定された行から開始するエラー処理ルーチンを有効にします。 *Line*引数は、任意の行ラベルまたは行番号です。 実行時エラーが発生した場合、コントロールは指定された行に分岐し、エラーハンドラーがアクティブになります。 指定された行は、 `On Error`ステートメントと同じプロシージャ内に存在する必要があります。指定しないと、コンパイル時エラーが発生します。|
|`GoTo 0`|現在のプロシージャで有効になっているエラーハンドラーを`Nothing`無効にし、にリセットします。|
|`GoTo -1`|現在のプロシージャで有効になっている例外を`Nothing`無効にし、にリセットします。|
|`Resume Next`|実行時エラーが発生したときに、エラーが発生したステートメントの直後のステートメントに制御を移動し、その時点から実行を続行することを指定します。 オブジェクト`On Error GoTo`にアクセスするときではなく、この形式を使用します。|

## <a name="remarks"></a>Remarks

> [!NOTE]
> 構造化例外処理は、構造化されていない例外処理と`On Error`ステートメントを使用するのではなく、可能な限りコードで使用することをお勧めします。 詳細については、[Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)を参照してください。

 "Enabled" エラーハンドラーは、 `On Error`ステートメントによって有効にされているものです。 "アクティブ" エラーハンドラーは、エラーを処理するための有効なハンドラーです。

 エラーハンドラーがアクティブになっている間にエラーが発生した場合 (エラーが`Resume`発生し`Exit Function`た場合`Exit Property`と`Exit Sub`、、、、またはステートメントの場合)、現在のプロシージャのエラーハンドラーはエラーを処理できません。 呼び出し元のプロシージャに制御が戻ります。
  
 呼び出し元のプロシージャに有効なエラーハンドラーがある場合は、エラーを処理するためにアクティブ化されます。 呼び出し元のプロシージャのエラーハンドラーもアクティブになっている場合は、有効になっているが非アクティブなエラーハンドラーが見つかるまで、制御は前の呼び出しプロシージャを通過します。 このようなエラーハンドラーが見つからない場合、エラーは実際に発生した時点で致命的です。
  
 エラーハンドラーが呼び出し元のプロシージャに制御を戻すたびに、そのプロシージャが現在のプロシージャになります。 任意のプロシージャのエラーハンドラーによってエラーが処理されると、 `Resume`ステートメントで指定された時点で、現在のプロシージャで実行が再開されます。
  
> [!NOTE]
> エラー処理ルーチンは、プロシージャ`Sub` `Function`またはプロシージャではありません。 これは、行ラベルまたは行番号でマークされたコードのセクションです。
  
## <a name="number-property"></a>Number プロパティ
 エラー処理ルーチンは、エラーの原因を特定`Number`するために`Err` 、オブジェクトのプロパティの値に依存します。 ルーチンは、他のエラーが発生する前、 `Err`またはエラーが発生する可能性のあるプロシージャが呼び出される前に、オブジェクト内の関連するプロパティ値をテストまたは保存する必要があります。 `Err`オブジェクトのプロパティ値は、最新のエラーのみを反映します。 に関連付けられ`Err.Number`ているエラー `Err.Description`メッセージは、に含まれています。  
  
## <a name="throw-statement"></a>Throw ステートメント  
 `Err.Raise`メソッドで発生したエラーは、 <xref:System.Exception>新しく作成`Exception`されたクラスのインスタンスにプロパティを設定します。 派生した例外の種類`Throw`の例外の発生をサポートするために、言語でステートメントがサポートされています。 これは、スローされる例外インスタンスである1つのパラメーターを受け取ります。 次の例は、これらの機能を既存の例外処理サポートと共に使用する方法を示しています。

 [!code-vb[VbVbalrErrorHandling#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#17)]  
  
 例外クラスに`On Error GoTo`関係なく、ステートメントによってすべてのエラーがトラップされることに注意してください。
  
## <a name="on-error-resume-next"></a>エラー時に再開する
 `On Error Resume Next`実行は、実行時エラーの原因となったステートメントの直後のステートメント、またはステートメントを含む`On Error Resume Next`プロシージャからの最新の呼び出しの直後のステートメントによって続行されます。 このステートメントを使用すると、実行時エラーが発生しても実行を続行できます。 プロシージャ内の別の場所に制御を転送するのではなく、エラーが発生するエラー処理ルーチンを配置できます。 別`On Error Resume Next`のプロシージャが呼び出されると、ステートメントは非アクティブになります`On Error Resume Next` 。そのため、ルーチン内でインラインエラー処理が必要な場合は、呼び出された各ルーチンでステートメントを実行する必要があります。
  
> [!NOTE]
> 他`On Error Resume Next`のオブジェクトへのアクセス`On Error GoTo`中に発生したエラーを処理する場合は、コンストラクトの方が適している場合があります。 オブジェクト`Err`を操作するたびに、コードによってアクセスされたオブジェクトがあいまいになるのを確認します。 エラーコード`Err.Number`を配置したオブジェクトと、最初にエラーを生成したオブジェクト (で`Err.Source`指定されたオブジェクト) を確認できます。

## <a name="on-error-goto-0"></a>On Error GoTo 0
 `On Error GoTo 0`現在のプロシージャでのエラー処理を無効にします。 プロシージャに行番号0が含まれている場合でも、エラー処理コードの先頭として行0が指定されていません。 `On Error GoTo 0`ステートメントを使用しない場合、プロシージャが終了すると、エラーハンドラーが自動的に無効になります。

## <a name="on-error-goto--1"></a>エラー時の GoTo-1
 `On Error GoTo -1`現在のプロシージャの例外を無効にします。 プロシージャに1行の番号が含まれている場合でも、エラー処理コードの開始として行-1 を指定しません。 `On Error GoTo -1`ステートメントを使用しない場合、プロシージャが終了すると、例外が自動的に無効になります。

 エラーが発生しなかったときにエラー処理コードが実行されない`Exit Sub`よう`Exit Function`にする`Exit Property`には、次のように、、、またはステートメントをエラー処理ルーチンの直前に配置します。

 [!code-vb[VbVbalrErrorHandling#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#18)]

 ここでは、エラー処理コードは`Exit Sub`ステートメントに従い、ステートメントの`End Sub`前に記述してプロシージャフローから分離します。 プロシージャ内の任意の場所にエラー処理コードを配置できます。

## <a name="untrapped-errors"></a>トラップエラー
 オブジェクトのトラップされていないエラーは、オブジェクトが実行可能ファイルとして実行されている場合に、制御を行うアプリケーションに返されます。 開発環境では、適切なオプションが設定されている場合にのみ、トラップされないエラーが制御アプリケーションに返されます。 デバッグ中に設定するオプション、設定方法、およびホストでクラスを作成できるかどうかの説明については、ホストアプリケーションのドキュメントを参照してください。

 他のオブジェクトにアクセスするオブジェクトを作成する場合は、返されたハンドルされていないエラーを処理する必要があります。 できない場合は、エラーコード`Err.Number`を独自のエラーのいずれかにマップし、オブジェクトの呼び出し元に渡します。 エラーコードを`VbObjectError`定数に追加して、エラーを指定する必要があります。 たとえば、エラーコードが1052の場合は、次のように割り当てます。

 [!code-vb[VbVbalrErrorHandling#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#19)]

> [!CAUTION]
> Windows ダイナミックリンクライブラリ (Dll) の呼び出し中にシステムエラーが発生しても、例外は発生せず、Visual Basic エラートラップでトラップすることはできません。 DLL 関数を呼び出すときは、API の仕様に従って、成功または失敗の各戻り値を確認し、エラーが発生した場合は、 `Err`オブジェクトの`LastDLLError`プロパティの値を確認する必要があります。

## <a name="example"></a>例
 この例では、 `On Error GoTo`最初にステートメントを使用して、プロシージャ内のエラー処理ルーチンの場所を指定します。 この例では、0で除算しようとするとエラー番号6が生成されます。 エラー処理ルーチンでエラーが処理され、エラーの原因となったステートメントに制御が返されます。 ステートメント`On Error GoTo 0`により、エラートラップが無効になります。 次に`On Error Resume Next` 、ステートメントを使用して、次のステートメントによって生成されるエラーのコンテキストが特定ので認識されるように、エラートラップを遅延します。 は、エラーが処理され`Err`た後にオブジェクトのプロパティをクリアするために使用されます。 `Err.Clear`

 [!code-vb[VbVbalrErrorHandling#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#20)]

## <a name="requirements"></a>必要条件
 **名前空間:** [Microsoft. Visual Basic](../../../visual-basic/language-reference/runtime-library-members.md)

 **組み立て**Visual Basic ランタイム ライブラリ (Microsoft.VisualBasic.dll)

## <a name="see-also"></a>関連項目

- <xref:Microsoft.VisualBasic.Information.Err%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Number%2A>
- <xref:Microsoft.VisualBasic.ErrObject.Description%2A>
- <xref:Microsoft.VisualBasic.ErrObject.LastDllError%2A>
- [End ステートメント](../../../visual-basic/language-reference/statements/end-statement.md)
- [Exit ステートメント](../../../visual-basic/language-reference/statements/exit-statement.md)
- [Resume ステートメント](../../../visual-basic/language-reference/statements/resume-statement.md)
- [エラー メッセージ](../../../visual-basic/language-reference/error-messages/index.md)
- [Try...Catch...Finally ステートメント](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
