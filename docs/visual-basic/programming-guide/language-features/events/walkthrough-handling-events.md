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
ms.openlocfilehash: 2ae32f0ac31c504e86d5cf39ed6a36cc5523a4a0
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308563"
---
# <a name="walkthrough-handling-events-visual-basic"></a>チュートリアル: イベントの処理 (Visual Basic)
これは、2 番目のイベントを使用する方法を示す 2 つのトピックです。 最初のトピックでは、[チュートリアル。イベントを宣言して発生](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)を宣言してイベントを発生させる方法を示しています。 このセクションでは、実行するときにイベントを処理するのに方法について説明フォームとそのチュートリアルからクラスを使用します。  
  
 `Widget`クラスの例は、従来のイベント処理ステートメントを使用します。 Visual Basic では、イベントの処理を他の手法を提供します。 演習として使用するには、この例を変更することができます、`AddHandler`と`Handles`ステートメント。  
  
### <a name="to-handle-the-percentdone-event-of-the-widget-class"></a>ウィジェットのクラスのことですイベントを処理するには  
  
1. 次のコードを配置`Form1`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#4)]  
  
     `WithEvents`キーワードを指定する変数`mWidget`オブジェクトのイベントを処理するために使用します。 オブジェクトの種類を指定するには、オブジェクトを作成するクラスの名前を指定します。  
  
     変数`mWidget`で宣言されている`Form1`ため`WithEvents`変数はクラス レベルである必要があります。 これはクラスの配置の種類に関係なく当てはまります。  
  
     変数`mblnCancel`をキャンセルするために使用、`LongTask`メソッド。  
  
## <a name="writing-code-to-handle-an-event"></a>イベントを処理するコードの記述  
 使用して変数を宣言するとすぐに`WithEvents`、クラスの左側のドロップダウン リストで、変数名が表示されます。**コード エディター**します。 選択すると`mWidget`、`Widget`クラスのイベントが右のドロップダウン リストに表示されます。 イベントを選択するには、プレフィックスを持つ、対応するイベント プロシージャが表示されます`mWidget`とアンダー スコア。 関連付けられているすべてのイベント プロシージャを`WithEvents`変数は、プレフィックスとして変数名を指定します。  
  
#### <a name="to-handle-an-event"></a>イベントを処理するには  
  
1. 選択`mWidget`で、左側のドロップダウン リストから、**コード エディター**します。  
  
2. 選択、`PercentDone`右のドロップダウン リストからイベント。 **コード エディター**開きます、`mWidget_PercentDone`イベント プロシージャ。  
  
    > [!NOTE]
    >  **コード エディター**は役立ちますが、新しいイベント ハンドラーを挿入するための必要ありません。 このチュートリアルでは、イベント ハンドラーのコードに直接コピーするより直接的します。  
  
3. `mWidget_PercentDone` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#5)]  
  
     たびに、`PercentDone`イベントは、イベント プロシージャの完了率が表示されます、`Label`コントロール。 `DoEvents`メソッドを再描画するラベルを使用し、また、ユーザーがクリックする可能性、**キャンセル**ボタンをクリックします。  
  
4. 次のコードを追加、`Button2_Click`イベント ハンドラー。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#6)]  
  
 ユーザーがクリックした場合、**キャンセル**中にボタン`LongTask`が実行されている、`Button2_Click`イベントが実行されるとすぐに、`DoEvents`ステートメントが発生するイベントの処理を使用できます。 クラス レベルの変数`mblnCancel`に設定されている`True`、および`mWidget_PercentDone`イベントは、ためのテストし、設定、`ByRef Cancel`引数`True`。  
  
## <a name="connecting-a-withevents-variable-to-an-object"></a>WithEvents 変数をオブジェクトに接続します。  
 `Form1` 処理するために設定するようになりました、`Widget`オブジェクトのイベント。 残っているは検索、`Widget`どこか。  
  
 変数を宣言するときに`WithEvents`デザイン時にオブジェクトが関連付けられていないこと。 A`WithEvents`変数は、他のすべてのオブジェクト変数と同じです。 オブジェクトを作成しを使って参照を代入する必要がある、`WithEvents`変数。  
  
#### <a name="to-create-an-object-and-assign-a-reference-to-it"></a>オブジェクトを作成してへの参照を割り当てる  
  
1. 選択 **(Form1 イベント)** で、左側のドロップダウン リストから、**コード エディター**します。  
  
2. 選択、`Load`右のドロップダウン リストからイベント。 **コード エディター**開きます、`Form1_Load`イベント プロシージャ。  
  
