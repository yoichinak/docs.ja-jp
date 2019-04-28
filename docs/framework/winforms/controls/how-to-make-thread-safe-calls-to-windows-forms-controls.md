---
title: '方法: Windows フォーム コントロールのスレッド セーフな呼び出しを行う'
ms.date: 02/19/2019
dev_langs:
- csharp
- vb
f1_keywords:
- EHInvalidOperation.WinForms.IllegalCrossThreadCall
helpviewer_keywords:
- thread safety [Windows Forms], calling controls [Windows Forms]
- calling controls [Windows Forms], thread safety [Windows Forms]
- CheckForIllegalCrossThreadCalls property [Windows Forms]
- Windows Forms controls [Windows Forms], multithreading
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], cross-thread calls
- controls [Windows Forms], multithreading
ms.assetid: 138f38b6-1099-4fd5-910c-390b41cbad35
ms.openlocfilehash: 3211df1f0e585780039471b80b5b913613ad9bbd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913797"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>方法: Windows フォーム コントロールのスレッド セーフな呼び出しを行う

マルチ スレッドは、Windows フォームのアプリのパフォーマンスを向上させることができますが、Windows フォーム コントロールへのアクセスがスレッド セーフでは本質的にはありません。 マルチ スレッドは、非常に深刻かつ複雑なバグ、コードを公開できます。 2 つまたは複数のスレッドが、コントロールの操作では、コントロールが不整合な状態に強制的に移動でき、競合状態、デッドロック、およびがフリーズやハングすることができます。 実装する場合は、マルチ スレッド アプリケーションでは、スレッド セーフな方法で、スレッド間のコントロールを呼び出すことを確認します。 詳細については、次を参照してください。[マネージ スレッド処理のベスト プラクティス](../../../standard/threading/managed-threading-best-practices.md)します。 

Windows フォーム コントロールをそのコントロールを作成していないスレッドから安全に呼び出すに 2 つの方法はあります。 使用することができます、<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>コントロールを呼び出し、メイン スレッドで作成したデリゲートを呼び出すメソッド。 または、実装することができます、<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>結果のレポートから、バック グラウンド スレッドで実行される作業を分離するにはイベント ドリブン モデルを使用します。 

## <a name="unsafe-cross-thread-calls"></a>安全でないスレッド間の呼び出し

コントロールを作成していないスレッドから直接呼び出しは安全ではありません。 次のコード スニペットは、安全でない呼び出しを示しています、<xref:System.Windows.Forms.TextBox?displayProperty=nameWithType>コントロール。 `Button1_Click`イベント ハンドラーを作成する新しい`WriteTextUnsafe`スレッドで、設定、メイン スレッドの<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>プロパティを直接します。 

```csharp
private void Button1_Click(object sender, EventArgs e)
{
    thread2 = new Thread(new ThreadStart(WriteTextUnsafe));
    thread2.Start();
}
private void WriteTextUnsafe()
{
    textBox1.Text = "This text was set unsafely.";
}
```

```vb
Private Sub Button1_Click(ByVal sender As Object, e As EventArgs) Handles Button1.Click
    Thread2 = New Thread(New ThreadStart(AddressOf WriteTextUnsafe))
    Thread2.Start()
End Sub

Private Sub WriteTextUnsafe()
    TextBox1.Text = "This text was set unsafely."
End Sub
```

Visual Studio デバッガーは、発生させることによってこれらの安全でないスレッドの呼び出しを検出、<xref:System.InvalidOperationException>メッセージと共に**スレッド間の操作が無効です。コントロール""上で作成されたスレッド以外のスレッドからアクセスします。** <xref:System.InvalidOperationException>常に、Visual Studio のデバッグ時に安全でないスレッド間の呼び出しが発生し、アプリの実行時に発生する可能性があります。 問題を修正する必要がありますが、設定して、例外を無効にすることができます、<xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType>プロパティを`false`します。

