---
title: '方法: Windows フォームコントロールに対してスレッドセーフな呼び出しを行う'
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
ms.openlocfilehash: 78ad7b16d5220972a61848c0c80cd884afa842d9
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928617"
---
# <a name="how-to-make-thread-safe-calls-to-windows-forms-controls"></a>方法: Windows フォームコントロールに対してスレッドセーフな呼び出しを行う

マルチスレッドは Windows フォームアプリのパフォーマンスを向上させることができますが、Windows フォームコントロールへのアクセスは本質的にスレッドセーフではありません。 マルチスレッドでは、非常に深刻で複雑なバグにコードを公開できます。 コントロールを操作する2つ以上のスレッドによって、コントロールが一貫性のない状態になり、競合状態、デッドロック、フリーズまたはハングが発生する可能性があります。 アプリにマルチスレッドを実装する場合は、スレッドセーフな方法でスレッド間コントロールを呼び出すようにしてください。 詳細については、「[マネージスレッド処理のベストプラクティス](../../../standard/threading/managed-threading-best-practices.md)」を参照してください。 

コントロールを作成していないスレッドから Windows フォームコントロールを安全に呼び出すには、2つの方法があります。 <xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName>メソッドを使用して、メインスレッドで作成されたデリゲートを呼び出すことができます。このデリゲートは、コントロールを呼び出します。 または、を実装<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>できます。これは、イベントドリブンモデルを使用して、バックグラウンドスレッドで実行された作業を結果のレポートから分離します。 

## <a name="unsafe-cross-thread-calls"></a>安全でないクロススレッド呼び出し

コントロールを作成していないスレッドから直接呼び出すことは安全ではありません。 次のコードスニペットは、コントロールへの<xref:System.Windows.Forms.TextBox?displayProperty=nameWithType>安全でない呼び出しを示しています。 イベント`Button1_Click`ハンドラーは、メインスレッド`WriteTextUnsafe`の<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType>プロパティを直接設定する新しいスレッドを作成します。 

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

Visual Studio デバッガーは、メッセージを使用してを発生<xref:System.InvalidOperationException>させ、 **スレッド間の操作が無効であることによって、これらのアンセーフスレッド呼び出しを検出します。コントロール "" が作成されたスレッド以外のスレッドからアクセスされました。** は<xref:System.InvalidOperationException> 、Visual Studio のデバッグ中に安全でないクロススレッド呼び出しに対して常に発生し、アプリの実行時に発生する可能性があります。 この問題は解決する必要がありますが、 <xref:System.Windows.Forms.Control.CheckForIllegalCrossThreadCalls%2A?displayProperty=nameWithType>プロパティをに`false`設定することによって例外を無効にすることができます。

## <a name="safe-cross-thread-calls"></a>安全なクロススレッド呼び出し 

次のコード例は、作成されていないスレッドから Windows フォームコントロールを安全に呼び出す2つの方法を示しています。 

1. メソッド<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=fullName> 。このメソッドは、コントロールを呼び出すメインスレッドからデリゲートを呼び出します。 
2. イベントドリブンモデルを提供するコンポーネント。<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> 

どちらの例でも、バックグラウンドスレッドは1秒間スリープして、そのスレッドで実行されている作業をシミュレートします。 

これらの例は、または Visual Basic のC#コマンドラインから .NET Framework アプリとしてビルドして実行できます。 詳細については、「 [csc.exe を使用したコマンドライン](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)からのビルド」または「[コマンドラインからのビルド (Visual Basic)](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)」を参照してください。 

.NET Core 3.0 以降では、ことができますもビルドおよび実行する例では、.NET Core アプリを Windows として .NET Core の Windows フォームのあるフォルダーから *\<フォルダー名>.csproj* プロジェクト ファイル。 

## <a name="example-use-the-invoke-method-with-a-delegate"></a>例:デリゲートで Invoke メソッドを使用する

