---
title: キーボード入力のしくみ
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
ms.openlocfilehash: 4335798395a3b73dbcb2546a6fadac3d8efedb64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204745"
---
# <a name="how-keyboard-input-works"></a>キーボード入力のしくみ
Windows フォームは、Windows メッセージに応答してキーボード イベントを発生させることにより、キーボード入力を処理します。 多くの Windows フォーム アプリケーションは、キーボード イベントを処理することによってキーボード入力を排他的に処理します。 しかし、高度なキーボード入力のシナリオ (キーがコントロールに到達する前にインターセプトするなど) を実装するためには、キーボード メッセージのしくみについて理解することが必要です。 このトピックでは、Windows フォームが認識するキー データの種類について説明し、キーボード メッセージをルーティングする方法について概要を説明します。 キーボード イベントの詳細については、「[キーボード イベントの使用](using-keyboard-events.md)」を参照してください。  
  
## <a name="types-of-keys"></a>キーの種類  
 Windows フォームでは、キーボード入力を識別、ビット単位で表される仮想キー コードとして<xref:System.Windows.Forms.Keys>列挙体。 <xref:System.Windows.Forms.Keys>列挙型で、一連の押されたキーを 1 つの値を組み合わせることができます。 これらの値は、WM_KEYDOWN および WM_SYSKEYDOWN の Windows メッセージに付随する値になります。 大半の物理キーの押下を検出するには処理することによって、<xref:System.Windows.Forms.Control.KeyDown>または<xref:System.Windows.Forms.Control.KeyUp>イベント。 文字のキーのサブセットである、<xref:System.Windows.Forms.Keys>列挙し、WM_CHAR および WM_SYSCHAR の Windows メッセージに付随する値に対応します。 押されたキーの組み合わせ文字の場合、処理することにより、文字を検出できます、<xref:System.Windows.Forms.Control.KeyPress>イベント。 また、使用することができます<xref:Microsoft.VisualBasic.Devices.Keyboard>、どのキーが押されたを探索し、キーを送信し、Visual Basic プログラミング インターフェイスによって公開されています。 詳細については、「[Accessing the Keyboard (キーボードへのアクセス)](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)」を参照してください。  
  
## <a name="order-of-keyboard-events"></a>キーボード イベントの順序  
 先に説明したとおり、コントロール上では 3 つのキーボード関連のイベントが発生します。 イベントは一般に次の順序で発生します。  
  
1.  ユーザーにプッシュ"a"キー、キーが前処理され、ディスパッチ、および<xref:System.Windows.Forms.Control.KeyDown>イベントが発生します。  
  
2.  ユーザーが"a"キーを保持して、キーが前処理され、ディスパッチ、および<xref:System.Windows.Forms.Control.KeyPress>イベントが発生します。  
  
     このイベントはユーザーがキーを押し続けているとき複数回発生します。  
  
3.  "A"キー、キーが前処理され、ユーザーのリリースのディスパッチと<xref:System.Windows.Forms.Control.KeyUp>イベントが発生します。  
  
## <a name="preprocessing-keys"></a>キーの前処理  
 他のメッセージのようなキーボード メッセージの処理、<xref:System.Windows.Forms.Control.WndProc%2A>フォームまたはコントロールのメソッド。 ただし、キーボードの前にメッセージが処理を<xref:System.Windows.Forms.Control.PreProcessMessage%2A>メソッドの特殊文字のキーと物理キーを処理するためにオーバーライド可能な 1 つまたは複数のメソッドを呼び出します。 これらのメソッドをオーバーライドすると、コントロールがメッセージを処理する前に、特定のキーを検出してフィルターできます。 次の表に、実行される処理と、そのとき呼び出されるメソッドを、メソッドが呼び出される順に示します。  
  
### <a name="preprocessing-for-a-keydown-event"></a>KeyDown イベントの前処理  
  
|アクション|関連メソッド|メモ|  
|------------|--------------------|-----------|  
|アクセラレータやメニュー ショートカットなどのコマンド キーの確認。|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|このメソッドはコマンド キーを処理します。コマンド キーは通常のキーよりも優先順位が上です。 このメソッドが `true` を返した場合、キー メッセージはディスパッチされず、キー イベントも発生しません。 返された場合`false`、<xref:System.Windows.Forms.Control.IsInputKey%2A>が呼び出されます`.`|  
|プリプロセスを必要とする特殊なキーまたは通常の文字のキーを発生させるかを確認してください、<xref:System.Windows.Forms.Control.KeyDown>イベントをコントロールにディスパッチします。|<xref:System.Windows.Forms.Control.IsInputKey%2A>|メソッドを返す場合`true`、コントロールが通常の文字を意味し、<xref:System.Windows.Forms.Control.KeyDown>イベントが発生します。 場合`false`、<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>が呼び出されます。 **注:** コントロールがキーまたはキーの組み合わせを取得するには、処理、<xref:System.Windows.Forms.Control.PreviewKeyDown>イベントとセット<xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A>の<xref:System.Windows.Forms.PreviewKeyDownEventArgs>に`true`キーまたはキーの <xref:system.windows.forms.previewkeydowneventargs> の。|  
|移動キー (Esc、Tab、Return、または方向キー) の確認。|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|このメソッドはコントロール内で特別な機能 (コントロールとその親コントロールの間のフォーカスの切り替えなど) を実行する物理キーを処理します。 このコントロールは、キーを処理しない場合、<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>が階層の最上位のコントロールに親コントロールで呼び出されます。 このメソッドが `true` を返した場合、前処理は完了し、キー イベントは生成されません。 返された場合`false`、<xref:System.Windows.Forms.Control.KeyDown>イベントが発生します。|  
  
