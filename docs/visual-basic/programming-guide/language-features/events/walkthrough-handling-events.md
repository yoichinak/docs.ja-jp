---
title: イベントの処理 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- event handling [Visual Basic], walkthroughs
- walkthroughs [Visual Basic], event handling
- variables [Visual Basic], WithEvents
- events [Visual Basic], walkthroughs
- WithEvents keyword [Visual Basic], walkthroughs
- event handlers [Visual Basic], walkthroughs
ms.assetid: f145b3fc-5ae0-4509-a2aa-1ff6934706bd
ms.openlocfilehash: 12267e0a70419298bc581421c4f3a220088d205f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956309"
---
# <a name="walkthrough-handling-events-visual-basic"></a>チュートリアル: イベントの処理 (Visual Basic)
これは、イベントを操作する方法を示す2つのトピックのうち2番目のトピックです。 最初のトピック[「チュートリアル:イベント](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)の宣言と発生、イベントを宣言して発生させる方法について説明します。 このセクションでは、そのチュートリアルのフォームとクラスを使用して、発生したイベントの処理方法を示します。  
  
 クラス`Widget`の例では、従来のイベント処理ステートメントを使用します。 Visual Basic には、イベントを操作するためのその他の手法が用意されています。 演習として、この例を変更`AddHandler`して、ステートメントと`Handles`ステートメントを使用することができます。  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>ウィジェットクラスの PercentDone イベントを処理するには  
  
1. に`Form1`次のコードを配置します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     キーワードは、変数`mWidget`がオブジェクトのイベントを処理するために使用されることを指定します。 `WithEvents` オブジェクトの種類を指定するには、オブジェクトの作成元となるクラスの名前を指定します。  
  
     変数はクラスレベルで`Form1`ある`WithEvents`必要があるため、ではとして宣言されています。 `mWidget` これは、配置したクラスの型に関係なく当てはまります。  
  
     変数`mblnCancel`は、 `LongTask`メソッドを取り消すために使用されます。  
  
## <a name="writing-code-to-handle-an-event"></a>イベントを処理するコードの記述  
 を使用し`WithEvents`て変数を宣言するとすぐに、クラスの**コードエディター**の左側のドロップダウンリストに変数名が表示されます。 を選択`mWidget`すると、 `Widget`クラスのイベントが右のドロップダウンリストに表示されます。 イベントを選択すると、対応するイベントプロシージャがプレフィックス`mWidget`とアンダースコア付きで表示されます。 `WithEvents`変数に関連付けられているすべてのイベントプロシージャには、プレフィックスとして変数名が割り当てられます。  
  
#### <a name="to-handle-an-event"></a>イベントを処理するには  
  
1. `mWidget` **コードエディター**の左側のドロップダウンリストからを選択します。  
  
2. 右側のドロップダウンリストからイベントを選択します。`PercentDone` **コードエディター**で`mWidget_PercentDone`イベントプロシージャが開きます。  
  
    > [!NOTE]
    > **コードエディター**は、新しいイベントハンドラーを挿入する場合には便利ですが、必須ではありません。 このチュートリアルでは、コードに直接イベントハンドラーをコピーするだけで済みます。  
  
3. `mWidget_PercentDone` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     イベントが`PercentDone`発生するたびに、イベントプロシージャによって`Label`コントロールの完了率が表示されます。 メソッドを使用すると、ラベルを再描画できます。また、ユーザーは [キャンセル] ボタンをクリックすることもできます。 `DoEvents`  
  
4. `Button2_Click`イベントハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 が実行`LongTask` `DoEvents`されているときにユーザーが **[キャンセル**] ボタンをクリックすると、イベントは、ステートメントによってイベント処理が許可されるとすぐに実行されます。 `Button2_Click` クラスレベル`mblnCancel`変数がに`mWidget_PercentDone` `True`設定されている場合、イベントはそれをテストし`ByRef Cancel` 、引数`True`をに設定します。  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>WithEvents 変数をオブジェクトに接続する  
 `Form1`は、オブジェクトのイベントを`Widget`処理するように設定されました。 残っているのは、 `Widget`どこかを見つけることだけです。  
  
 デザイン時に変数`WithEvents`を宣言しても、オブジェクトにはオブジェクトが関連付けられていません。 変数`WithEvents`は、他のオブジェクト変数と同じです。 オブジェクトを作成し、そのオブジェクトへの`WithEvents`参照を変数で割り当てる必要があります。  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>オブジェクトを作成し、そのオブジェクトへの参照を割り当てるには  
  
