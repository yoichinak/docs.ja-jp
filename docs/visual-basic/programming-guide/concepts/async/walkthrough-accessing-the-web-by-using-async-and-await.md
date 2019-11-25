---
title: 'チュートリアル: Async と Await を使用した Web へのアクセス'
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: c13e592eb155d14c2e7cb2388a96925a7f1fa413
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349093"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a>チュートリアル: Async と Await を使用した Web へのアクセス (Visual Basic)

async/await 機能を使用することで、非同期プログラムをより簡単かつ直感的に記述できます。 同期コードに似た非同期コードを記述し、通常の非同期コードが必要とする難しいコールバック関数や継続の処理をコンパイラに任せます。

For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).

このチュートリアルは、Web サイトの一覧でのバイト数の合計を計算する同期 Windows Presentation Foundation (WPF) アプリケーションから開始します。 その後、新しい機能を使用して、アプリケーションを非同期ソリューションに変換します。

自分でアプリケーションを作成しない場合は、[開発者コード サンプル](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)のページから、"Async Sample: Accessing the Web Walkthrough (C# and Visual Basic) (非同期サンプル: Web へのアクセスのチュートリアル (C# および Visual Basic))" をダウンロードできます。

このチュートリアルでは、次のタスクを行います。

> [!div class="checklist"]
>
> - [Create a WPF application](#create-a-wpf-application)
> - [Design a simple WPF MainWindow](#design-a-simple-wpf-mainwindow)
> - [Add a reference](#add-a-reference)
> - [Add necessary Imports statements](#add-necessary-imports-statements)
> - [Create a synchronous application](#create-a-synchronous-application)
> - [Test the synchronous solution](#test-the-synchronous-solution)
> - [Convert GetURLContents to an asynchronous method](#convert-geturlcontents-to-an-asynchronous-method)
> - [Convert SumPageSizes to an asynchronous method](#convert-sumpagesizes-to-an-asynchronous-method)
> - [Convert startButton_Click to an asynchronous method](#convert-startbutton_click-to-an-asynchronous-method)
> - [Test the asynchronous solution](#test-the-asynchronous-solution)
> - [Replace the GetURLContentsAsync method with a .NET Framework method](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

See the [Example](#example) section for the complete asynchronous example.

## <a name="prerequisites"></a>必要条件

お使いのコンピューターに、Visual Studio 2012 以降がインストールされている必要があります。 For more information, see the Visual Studio [Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.

## <a name="create-a-wpf-application"></a>WPF アプリケーションを作成する

1. Visual Studio を起動します。

2. メニュー バーで **[ファイル]** 、 **[新規作成]** 、 **[プロジェクト]** の順にクリックします。

    **[新しいプロジェクト]** ダイアログ ボックスが表示されます。

3. In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.

4. **[名前]** ボックスに「`AsyncExampleWPF`」と入力して、 **[OK]** を選択します。

    **ソリューション エクスプローラー**に新しいプロジェクトが表示されます。

## <a name="design-a-simple-wpf-mainwindow"></a>単純な WPF MainWindow をデザインする

1. Visual Studio コード エディターで、 **[MainWindow.xaml]** タブをクリックします。

2. **[ツールボックス]** ウィンドウが表示されていない場合は、 **[表示]** メニューを開き、 **[ツールボックス]** をクリックします。

3. **[Button]** コントロールと **[TextBox]** コントロールを **[MainWindow]** ウィンドウに追加します。

4. **[TextBox]** コントロールを強調表示し、 **[プロパティ]** ウィンドウで次の値を設定します。

    - **[Name]** プロパティを `resultsTextBox` に設定します。

    - **[Height]** プロパティを 250 に設定します。

    - **[Width]** プロパティを 500 に設定します。

    - **[テキスト]** タブで、Lucida Console や Global Monospace などの等幅フォントを指定します。

5. **[Button]** コントロールを強調表示し、 **[プロパティ]** ウィンドウで次の値を設定します。

    - **[Name]** プロパティを `startButton` に設定します。

    - **[Content]** プロパティの値を **[Button]** から **[Start]** に変更します。

6. テキスト ボックスとボタンの位置を調整し、両方が **[MainWindow]** ウィンドウ内に表示されるようにします。

    WPF XAML デザイナーについて詳しくは、「[XAML デザイナーを使用した UI の作成](/visualstudio/xaml-tools/creating-a-ui-by-using-xaml-designer-in-visual-studio)」をご覧ください。

## <a name="add-a-reference"></a>参照を追加する

1. **ソリューション エクスプローラー**で、プロジェクトの名前を強調表示します。

2. メニュー バーで、 **[プロジェクト]** 、 **[参照の追加]** の順に選択します。

    **[参照マネージャー]** ダイアログ ボックスが表示されます。

3. ダイアログ ボックスの上部で、プロジェクトのターゲットが .NET Framework 4.5 以上であることを確認します。

4. **[アセンブリ]** で、 **[フレームワーク]** を選択します (選択されていない場合)。

5. 名前の一覧で、 **[System.Net.Http]** のチェック ボックスをオンにします。

6. **[OK]** をクリックしてダイアログ ボックスを閉じます。

## <a name="add-necessary-imports-statements"></a>Add necessary Imports statements

1. In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.

2. Add the following `Imports` statements at the top of the code file if they’re not already present.

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a>Create a synchronous application

1. In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.

2. In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    このコードは、`SumPageSizes` アプリケーションを実行するメソッドを呼び出し、`startButton_Click` に制御が戻るとメッセージを表示します。

3. 同期ソリューションのコードには、次の 4 つのメソッドが含まれています。

    - `SumPageSizes` は、`SetUpURLList` から Web ページ URL のリストを取得し、`GetURLContents` と `DisplayResults` を呼び出して各 URL を処理します。

    - `SetUpURLList` は、Web アドレスのリストを作成して返します。

    - `GetURLContents` は、各 Web サイトのコンテンツをダウンロードし、バイト配列としてそのコンテンツを返します。

    - `DisplayResults` は、各 URL のバイト配列内のバイト数を表示します。

    Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:

    ```vb
    Private Sub SumPageSizes()

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetURLContents returns the contents of url as a byte array.
            Dim urlContents As Byte() = GetURLContents(url)

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the web addresses.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)
    End Sub

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Function GetURLContents(url As String) As Byte()

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        Using response As WebResponse = webReq.GetResponse()
            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content)
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

## <a name="test-the-synchronous-solution"></a>同期ソリューションをテストする

1. F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。

    次の一覧のような出力が表示されます。

    ```console
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832
    msdn.microsoft.com                                            33964
    msdn.microsoft.com/library/hh290136.aspx               225793
    msdn.microsoft.com/library/ee256749.aspx               143577
    msdn.microsoft.com/library/hh290138.aspx               237372
    msdn.microsoft.com/library/hh290140.aspx               128279
    msdn.microsoft.com/library/dd470362.aspx               157649
    msdn.microsoft.com/library/aa578028.aspx               204457
    msdn.microsoft.com/library/ms404677.aspx               176405
    msdn.microsoft.com/library/ff730837.aspx               143474

    Total bytes returned:  1834802

    Control returned to startButton_Click.
    ```

    カウントの表示には数秒かかる点に注意してください。 その間、要求されたリソースのダウンロードが完了するまで UI スレッドがブロックされます。 このため、 **[Start]** ボタンのクリック後は、表示ウィンドウの移動、最大化、最小化のほか、閉じることさえできなくなります。 バイト カウントの表示が開始するまでは、これらの操作を実行しても失敗します。 Web サイトが応答していない場合、どのサイトに問題があるのかを示す情報は表示されません。 待つのをやめて、プログラムを閉じることさえ難しい状態になります。

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a>GetURLContents を非同期メソッドに変換する

1. To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> method and to the <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> method are where the application accesses the web. .NET Framework には両方のメソッドの非同期バージョンが用意されているため、変換は簡単です。

    `GetURLContents` で使用されているメソッドの詳細については、「<xref:System.Net.WebRequest>」を参照してください。

    > [!NOTE]
    > このチュートリアルの手順に従っていると、いくつかのコンパイラ エラーが表示されます。 これらのエラーは無視することで、チュートリアルを続行できます。

    `GetURLContents` の 3 行目で呼び出されるメソッドを、`GetResponse` から、非同期でタスク ベースの <xref:System.Net.WebRequest.GetResponseAsync%2A> メソッドに変更します。

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. `GetResponseAsync` は、<xref:System.Threading.Tasks.Task%601> を返します。 この場合、*タスク戻り変数*の `TResult` の型は <xref:System.Net.WebResponse> です。 このタスクは、要求されたデータのダウンロードが完了し、タスクが最後まで実行された後に、実際の `WebResponse` オブジェクトを生成するという約束です。

    To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    `Await` 演算子は、現在のメソッド、`GetURLContents` の実行を、待機しているタスクが完了するまで中断します。 その間、現在のメソッドの呼び出し元に制御が戻されます。 この例では、現在のメソッドが `GetURLContents` で、呼び出し元が `SumPageSizes` です。 タスクが完了すると、約束されていた `WebResponse` オブジェクトが完了したタスクの値として生成され、変数 `response` に割り当てられます。

    上記のステートメントは、動作を明確にするため、次の 2 つのステートメントに分割できます。

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    `webReq.GetResponseAsync` への呼び出しによって、`Task(Of WebResponse)` または `Task<WebResponse>` が返されます。 Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.

    非同期メソッドにタスクの完了に依存しない処理がある場合、メソッドはこれら 2 つのステートメントの間、つまり非同期メソッドへの呼び出しから、await 演算子の適用までの間にその処理を続行することができます。 For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).

3. 前の手順で `Await` 演算子を追加したため、コンパイラ エラーが発生します。 The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier. `CopyTo` への呼び出しを `CopyToAsync` への呼び出しに置き換える変換手順を繰り返す間は、エラーを無視してください。

    - 呼び出されるメソッドの名前を <xref:System.IO.Stream.CopyToAsync%2A> に変更します。

    - `CopyTo` または `CopyToAsync` メソッドは、その引数 `content` にバイトをコピーし、意味のある値は返しません。 同期バージョンでは、`CopyTo` への呼び出しは値を返さない単純なステートメントです。 非同期バージョンでは、`CopyToAsync` は <xref:System.Threading.Tasks.Task> を返します。 タスクは "Task(void)" のように機能し、メソッドを待機できるようにします。 次のコードに示すように、`Await` または `await` を、`CopyToAsync` への呼び出しに適用します。

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         上記のステートメントでは、次の 2 行のコードを省略しています。

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. `GetURLContents` 内で必要な作業として残っているのは、メソッド シグネチャの調整のみです。 You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier. 次のコードに示すように、修飾子を追加し、メソッドを*非同期メソッド*としてマークします。

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>. Visual Basic でのメソッドは、`Task` または `Task(Of T)` を返す `Function` にするか、`Sub` にする必要があります。 Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required. In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.

    For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).

    メソッド `GetURLContents` には return ステートメントがあり、このステートメントはバイト配列を返します。 そのため、非同期バージョンの戻り値の型は Task(T) であり、T はバイト配列です。 メソッド シグネチャに、次の変更を加えます。

    - 戻り値の型を `Task(Of Byte())` に変更します。

    - 規則により、非同期メソッドは "Async" で終わる名前を持つことになっているため、メソッドの名前を `GetURLContentsAsync` に変更します。

    これらの変更を次のコードに示します。

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    このいくつかの変更によって、`GetURLContents` の非同期メソッドへの変換が完了しました。

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a>SumPageSizes を非同期メソッドに変換する

1. `SumPageSizes` に対して、前述した手順を繰り返します。 まずは、`GetURLContents` への呼び出しを非同期呼び出しに変更します。

    - 呼び出されるメソッドの名前を `GetURLContents` から `GetURLContentsAsync` に変更します (まだ変更していない場合)。

    - バイト配列値を取得するために、`Await` を、`GetURLContentsAsync` が返すタスクに適用します。

    これらの変更を次のコードに示します。

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    上記の割り当てでは、次の 2 行のコードを省略しています。

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. メソッドのシグネチャに、次の変更を加えます。

    - メソッドを `Async` 修飾子でマークします。

    - メソッド名に "Async" を追加します。

    - There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable. Therefore, change the method type from `Sub` to `Function`. 関数の戻り値の型は、`Task` です。

    これらの変更を次のコードに示します。

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    `SumPageSizes` から `SumPageSizesAsync` への変換が完了しました。

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a>startButton_Click を非同期メソッドに変換する

1. イベント ハンドラーで、呼び出されるメソッドの名前を `SumPageSizes` から `SumPageSizesAsync` に変更します (まだ変更していない場合)。

2. `SumPageSizesAsync` は非同期メソッドであるため、結果を待機するイベント ハンドラーのコードを変更します。

    `SumPageSizesAsync` への呼び出しは、`GetURLContentsAsync` の `CopyToAsync` への呼び出しに似ています。 この呼び出しによって、`Task(T)` ではなく `Task` が返されます。

    前述した手順と同様に、1 つまたは 2 つのステートメントを使用して、呼び出しを変換できます。 これらの変更を次のコードに示します。

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. 誤って操作が再入することを避けるために、次のステートメントを `startButton_Click` の先頭に追加して **[Start]** ボタンを無効にします。

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    イベント ハンドラーの末尾で、ボタンを再び有効にできます。

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).

4. 最後に、`Async` 修飾子を宣言に追加し、イベント ハンドラーが `SumPagSizesAsync` を待機できるようにします。

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    通常、イベント ハンドラーの名前は変更されません。 The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.

    同期処理から非同期処理へのプロジェクトの変換が完了しました。

## <a name="test-the-asynchronous-solution"></a>非同期ソリューションをテストする

1. F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。

2. 同期ソリューションの出力に似た出力が表示されます。 ただし、次の相違点に注意してください。

    - 処理の完了後に、すべての結果が同時に表示されることはありません。 たとえば、両方のプログラムの `startButton_Click` には、テキスト ボックスをクリアする行が含まれています。 この目的は、実行ごとにテキスト ボックスをクリアすることです。1 つの結果セットが表示された後に、もう一度 **[Start]** ボタンをクリックすると、テキスト ボックスがクリアされます。 同期バージョンでは、2 回目のカウントが表示される直前、ダウンロードが完了して UI スレッドが他の処理を実行できる状態になったときにテキスト ボックスがクリアされます。 非同期バージョンでは、 **[Start]** ボタンをクリックした直後にテキスト ボックスがクリアされます。

    - 最も重要な点は、ダウンロード中に UI スレッドがブロックされないことです。 Web リソースをダウンロード、カウント、および表示している間に、ウィンドウの移動やサイズ変更を行うことができます。 いずれかの Web サイトの処理が遅い、または応答しない場合、**閉じる**ボタン (右上隅の赤色のフィールドにある [x]) をクリックすることで、操作を取り消すことができます。

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a>Replace the GetURLContentsAsync method with a .NET Framework method

1. The .NET Framework provides many async methods that you can use. One of them, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> method, does just what you need for this walkthrough. これを、前述の手順で作成した `GetURLContentsAsync` メソッドの代わりに使用できます。

    The first step is to create an <xref:System.Net.Http.HttpClient> object in the `SumPageSizesAsync` method. 次の宣言をメソッドの先頭に追加します。

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. `SumPageSizesAsync,` で、`GetURLContentsAsync` メソッドへの呼び出しを `HttpClient` メソッドへの呼び出しに置き換えます。

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. 記述した `GetURLContentsAsync` メソッドを削除するかコメント アウトします。

4. F5 キーを押してプログラムを実行し、 **[Start]** を複数回クリックします。

    このバージョンのプロジェクトの動作は、「非同期ソリューションをテストするには」の手順で説明している動作と同じですが、さらに少ない手間で作成できます。

## <a name="example"></a>例

The following is the full example of the converted asynchronous solution that uses the asynchronous `GetURLContentsAsync` method. この例は、元の同期ソリューションと非常によく似ています。

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        resultsTextBox.Clear()

        '' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)

            ' The previous line abbreviates the following two assignment statements.

            '//<snippet21>
            ' GetURLContentsAsync returns a task. At completion, the task
            ' produces a byte array.
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())

        ' The downloaded resource ends up in the variable named content.
        Dim content = New MemoryStream()

        ' Initialize an HttpWebRequest for the current URL.
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)

        ' Send the request to the Internet resource and wait for
        ' the response.
        Using response As WebResponse = Await webReq.GetResponseAsync()

            ' The previous statement abbreviates the following two statements.

            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
            'Using response As WebResponse = Await responseTask

            ' Get the data stream that is associated with the specified URL.
            Using responseStream As Stream = response.GetResponseStream()
                ' Read the bytes in responseStream and copy them to content.
                Await responseStream.CopyToAsync(content)

                ' The previous statement abbreviates the following two statements.

                ' CopyToAsync returns a Task, not a Task<T>.
                'Dim copyTask As Task = responseStream.CopyToAsync(content)

                ' When copyTask is completed, content contains a copy of
                ' responseStream.
                'Await copyTask
            End Using
        End Using

        ' Return the result as a byte array.
        Return content.ToArray()
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

次のコードには、`HttpClient` の `GetByteArrayAsync` メソッドを使用するソリューション例のすべてが含まれています。

```vb
' Add the following Imports statements, and add a reference for System.Net.Http.
Imports System.Net.Http
Imports System.Net
Imports System.IO

Class MainWindow

    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click

        resultsTextBox.Clear()

        ' Disable the button until the operation is complete.
        startButton.IsEnabled = False

        ' One-step async call.
        Await SumPageSizesAsync()

        ' Two-step async call.
        'Dim sumTask As Task = SumPageSizesAsync()
        'Await sumTask

        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."

        ' Reenable the button in case you want to run the operation again.
        startButton.IsEnabled = True
    End Sub

    Private Async Function SumPageSizesAsync() As Task

        ' Declare an HttpClient object and increase the buffer size. The
        ' default buffer size is 65,536.
        Dim client As HttpClient =
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}

        ' Make a list of web addresses.
        Dim urlList As List(Of String) = SetUpURLList()

        Dim total = 0
        For Each url In urlList
            ' GetByteArrayAsync returns a task. At completion, the task
            ' produces a byte array.
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)

            ' The following two lines can replace the previous assignment statement.
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)
            'Dim urlContents As Byte() = Await getContentsTask

            DisplayResults(url, urlContents)

            ' Update the total.
            total += urlContents.Length
        Next

        ' Display the total count for all of the websites.
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &
                                             "Total bytes returned:  {0}" & vbCrLf, total)
    End Function

    Private Function SetUpURLList() As List(Of String)

        Dim urls = New List(Of String) From
            {
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="see-also"></a>関連項目

- [非同期サンプル: Web へのアクセスのチュートリアル (C# および Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [Await 演算子](../../../../visual-basic/language-reference/operators/await-operator.md)
- [Async](../../../../visual-basic/language-reference/modifiers/async.md)
- [Async および Await を使用した非同期プログラミング (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [非同期の戻り値の型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- [タスク ベースの非同期プログラミング (TAP)](https://go.microsoft.com/fwlink/?LinkId=204847)
- [方法: Task.WhenAll を使用して AsyncWalkthrough を拡張する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [方法: Async と Await を使用して複数の Web 要求を並列実行する (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
