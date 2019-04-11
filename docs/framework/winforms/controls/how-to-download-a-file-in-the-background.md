---
title: '方法: バックグラウンドでファイルをダウンロードする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BackgroundWorker component
- background tasks
- Asynchronous Pattern
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9b7bc5ae-051c-4904-9720-18f6667388bd
ms.openlocfilehash: af5a607b4800635d096e83b55a5bd5a912c8538d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128779"
---
# <a name="how-to-download-a-file-in-the-background"></a>方法: バックグラウンドでファイルをダウンロードする
ファイルのダウンロードは一般的なタスクであり、時間のかかる可能性があるこの操作を別のスレッドで実行すると便利です。 ごくわずかなコードでこのタスクを実行するには、<xref:System.ComponentModel.BackgroundWorker> コンポーネントを使用します。  
  
## <a name="example"></a>例  
 次のコード例は、<xref:System.ComponentModel.BackgroundWorker> コンポーネントを使用して、URL からの XML ファイルを読み込む方法を示しています。 ユーザーがクリックしたとき、**ダウンロード**ボタン、<xref:System.Windows.Forms.Control.Click>イベント ハンドラーの呼び出し、<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>のメソッドを<xref:System.ComponentModel.BackgroundWorker>コンポーネント ダウンロード操作を開始します。 ダウンロード中はボタンが無効になり、ダウンロードが完了すると有効になります。 <xref:System.Windows.Forms.MessageBox> にファイルの内容が表示されます。  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#1)]  
  
 **ファイルのダウンロード**  
  
 ファイルが <xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラーを実行する <xref:System.ComponentModel.BackgroundWorker> コンポーネントのワーカー スレッドにダウンロードされます。 このスレッドは、コードが <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> メソッドを呼び出すときに開始されます。  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#3)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#3)]  
  
 **完了する BackgroundWorker を待機する**  
  
 `downloadButton_Click` イベント ハンドラーが <xref:System.ComponentModel.BackgroundWorker> コンポーネントの非同期タスクの終了を待機する方法を示します。  
  
 アプリケーションがイベントへの応答のみを実行し、バック グラウンド スレッドを待機している間にメイン スレッドでその他の作業を実行しないようにする場合は、ハンドラーを終了します。  
  
 メイン スレッドで処理を続行する場合は、<xref:System.ComponentModel.BackgroundWorker.IsBusy%2A> プロパティを使用して、<xref:System.ComponentModel.BackgroundWorker> スレッドをまだ実行するかどうかを決定します。 例では、ダウンロードの処理中に、進行状況バーが更新されます。 必ず <xref:System.Windows.Forms.Application.DoEvents%2A?displayProperty=nameWithType> メソッドを呼び出して、UI 応答性を維持してください。  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#2)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#2)]  
  
 **結果の表示**  
  
 `backgroundWorker1_RunWorkerCompleted` メソッドは、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベントを処理し、バック グラウンド操作が完了したときに呼び出されます。 このメソッドはまず、<xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> プロパティを確認します。 <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> が `null` の場合に、このメソッドはファイルの内容を表示します。 これで、ダウンロードを開始したときに無効になっていた [ダウンロード] ボタンが有効になり、進行状況バーがリセットされます。  
  
 [!code-csharp[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/CS/Form1.cs#4)]
 [!code-vb[System.ComponentModel.BackgroundWorker.IsBusy#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.IsBusy/VB/Form1.vb#4)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System.Drawing、System.Windows.Forms、および System.Xml の各アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual C# の構築方法の詳細については、[、コマンドラインからビルドする](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)を参照してください。 新しいプロジェクトにコードを貼り付けることによって、この例では、Visual Studio を構築することもできます。  
  
## <a name="robust-programming"></a>信頼性の高いプログラミング  
 <xref:System.ComponentModel.BackgroundWorker.DoWork> イベント ハンドラーにより影響を受けている可能性がある <xref:System.ComponentModel.RunWorkerCompletedEventArgs.Result%2A?displayProperty=nameWithType> プロパティまたはその他のオブジェクトへのアクセスを試みる前に、常に <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> イベント ハンドラーの <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A?displayProperty=nameWithType> プロパティを確認してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.BackgroundWorker>
- [方法: バックグラウンドで操作を実行する](how-to-run-an-operation-in-the-background.md)
- [方法: バックグラウンド操作を使用するフォームを実装する](how-to-implement-a-form-that-uses-a-background-operation.md)