次の例は、Windows フォームコントロールへのスレッドセーフな呼び出しを保証するパターンを示しています。 このメソッドは<xref:System.Windows.Forms.Control.InvokeRequired%2A?displayProperty=fullName> 、プロパティに対してクエリを行います。これにより、コントロールの作成スレッド id が呼び出し元のスレッド id と比較されます。 スレッド Id が同じである場合は、コントロールを直接呼び出します。 スレッド id が異なる場合は、メインスレッドから<xref:System.Windows.Forms.Control.Invoke%2A?displayProperty=nameWithType>のデリゲートを使用してメソッドを呼び出します。これにより、コントロールへの実際の呼び出しが行われます。

を`SafeCallDelegate`使用すると<xref:System.Windows.Forms.TextBox> 、コントロール<xref:System.Windows.Forms.TextBox.Text%2A>のプロパティを設定できます。 メソッド`WriteTextSafe`がクエリ<xref:System.Windows.Forms.Control.InvokeRequired%2A>を行います。 が<xref:System.Windows.Forms.Control.InvokeRequired%2A> `true` `SafeCallDelegate` を返す<xref:System.Windows.Forms.Control.Invoke%2A>場合は、をメソッドに渡して、コントロールへの実際の呼び出しを行います。`WriteTextSafe` が<xref:System.Windows.Forms.Control.InvokeRequired%2A>を`false`返す`WriteTextSafe`場合は<xref:System.Windows.Forms.TextBox.Text%2A?displayProperty=nameWithType> 、を直接設定します。 イベント`Button1_Click`ハンドラーは、新しいスレッドを作成し、 `WriteTextSafe`メソッドを実行します。 

 [!code-csharp[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#1](~/samples/snippets/winforms/thread-safe/example1/vb/Form1.vb)]  

## <a name="example-use-a-backgroundworker-event-handler"></a>例:BackgroundWorker イベントハンドラーを使用する

マルチスレッドを実装する簡単な方法は<xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType> 、イベントドリブンモデルを使用するコンポーネントです。 バックグラウンドスレッドは、メイン<xref:System.ComponentModel.BackgroundWorker.DoWork?displayProperty=nameWithType>スレッドと対話しないイベントを実行します。 メインスレッドは、メイン<xref:System.ComponentModel.BackgroundWorker.ProgressChanged?displayProperty=nameWithType>スレッド<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted?displayProperty=nameWithType>のコントロールを呼び出すことができるイベントハンドラーとイベントハンドラーを実行します。

を使用<xref:System.ComponentModel.BackgroundWorker>してスレッドセーフな呼び出しを行うには、バックグラウンドスレッドでメソッドを作成して作業を実行し、 <xref:System.ComponentModel.BackgroundWorker.DoWork>イベントにバインドします。 メインスレッドで別のメソッドを作成して、バックグラウンド作業の結果を報告し、イベント<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>または<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベントにバインドします。 バックグラウンドスレッドを開始するには<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A?displayProperty=nameWithType>、を呼び出します。 

この例では<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 、イベントハンドラーを使用<xref:System.Windows.Forms.TextBox>して<xref:System.Windows.Forms.TextBox.Text%2A> 、コントロールのプロパティを設定します。 イベントの<xref:System.ComponentModel.BackgroundWorker.ProgressChanged>使用例については<xref:System.ComponentModel.BackgroundWorker>、「」を参照してください。 

 [!code-csharp[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/cs/Form1.cs)]
 [!code-vb[ThreadSafeCalls#2](~/samples/snippets/winforms/thread-safe/example2/vb/Form1.vb)]  

## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.BackgroundWorker>
- [方法: バックグラウンドで操作を実行する](how-to-run-an-operation-in-the-background.md)
- [方法: バックグラウンド操作を使用するフォームを実装する](how-to-implement-a-form-that-uses-a-background-operation.md)
- [.NET Framework を使用したカスタム Windows フォームコントロールの開発](developing-custom-windows-forms-controls.md)