## <a name="safe-cross-thread-calls"></a>スレッド間の安全な呼び出し 

次のコード例は、それを作成していないスレッドから、Windows フォーム コントロールを安全に呼び出す 2 つの方法を示しています。 
1. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>メソッドを呼び出すコントロールをメイン スレッドからデリゲートを呼び出します。 
2. A<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>コンポーネントであり、イベント ドリブン モデルを提供します。 

どちらの例では、シミュレートする 2 番目の 1 つのバック グラウンド スレッド スリープは、そのスレッドで実行されている動作します。 

ビルドしてから、.NET Framework アプリとしてこれらの例を実行することができます、C#または Visual Basic のコマンド ライン。 詳細については、次を参照してください。 [csc.exe を](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)または[(Visual Basic) コマンドラインからビルド](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)します。 

.NET Core 3.0 以降では、ことができますもビルドおよび実行する例では、.NET Core アプリを Windows として .NET Core の Windows フォームのあるフォルダーから *\<フォルダー名>.csproj* プロジェクト ファイル。 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>例:デリゲートで Invoke メソッドを使用します。

次の例では、Windows フォーム コントロールのスレッド セーフな呼び出しを確保するためのパターンを示します。 これは、クエリを<xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>コントロールを比較し、プロパティの呼び出し元のスレッド id ですスレッドの ID を作成する。 スレッド Id が同じ場合は、コントロールを直接呼び出します。 呼び出しスレッド Id が異なる場合、<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType>コントロールに実際の呼び出し、メイン スレッドからのデリゲート メソッド。

`SafeCallDelegate`設定を有効に、<xref:System.Windows.Forms.TextBox>コントロールの<xref:System.Windows.Forms.TextBox.Text%2A>プロパティ。 `WriteTextSafe`メソッド クエリ<xref:System.Windows.Forms.Control.InvokeRequired%2A>します。 場合<xref:System.Windows.Forms.Control.InvokeRequired%2A>返します`true`、`WriteTextSafe`渡します、`SafeCallDelegate`を<xref:System.Windows.Forms.Control.Invoke%2A>をコントロールには、実際の呼び出しを行うメソッドです。 場合<xref:System.Windows.Forms.Control.InvokeRequired%2A>返します`false`、`WriteTextSafe`設定、<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>直接します。 `Button1_Click`イベント ハンドラーが新しいスレッドを作成および実行される、`WriteTextSafe`メソッド。 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>例:BackgroundWorker のイベント ハンドラーを使用します。

簡単にマルチ スレッドの実装は、<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>イベント ドリブン モデルを使用して、コンポーネント。 バック グラウンド スレッドが、<xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType>イベントで、メイン スレッドと対話しません。 メイン スレッドが実行され、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType>と<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType>イベント ハンドラーは、メイン スレッドのコントロールを呼び出すことができます。

使用して、スレッド セーフな呼び出しを行う<xref:System.ComponentModel.BackgroundWorker>、操作を実行するバック グラウンド スレッドでメソッドを作成し、バインドするに、は<xref:System.ComponentModel.BackgroundWorker.DoWork>イベント。 バック グラウンド作業の結果を報告するメイン スレッドで別のメソッドを作成しにバインド、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>または<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント。 バック グラウンド スレッドを開始するには、呼び出す<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>します。 

この例では、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント ハンドラーを設定する、<xref:System.Windows.Forms.TextBox>コントロールの<xref:System.Windows.Forms.TextBox.Text%2A>プロパティ。 使用例について、<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベントを参照してください<xref:System.ComponentModel.BackgroundWorker>します。 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.BackgroundWorker>
- [方法: バック グラウンドで操作を実行します。](how-to-run-an-operation-in-the-background.md)
- [方法: バック グラウンド操作を使用してフォームを実装します。](how-to-implement-a-form-that-uses-a-background-operation.md)
- [.NET Framework でのカスタムの Windows フォーム コントロールを開発します。](developing-custom-windows-forms-controls.md)
