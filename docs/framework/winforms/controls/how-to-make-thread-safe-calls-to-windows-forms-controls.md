---
title: コントロールへのスレッド セーフな呼び出しを行う
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
ms.openlocfilehash: 365b1acb693b9ff2be603a3e659ed8d846a7696a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142005"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>方法 : Windows フォーム コントロールをスレッド セーフに呼び出す

マルチスレッド化は Windows フォーム アプリのパフォーマンスを向上させることができますが、Windows フォーム コントロールへのアクセスは本質的にスレッド セーフではありません。 マルチスレッド化は、コードを非常に深刻で複雑なバグにさらす可能性があります。 コントロールを操作する 2 つ以上のスレッドが、コントロールを強制的に不整合状態にし、競合状態、デッドロック、フリーズまたはハングを引き起こす可能性があります。 アプリにマルチスレッドを実装する場合は、スレッド セーフな方法でスレッド間コントロールを呼び出してください。 詳細については、「マネージ[スレッド化のベスト プラクティス」を参照してください](../../../standard/threading/managed-threading-best-practices.md)。

そのコントロールを作成していないスレッドから Windows フォーム コントロールを安全に呼び出す方法は 2 つあります。 このメソッドを<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>使用して、メイン スレッドで作成されたデリゲートを呼び出し、そのデリゲートを呼び出すことができます。 または、イベント駆動モデルを<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>使用して、バックグラウンド スレッドで実行された作業と結果のレポートを区別する を実装できます。

## <a name="unsafe-cross-thread-calls"></a>安全でないスレッド間呼び出し

コントロールを作成しなかったスレッドから直接コントロールを呼び出すのは安全ではありません。 次のコード スニペットは、コントロールへの安全でない<xref:System.Windows.Forms.TextBox?displayProperty=nameWithType>呼び出しを示しています。 イベント`Button1_Click`ハンドラーは、メイン`WriteTextUnsafe`スレッドの<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>プロパティを直接設定する新しいスレッドを作成します。

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

Visual Studio デバッガーは、メッセージを持つを発生<xref:System.InvalidOperationException>させることによってこれらの安全でないスレッドの呼び出しを検出します,**スレッド間操作が無効です。作成されたスレッド以外のスレッドからアクセスされるコントロール "" 。** 常<xref:System.InvalidOperationException>に、Visual Studio のデバッグ中に安全でないスレッド間呼び出しに発生し、アプリの実行時に発生する可能性があります。 この問題は修正する必要がありますが、プロパティを に設定することで例外<xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType>を無効`false`にできます。

## <a name="safe-cross-thread-calls"></a>安全なスレッド間呼び出し

次のコード例は、Windows フォーム コントロールを作成していないスレッドから安全に呼び出す 2 つの方法を示しています。

1. <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>メイン スレッドからデリゲートを呼び出してコントロールを呼び出すメソッド。
2. イベント<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>駆動モデルを提供するコンポーネント。

どちらの例でも、バックグラウンド スレッドは 1 秒間スリープして、そのスレッドで実行される作業をシミュレートします。

これらの例は、C# または Visual Basic のコマンド ラインから .NET Framework アプリとしてビルドして実行できます。 詳細については、「 [csc.exe を使用したコマンド ラインビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)」または「[コマンド ラインからビルドする (Visual Basic)」](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)を参照してください。

NET Core 3.0 以降では、.NET Core Windows フォーム*\<フォルダー名>.csproj*プロジェクト ファイルを持つフォルダーから Windows .NET Core アプリとしてサンプルをビルドして実行することもできます。

## <a name="example-use-the-invoke-method-with-a-delegate"></a>例: デリゲートで Invoke メソッドを使用する

次の例は、Windows フォーム コントロールへのスレッド セーフな呼び出しを保証するためのパターンを示しています。 このプロパティは、<xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName>コントロールの作成スレッド ID と呼び出し元のスレッド ID を比較します。 スレッド ID が同じ場合は、コントロールを直接呼び出します。 スレッド ID が異なる場合は、メイン<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType>スレッドのデリゲートを使用してメソッドを呼び出し、コントロールを実際に呼び出します。

コントロール`SafeCallDelegate`の<xref:System.Windows.Forms.TextBox.Text%2A>プロパティを<xref:System.Windows.Forms.TextBox>設定できます。 メソッド`WriteTextSafe`は、<xref:System.Windows.Forms.Control.InvokeRequired%2A>を照会します。 が<xref:System.Windows.Forms.Control.InvokeRequired%2A>返`true`された`WriteTextSafe`場合は、 `SafeCallDelegate` <xref:System.Windows.Forms.Control.Invoke%2A>メソッドに渡され、コントロールへの実際の呼び出しが行われます。 を<xref:System.Windows.Forms.Control.InvokeRequired%2A>返`false`す`WriteTextSafe`場合は<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>、直接を設定します。 イベント`Button1_Click`ハンドラーは、新しいスレッドを作成`WriteTextSafe`し、メソッドを実行します。

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>例: バックグラウンドワーカー イベント ハンドラを使用する

マルチスレッドを実装する簡単な方法は、イベント<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>駆動モデルを使用するコンポーネントを使用することです。 バックグラウンド スレッドは、<xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType>メイン スレッドと対話しないイベントを実行します。 メイン スレッドは<xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType>、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType>および イベント ハンドラーを実行し、メイン スレッドのコントロールを呼び出すことができます。

を使用<xref:System.ComponentModel.BackgroundWorker>してスレッド セーフな呼び出しを行うには、バックグラウンド スレッドでメソッドを作成して処理を行い<xref:System.ComponentModel.BackgroundWorker.DoWork>、イベントにバインドします。 メイン スレッドに別のメソッドを作成して、バックグラウンド処理の結果を報告し、 または<xref:System.ComponentModel.BackgroundWorker.ProgressChanged><xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベントにバインドします。 バックグラウンド スレッドを開始するには、<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>を呼び出します。

この例では、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント ハンドラーを使用<xref:System.Windows.Forms.TextBox>してコントロールの<xref:System.Windows.Forms.TextBox.Text%2A>プロパティを設定します。 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベントの使用例については、を参照してください<xref:System.ComponentModel.BackgroundWorker>。

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.BackgroundWorker>
- [方法: 操作をバックグラウンドで実行する](how-to-run-an-operation-in-the-background.md)
- [方法: バックグラウンド操作を使用するフォームを実装する](how-to-implement-a-form-that-uses-a-background-operation.md)
- [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](developing-custom-windows-forms-controls.md)