### <a name="preprocessing-for-a-keypress-event"></a>KeyPress イベントの前処理  
  
|アクション|関連メソッド|メモ|  
|------------|--------------------|-----------|  
|キーがコントロールによって処理される通常の文字であるかどうかの確認|<xref:System.Windows.Forms.Control.IsInputChar%2A>|かどうか、文字は、通常の文字は、このメソッドが戻る`true`、<xref:System.Windows.Forms.Control.KeyPress>イベントが発生し、それ以上の前処理に発生します。 それ以外の場合<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>が呼び出されます。|  
|文字がニーモニック (ボタン上の &OK など) かどうかの確認|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|このメソッドは、のような<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>コントロールの階層構造が呼び出されます。 呼び出すことによってニーモニックの確認、コントロールがコンテナー コントロールの場合は、<xref:System.Windows.Forms.Control.ProcessMnemonic%2A>自体とその子コントロールにします。 場合<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>返します`true`、<xref:System.Windows.Forms.Control.KeyPress>イベントは発生しません。|  
  
## <a name="processing-keyboard-messages"></a>キーボード メッセージの処理  
 キーボード メッセージ数に到達した後、<xref:System.Windows.Forms.Control.WndProc%2A>メソッドをフォームまたはコントロールの一連のオーバーライド可能なメソッドで処理されます。 これらの各メソッドを返します、<xref:System.Boolean>キーボード メッセージが処理され、コントロールによって使用されるかどうかを指定する値。 いずれかのメソッドが `true` を返した場合は、メッセージが処理されたと判断されるため、ベース コントロールまたは親コントロールにメッセージが渡されることはありません。 そうでない場合は、メッセージがメッセージ キューに残り、場合によってはそのコントロールのベースまたは親に含まれる別のメソッドで処理されます。 次の表に、キーボード メッセージを処理するメソッドを示します。  
  
|メソッド|メモ|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|このメソッドによって受信されたすべてのキーボード メッセージを処理する、<xref:System.Windows.Forms.Control.WndProc%2A>コントロールのメソッド。|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|このメソッドは、キーボード メッセージを親コントロールに送信します。 場合<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>返します`true`、キー イベントは生成されず、それ以外の場合<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>が呼び出されます。|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|このメソッド、 <xref:System.Windows.Forms.Control.KeyDown>、 <xref:System.Windows.Forms.Control.KeyPress>、および<xref:System.Windows.Forms.Control.KeyUp>適切なイベント。|  
  
## <a name="overriding-keyboard-methods"></a>キーボード メソッドのオーバーライド  
 キーボード メッセージを処理するためにオーバーライドできるメソッドは多数ありますが、どのメソッドを選ぶかが非常に重要です。 次の表に、実行するタスクと、キーボード メソッドをオーバーライドする最善の方法を示します。 メソッドのオーバーライドの詳細については、次を参照してください。[のプロパティとメソッドをオーバーライドする派生クラス](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes)します。  
  
|タスク|メソッド|  
|----------|------------|  
|ナビゲーション キーをインターセプトし、発生させる、<xref:System.Windows.Forms.Control.KeyDown>イベント。 たとえば、テキスト ボックス内で Tab や Return を処理するなど。|<xref:System.Windows.Forms.Control.IsInputKey%2A> をオーバーライドします。 **注:** また、処理することができます、<xref:System.Windows.Forms.Control.PreviewKeyDown>イベントとセット<xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A>の<xref:System.Windows.Forms.PreviewKeyDownEventArgs>に`true`キーまたはキーの <xref:system.windows.forms.previewkeydowneventargs> の。|  
|コントロールで特別な入力処理や移動処理を実行する。 たとえば、リスト コントロールで方向キーを使用して選択項目を変更するなど。|オーバーライド <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|ナビゲーション キーをインターセプトし、発生させる、<xref:System.Windows.Forms.Control.KeyPress>イベント。 たとえば、スピン ボックス コントロールで方向キーを複数回押して、項目の移動を加速するなど。|<xref:System.Windows.Forms.Control.IsInputChar%2A> をオーバーライドします。|  
|実行中に入力またはナビゲーションの特別な処理を<xref:System.Windows.Forms.Control.KeyPress>イベント。 たとえば、リスト コントロール内で "r" キーを押し続けると、r の文字で始まる項目にスキップするなど。|オーバーライド <xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|カスタムなニーモニックの処理を実行する。たとえば、ツール バーに配置されたオーナー描画ボタンのニーモニックを処理するなど。|<xref:System.Windows.Forms.Control.ProcessMnemonic%2A> をオーバーライドします。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.WndProc%2A>
- <xref:System.Windows.Forms.Control.PreProcessMessage%2A>
- [My.Computer.Keyboard オブジェクト](~/docs/visual-basic/language-reference/objects/my-computer-keyboard-object.md)
- [キーボードへのアクセス](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)
- [キーボード イベントの使用](using-keyboard-events.md)