3. 次のコードを追加、`Form1_Load`イベント プロシージャを作成、 `Widget`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#7)]  
  
 このコードが実行されると、Visual Basic を作成、`Widget`オブジェクトし、そのイベントを接続に関連付けられているイベント プロシージャに`mWidget`します。 した時点で、ときに、`Widget`を発生させますその`PercentDone`、イベント、`mWidget_PercentDone`イベント プロシージャを実行します。  
  
#### <a name="to-call-the-longtask-method"></a>LongTask メソッドを呼び出す  
  
-   `Button1_Click` イベント ハンドラーに次のコードを追加します。  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#8)]  
  
 前に、`LongTask`メソッドが呼び出されると、ラベルの表示が完了した割合を初期化する必要があり、クラス レベル`Boolean`フラグ設定するメソッドをキャンセルする必要があります`False`します。  
  
 `LongTask` 12.2 秒のタスクの実行時間と呼びます。 `PercentDone`イベントは、1 回ごとに 3 分の 1、2 つ目の。 イベントが発生すると、毎回、`mWidget_PercentDone`イベント プロシージャを実行します。  
  
 ときに`LongTask`が完了したら、`mblnCancel`かどうかをテスト`LongTask`通常は、終了したため、停止した場合、または`mblnCancel`に設定された`True`。 達成率は、前者の場合にのみ更新されます。  
  
#### <a name="to-run-the-program"></a>プログラムを実行するには  
  
1. F5 キーを押して、実行モードで、プロジェクトを配置します。  
  
2. をクリックして、**タスクの開始**ボタンをクリックします。 毎回、`PercentDone`イベントは、ラベルは、タスクが完了の割合で更新されます。  
  
3. をクリックして、**キャンセル**タスクを停止するボタンをクリックします。 注意の外観、**キャンセル**ボタンがクリックするとすぐには変更されません。 `Click`イベントまで発生することはできません、`My.Application.DoEvents`ステートメントは、イベント処理を使用できます。  
  
    > [!NOTE]
    >  `My.Application.DoEvents`フォームは、メソッドがまったく同じ方法でイベントを処理できません。 たとえば、このチュートリアルでは、する必要があります をクリックして、**キャンセル**2 回ボタンをクリックします。 使用することができます、イベントを直接処理するためのフォームは、マルチ スレッドです。 詳細については、次を参照してください。[マネージ スレッド処理](../../../../standard/threading/index.md)します。
  
 F11 キーを押してプログラムを実行し、コードを 1 行ずつ処理するときにあります。 実行の入力を明確に確認`LongTask`、し、簡単に再入力`Form1`たびに、`PercentDone`イベントが発生します。  
  
 何が起こる場合、実行中のコードに戻る`Form1`、`LongTask`メソッドが再度呼び出されたでしょうか。 場合、スタック オーバーフローが発生する最悪の場合、`LongTask`イベントが発生するたびに呼び出されました。  
  
 変数が可能性`mWidget`、別のイベントを処理する`Widget`新しいへの参照を割り当てることでオブジェクト`Widget`に`mWidget`します。 コードでは、実際には、行うことができます`Button1_Click`ボタンをクリックするたびにこの操作を行います。  
  
#### <a name="to-handle-events-for-a-different-widget"></a>別のウィジェットのイベントを処理するには  
  
-   次のコードの行を追加、`Button1_Click`という行のすぐ前に、プロシージャ`mWidget.LongTask(12.2, 0.33)`:  
  
     [!code-vb[VbVbcnWalkthroughDeclaringAndRaisingEvents#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnWalkthroughDeclaringAndRaisingEvents/VB/Form1.vb#9)]  
  
 上記のコードを作成する新しい`Widget`たびにこのボタンをクリックします。 すぐに、`LongTask`メソッドが完了するへの参照、`Widget`がリリースされると、`Widget`は破棄されます。  
  
 A`WithEvents`変数は、一度に 1 つのオブジェクト参照を含めることができます別に割り当てた場合、`Widget`オブジェクトを`mWidget`、前の`Widget`オブジェクトのイベントを処理できなくなります。 場合`mWidget`古いへの参照を格納している唯一のオブジェクト変数`Widget`オブジェクトは破棄されます。 いくつかのイベントを処理する場合`Widget`、オブジェクトを使用して、`AddHandler`ステートメントを個別に各オブジェクトからのイベントを処理します。  
  
> [!NOTE]
>  数を宣言する`WithEvents`変数としてする必要がありますの配列が`WithEvents`変数がサポートされていません。  
  
## <a name="see-also"></a>関連項目

- [チュートリアル: イベントの宣言と発生](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)
- [イベント](../../../../visual-basic/programming-guide/language-features/events/index.md)
