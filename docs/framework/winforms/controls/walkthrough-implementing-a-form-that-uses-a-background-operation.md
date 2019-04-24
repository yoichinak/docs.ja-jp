---
title: 'チュートリアル: バックグラウンド操作を使用するフォームの実装'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- threading [Windows Forms], walkthroughs
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 4691b796-9200-471a-89c3-ba4c7cc78c03
ms.openlocfilehash: 6399fb853162174895d892399fd3eb5226101515
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59343403"
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a>チュートリアル: バックグラウンド操作を使用するフォームの実装
場合は、完了に長い時間がかかる操作があると応答を停止する、ユーザー インターフェイス (UI) を設定したくない、または「ハング」しを使用できます、<xref:System.ComponentModel.BackgroundWorker>クラスを別のスレッドで操作を実行します。  
  
 このチュートリアルで使用する方法、 <xref:System.ComponentModel.BackgroundWorker> ""バック グラウンドで時間のかかる計算を実行するクラス、ユーザー インターフェイスの応答性の高いままです。  このチュートリアルを完了すると、フィボナッチ数を非同期に計算するアプリケーションが作成されます。 大きなフィボナッチ数の計算にはかなりの時間がかかることがありますが、この遅延によってメイン UI スレッドが中断されることはなく、計算中もフォームは応答性を維持します。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   Windows ベースのアプリケーションの作成  
  
-   作成、<xref:System.ComponentModel.BackgroundWorker>フォーム  
  
-   非同期イベント ハンドラーの追加  
  
