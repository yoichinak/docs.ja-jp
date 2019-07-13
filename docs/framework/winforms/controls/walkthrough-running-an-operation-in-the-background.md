---
title: 'チュートリアル: 操作をバックグラウンドで実行する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
ms.openlocfilehash: 6c705c6d6ff9bbd233bbddc3a73acf8aca13a547
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211524"
---
# <a name="walkthrough-running-an-operation-in-the-background"></a>チュートリアル: 操作をバックグラウンドで実行する

完了に長い時間がかかる操作を実行しており、ユーザー インターフェイスで遅延が発生しないようにするには<xref:System.ComponentModel.BackgroundWorker> クラスを使用して別のスレッドで操作を実行できます。

この例で使用するコードの完全な一覧については、次を参照してください。[方法。バックグラウンドで操作を実行する](how-to-run-an-operation-in-the-background.md)」を参照してください。

## <a name="run-an-operation-in-the-background"></a>バック グラウンドで操作を実行します。

1. 2 つの Visual Studio での Windows フォーム デザイナーでアクティブなフォームにドラッグ<xref:System.Windows.Forms.Button>コントロールを**ツールボックス**フォームを設定して、`Name`と<xref:System.Windows.Forms.Control.Text%2A>に従って、ボタンのプロパティ、次の表にします。

    |ボタン|名前|テキスト|
    |------------|----------|----------|
    |`button1`|`startBtn`|**[開始]**|
    |`button2`|`cancelBtn`|**キャンセル**|

2. 開く、**ツールボックス**、クリックして、**コンポーネント**タブをクリックし、ドラッグ、<xref:System.ComponentModel.BackgroundWorker>コンポーネントをフォームにします。

     `backgroundWorker1`コンポーネントに表示されます、**コンポーネント トレイ**します。

3. **[プロパティ]** ウィンドウで、 <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> プロパティを `true`に設定します。

4. **プロパティ**ウィンドウの**イベント**ボタンをクリックし、ダブルクリック、<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベントをイベント ハンドラーを作成します。

5. 挿入に時間のかかるコード、<xref:System.ComponentModel.BackgroundWorker.DoWork>イベント ハンドラー。

6. 操作に必要なすべてのパラメーターを抽出、<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>のプロパティ、<xref:System.ComponentModel.DoWorkEventArgs>パラメーター。

7. 計算の結果に割り当てる、<xref:System.ComponentModel.DoWorkEventArgs.Result%2A>のプロパティ、<xref:System.ComponentModel.DoWorkEventArgs>します。

     これは使用できる、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント ハンドラー。

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]

8. 操作の結果を取得するためのコードを挿入、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント ハンドラー。

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]

9. `TimeConsumingOperation` メソッドを実装します。

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]

10. Windows フォーム デザイナーで、ダブルクリック`startButton`を作成する、<xref:System.Windows.Forms.Control.Click>イベント ハンドラー。

11. 呼び出す、<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>メソッドで、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー`startButton`します。

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]

12. Windows フォーム デザイナーで、ダブルクリック`cancelButton`を作成する、<xref:System.Windows.Forms.Control.Click>イベント ハンドラー。

13. 呼び出す、<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>メソッドで、<xref:System.Windows.Forms.Control.Click>のイベント ハンドラー`cancelButton`します。

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]

14. ファイルの上部にある、System.ComponentModel および System.Threading 名前空間をインポートします。

     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]

15. キーを押して**F6**ソリューションをビルドし、キーを押します**Ctrl**+**f5 キーを押して**デバッガーの外部のアプリケーションを実行します。

    > [!NOTE]
    > キーを押す場合**F5**で、デバッガーの下でアプリケーションを実行する、例外が発生した、`TimeConsumingOperation`メソッドがキャッチされ、デバッガーによって表示されます。 デバッガーの外部のアプリケーションを実行すると、 <xref:System.ComponentModel.BackgroundWorker> 、例外を処理し、キャッシュで、<xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>のプロパティ、<xref:System.ComponentModel.RunWorkerCompletedEventArgs>します。

16. をクリックして、**開始**、非同期操作を実行するボタンをクリックし、をクリックし、**キャンセル**実行中の非同期操作を停止するボタンをクリックします。

     各操作の結果は、<xref:System.Windows.Forms.MessageBox> に表示されます。

## <a name="next-steps"></a>次の手順

- 非同期操作の進行に伴って進行状況を報告するフォームを実装します。 詳細については、「[方法 :バック グラウンド操作を使用してフォームを実装する](how-to-implement-a-form-that-uses-a-background-operation.md)します。

- コンポーネントの非同期パターンをサポートするクラスを実装します。 詳細については、次を参照してください。[イベント ベースの非同期パターンを実装する](../../../standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)します。

## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [方法: バックグラウンド操作を使用するフォームを実装する](how-to-implement-a-form-that-uses-a-background-operation.md)
- [方法: バックグラウンドで操作を実行する](how-to-run-an-operation-in-the-background.md)
- [BackgroundWorker コンポーネント](backgroundworker-component.md)