1. **コードエディター**の左側のドロップダウンリストで **[(Form1 イベント)]** を選択します。  
  
2. 右側のドロップダウンリストからイベントを選択します。`Load` **コードエディター**で`Form1_Load`イベントプロシージャが開きます。  
  
3. `Form1_Load`イベントプロシージャに次のコードを追加して、 `Widget`を作成します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 このコードが実行されると、 `Widget` Visual Basic がオブジェクトを作成し、そのイベントをに`mWidget`関連付けられたイベントプロシージャに接続します。 その時点から、によっ`Widget`て`PercentDone`イベント`mWidget_PercentDone`が発生するたびに、イベントプロシージャが実行されます。  
  
#### <a name="to-call-the-longtask-method"></a>LongTask メソッドを呼び出すには  
  
- `Button1_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 メソッドが呼び出される前に、完了率を示すラベルを初期化する必要があります。また、 `Boolean`メソッドをキャンセルするためのクラスレベルの`False`フラグをに設定する必要があります。 `LongTask`  
  
 `LongTask`は、タスク期間が12.2 秒の場合に呼び出されます。 `PercentDone`イベントは、1秒間に1回発生します。 イベントが発生するたびに`mWidget_PercentDone` 、イベントプロシージャが実行されます。  
  
 が`LongTask`終了すると`mblnCancel` 、 `LongTask`は、が正常に終了したかどうか、 `mblnCancel`またはが`True`に設定されたために停止したかどうかをテストします。 完了率は、前者の場合にのみ更新されます。  
  
#### <a name="to-run-the-program"></a>プログラムを実行するには  
  
1. F5 キーを押して、プロジェクトを実行モードにします。  
  
2. **[タスクの開始]** ボタンをクリックします。 `PercentDone`イベントが発生するたびに、ラベルは、完了したタスクの割合で更新されます。  
  
3. **[キャンセル]** ボタンをクリックして、タスクを停止します。 **[キャンセル]** ボタンの外観は、クリックしてもすぐには変更されないことに注意してください。 イベント`Click`は、ステートメントによっ`My.Application.DoEvents`てイベント処理が許可されるまで発生しません。  
  
    > [!NOTE]
    > `My.Application.DoEvents`メソッドは、フォームとまったく同じ方法でイベントを処理しません。 たとえば、このチュートリアルでは、 **[キャンセル]** ボタンを2回クリックする必要があります。 フォームがイベントを直接処理できるようにするには、マルチスレッドを使用します。 詳細については、「[マネージスレッド処理](../../../../standard/threading/index.md)」を参照してください。
  
 F11 キーを使用してプログラムを実行し、一度に1行ずつコードをステップ実行することをお勧めします。 実行`LongTask`がどのように行われるかを明確に確認し、 `Form1` `PercentDone`イベントが発生するたびに簡単に再入力することができます。  
  
 `Form1`の`LongTask`コードで実行が戻ったときに、メソッドが再度呼び出された場合はどうなるでしょうか。 最悪の場合`LongTask` 、イベントが発生するたびにが呼び出されると、スタックオーバーフローが発生する可能性があります。  
  
 `mWidget` `Widget`新しい`mWidget`への参照をに割り当てることによって、変数が別のオブジェクトのイベントを処理するようにすることができます。 `Widget` 実際には、ボタンをクリックするたび`Button1_Click`に、このコードを作成できます。  
  
#### <a name="to-handle-events-for-a-different-widget"></a>別のウィジェットのイベントを処理するには  
  
- `Button1_Click`プロシージャに次のコード行を追加し`mWidget.LongTask(12.2, 0.33)`ます。行の直前にを記述します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 上記のコードでは、 `Widget`ボタンがクリックされるたびに新しいが作成されます。 `LongTask`メソッドが完了するとすぐに、への`Widget`参照`Widget`が解放され、が破棄されます。  
  
 変数には一度に1つのオブジェクト参照のみを含めることができます。 `Widget`したがって`mWidget`、別の`Widget`オブジェクトをに割り当てると、前のオブジェクトのイベントは処理されなくなります。 `WithEvents` が`mWidget` 古い`Widget`への参照を含む唯一のオブジェクト変数である場合は、オブジェクトが破棄されます。 複数`Widget`のオブジェクトのイベントを処理する場合は、ステートメント`AddHandler`を使用して各オブジェクトのイベントを個別に処理します。  
  
> [!NOTE]
> 必要な数`WithEvents`の変数を宣言できますが、変数の`WithEvents`配列はサポートされていません。  
  
## <a name="see-also"></a>関連項目

- [チュートリアル: イベントの宣言と発生](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