-   進行状況の報告とキャンセルのサポートの追加  
  
 この例で使用するコードの完全な一覧については、次を参照してください。[方法。バック グラウンド操作を使用してフォームを実装する](how-to-implement-a-form-that-uses-a-background-operation.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
## <a name="creating-the-project"></a>プロジェクトの作成  
 まず、プロジェクトを作成し、フォームを設定します。  
  
#### <a name="to-create-a-form-that-uses-a-background-operation"></a>バックグラウンド操作を使用するフォームを作成するには  
  
1. という名前の Windows ベースのアプリケーション プロジェクトを作成する`BackgroundWorkerExample`(**ファイル** > **新規** > **プロジェクト** >  **Visual c#** または**Visual Basic** > **クラシック デスクトップ** > **Windows フォーム アプリケーション**)。  
  
2. **ソリューション エクスプローラー**で、**[Form1]** を右クリックし、ショートカット メニューの **[名前の変更]** をクリックします。 ファイル名を `FibonacciCalculator` に変更します。 コード要素 "`Form1`" へのすべての参照の名前を変更するかどうかをたずねられたら、**[はい]** をクリックします。  
  
3. ドラッグ、<xref:System.Windows.Forms.NumericUpDown>コントロールから、**ツールボックス**フォーム上にします。 設定、<xref:System.Windows.Forms.NumericUpDown.Minimum%2A>プロパティを`1`と<xref:System.Windows.Forms.NumericUpDown.Maximum%2A>プロパティを`91`します。  
  
4. 2 つ追加<xref:System.Windows.Forms.Button>フォームのコントロール。  
  
5. 最初の名前を変更<xref:System.Windows.Forms.Button>コントロール`startAsyncButton`設定と、<xref:System.Windows.Forms.Control.Text%2A>プロパティを`Start Async`します。 2 つ目の名前を変更<xref:System.Windows.Forms.Button>コントロール`cancelAsyncButton`、設定、<xref:System.Windows.Forms.Control.Text%2A>プロパティを`Cancel Async`します。 設定の<xref:System.Windows.Forms.Control.Enabled%2A>プロパティを`false`します。  
  
6. この 2 つのイベント ハンドラーを作成、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>イベント。 詳細については、「[方法: デザイナーを使用してイベント ハンドラーを作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))します。  
  
7. ドラッグ、<xref:System.Windows.Forms.Label>コントロールから、**ツールボックス**をフォームに名前を変更し、`resultLabel`します。  
  
8. ドラッグ、<xref:System.Windows.Forms.ProgressBar>コントロールから、**ツールボックス**フォーム上にします。  
  
## <a name="creating-a-backgroundworker-in-your-form"></a>フォームでの BackgroundWorker の作成  
 作成することができます、<xref:System.ComponentModel.BackgroundWorker>を使用して、非同期操作の**Windows** **フォーム デザイナー**します。  
  
#### <a name="to-create-a-backgroundworker-with-the-designer"></a>デザイナーを使用して BackgroundWorker を作成するには  
  
-   **コンポーネント**のタブ、**ツールボックス**、ドラッグ、<xref:System.ComponentModel.BackgroundWorker>フォーム上にします。  
  
## <a name="adding-asynchronous-event-handlers"></a>非同期イベント ハンドラーの追加  
 イベント ハンドラーを追加する準備が整いました、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの非同期イベント。 バックグラウンドで実行される時間のかかる操作 (フィボナッチ数の計算) は、これらのイベント ハンドラーのいずれかによって呼び出されます。  
  
#### <a name="to-implement-asynchronous-event-handlers"></a>非同期イベント ハンドラーを実装するには  
  
1. **プロパティ** ウィンドウで、<xref:System.ComponentModel.BackgroundWorker>が選択されているコンポーネントをクリックして、**イベント**ボタン。 ダブルクリックして、<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベントをイベント ハンドラーを作成します。 イベント ハンドラーを使用する方法の詳細については、次を参照してください。[方法。デザイナーを使用してイベント ハンドラーを作成する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/zwwsdtbk(v=vs.100))します。  
  
2. フォームで `ComputeFibonacci` という新しいメソッドを作成します。 このメソッドがバックグラウンドで実行され、実際の処理を行います。 このコードは、フィボナッチ アルゴリズムの再帰的実装を示しています。これは、非常に非効率であり、数が大きくなるにつれて、完了までの所要時間が急激に増大します。 ここでは、アプリケーションで長時間の遅延が発生する可能性のある操作を示すために、このコードを使用しています。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3. <xref:System.ComponentModel.BackgroundWorker.DoWork>イベント ハンドラー呼び出しを追加、`ComputeFibonacci`メソッド。 最初のパラメーターを受け取る`ComputeFibonacci`から、<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>のプロパティ、<xref:System.ComponentModel.DoWorkEventArgs>します。 <xref:System.ComponentModel.BackgroundWorker>と<xref:System.ComponentModel.DoWorkEventArgs>パラメーターが進行状況の報告とキャンセルの後で使用をサポートします。 戻り値を割り当てる`ComputeFibonacci`を<xref:System.ComponentModel.DoWorkEventArgs.Result%2A>のプロパティ、<xref:System.ComponentModel.DoWorkEventArgs>します。 この結果は、使用可能になります、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント ハンドラー。  
  
    > [!NOTE]
    >  <xref:System.ComponentModel.BackgroundWorker.DoWork>イベント ハンドラーを参照していません、`backgroundWorker1`の特定のインスタンスにこのイベント ハンドラーを結合はこのように、変数を直接インスタンス<xref:System.ComponentModel.BackgroundWorker>します。 代わりへの参照、<xref:System.ComponentModel.BackgroundWorker>これが発生したイベントがから復元、`sender`パラメーター。 これは、1 つ以上のフォームがホストされる場合に重要な<xref:System.ComponentModel.BackgroundWorker>します。 内の任意のユーザー インターフェイス オブジェクトを操作しないようにする重要なも、<xref:System.ComponentModel.BackgroundWorker.DoWork>イベント ハンドラー。 代わりに、を通じてユーザー インターフェイスとの通信、<xref:System.ComponentModel.BackgroundWorker>イベント。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4. `startAsyncButton`コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラー、非同期操作を開始するコードを追加します。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5. <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント ハンドラーでは、計算の結果に割り当てる、`resultLabel`コントロール。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## <a name="adding-progress-reporting-and-support-for-cancellation"></a>進行状況の報告とキャンセルのサポートの追加  
 時間のかかる非同期操作では、多くの場合、進行状況をユーザーに報告し、ユーザーが操作をキャンセルできるようにすることが望まれます。 <xref:System.ComponentModel.BackgroundWorker>クラスは、バック グラウンド操作処理の進行状況の進行状況を投稿できるイベントを提供します。 呼び出しを検出するために、ワーカー コードを許可するフラグも用意されています。<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>自体を中断するとします。  
  
#### <a name="to-implement-progress-reporting"></a>進行状況の報告を実装するには  
  
1. **[プロパティ]** ウィンドウで `backgroundWorker1` を選択します。 <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> と <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> プロパティを `true` に設定します。  
  
2. `FibonacciCalculator` フォームで 2 つの変数を宣言します。 これらの変数を使用して進行状況を追跡します。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3. <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベントのイベント ハンドラーを追加します。 <xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント ハンドラー、update、<xref:System.Windows.Forms.ProgressBar>で、<xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A>のプロパティ、<xref:System.ComponentModel.ProgressChangedEventArgs>パラメーター。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### <a name="to-implement-support-for-cancellation"></a>キャンセルのサポートを実装するには  
  
1. `cancelAsyncButton`コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラー、非同期操作をキャンセルするコードを追加します。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2. `ComputeFibonacci` メソッドの次のコード フラグメントは、進行状況の報告とキャンセルのサポートを示しています。  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## <a name="checkpoint"></a>チェックポイント  
 この時点で、フィボナッチ電卓アプリケーションをコンパイルして実行できます。  
  
#### <a name="to-test-your-project"></a>プロジェクトをテストするには  
  
-   F5 キーを押してアプリケーションをコンパイルし、実行します。  
  
     計算がバック グラウンドで実行しているときに表示されます、<xref:System.Windows.Forms.ProgressBar>完了するまでの進行状況を表示します。 また、保留中の操作をキャンセルすることもできます。  
  
     数値が小さい場合、計算に時間はかかりませんが、数値が大きくなると、大幅な遅延が発生します。 30 以上の値を入力した場合、コンピューターの速度によっては数秒の遅延が発生します。 値が 40 を超えると、計算が終了するまでに数分から数時間かかることがあります。 電卓が大きなフィボナッチ数を計算している間も、フォームの移動、最小化、最大化を自由に行うことができ、フォームを閉じることもできます。 これは、メイン UI スレッドが計算の終了を待機していないためです。  
  
## <a name="next-steps"></a>次の手順  
 使用するフォームを実装している、<xref:System.ComponentModel.BackgroundWorker>バック グラウンドで計算を実行するコンポーネントの他の非同期操作の可能性を調べることができます。  
  
-   複数回使用<xref:System.ComponentModel.BackgroundWorker>複数の同時操作のオブジェクト。  
  
-   マルチ スレッド アプリケーションをデバッグするを参照してください。[方法。[スレッド] ウィンドウを使用して、](/visualstudio/debugger/how-to-use-the-threads-window)します。  
  
-   非同期プログラミング モデルをサポートする独自のコンポーネントを実装する。 詳細については、「[イベント ベースの非同期パターンの概要](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)」を参照してください。  
  
    > [!CAUTION]
    >  どのような種類のマルチスレッドを使用している場合でも、非常に深刻で複雑なバグを引き起こしてしまう可能性があります。 マルチスレッドを使用するソリューションを実装する前に、「[マネージド スレッド処理の実施](../../../standard/threading/managed-threading-best-practices.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ComponentModel.BackgroundWorker?displayProperty=nameWithType>
- [マネージド スレッド処理](../../../standard/threading/index.md)
- [マネージド スレッド処理の実施](../../../standard/threading/managed-threading-best-practices.md)
- [イベントベースの非同期パターンの概要](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [方法: バックグラウンド操作を使用するフォームを実装する](how-to-implement-a-form-that-uses-a-background-operation.md)
- [チュートリアル: バック グラウンドで操作を実行します。](walkthrough-running-an-operation-in-the-background.md)
- [BackgroundWorker コンポーネント](backgroundworker-component.md)
