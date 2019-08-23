---
title: キーボード入力のしくみ
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
ms.openlocfilehash: 369c434f5443334ccb8b136ce50ff2d5db8ece01
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963442"
---
# <a name="how-keyboard-input-works"></a>キーボード入力のしくみ
Windows フォームは、Windows メッセージに応答してキーボード イベントを発生させることにより、キーボード入力を処理します。 多くの Windows フォーム アプリケーションは、キーボード イベントを処理することによってキーボード入力を排他的に処理します。 しかし、高度なキーボード入力のシナリオ (キーがコントロールに到達する前にインターセプトするなど) を実装するためには、キーボード メッセージのしくみについて理解することが必要です。 このトピックでは、Windows フォームが認識するキー データの種類について説明し、キーボード メッセージをルーティングする方法について概要を説明します。 キーボード イベントの詳細については、「[キーボード イベントの使用](using-keyboard-events.md)」を参照してください。  
  
## <a name="types-of-keys"></a>キーの種類  
 Windows フォームは、ビットごと<xref:System.Windows.Forms.Keys>の列挙体によって表される仮想キーコードとして、キーボード入力を識別します。 <xref:System.Windows.Forms.Keys>列挙体を使用すると、一連の押されたキーを結合して1つの値にすることができます。 これらの値は、WM_KEYDOWN および WM_SYSKEYDOWN の Windows メッセージに付随する値になります。 イベントまたはイベントを処理することで、 <xref:System.Windows.Forms.Control.KeyDown>ほとんど<xref:System.Windows.Forms.Control.KeyUp>の物理キーの押下を検出できます。 文字キーは<xref:System.Windows.Forms.Keys>列挙体のサブセットであり、WM_CHAR および WM_SYSCHAR Windows メッセージに付随する値に対応します。 押されたキーの組み合わせによって文字が生成される場合は、 <xref:System.Windows.Forms.Control.KeyPress>イベントを処理することによって文字を検出できます。 または、Visual Basic プログラミング<xref:Microsoft.VisualBasic.Devices.Keyboard>インターフェイスによって公開されたを使用して、どのキーが押されたかを検出し、キーを送信することもできます。 詳細については、「[Accessing the Keyboard (キーボードへのアクセス)](../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)」を参照してください。  
  
## <a name="order-of-keyboard-events"></a>キーボード イベントの順序  
 先に説明したとおり、コントロール上では 3 つのキーボード関連のイベントが発生します。 イベントは一般に次の順序で発生します。  
  
1. ユーザーは "a" キーをプッシュし、キーは前処理され、ディスパッチ<xref:System.Windows.Forms.Control.KeyDown>されて、イベントが発生します。  
  
2. ユーザーは "a" キーを保持し、キーは前処理され、ディスパッチ<xref:System.Windows.Forms.Control.KeyPress>されて、イベントが発生します。  
  
     このイベントはユーザーがキーを押し続けているとき複数回発生します。  
  
3. ユーザーが "a" キーを解放すると、キーが前処理され<xref:System.Windows.Forms.Control.KeyUp> 、ディスパッチされて、イベントが発生します。  
  
## <a name="preprocessing-keys"></a>キーの前処理  
 他のメッセージと同様に、キーボードメッセージは<xref:System.Windows.Forms.Control.WndProc%2A>フォームまたはコントロールのメソッドで処理されます。 ただし、キーボードメッセージが処理される前<xref:System.Windows.Forms.Control.PreProcessMessage%2A>に、メソッドは、特殊文字キーと物理キーを処理するためにオーバーライドできる1つ以上のメソッドを呼び出します。 これらのメソッドをオーバーライドすると、コントロールがメッセージを処理する前に、特定のキーを検出してフィルターできます。 次の表に、実行される処理と、そのとき呼び出されるメソッドを、メソッドが呼び出される順に示します。  
  
### <a name="preprocessing-for-a-keydown-event"></a>KeyDown イベントの前処理  
  
|アクション|関連メソッド|メモ|  
|------------|--------------------|-----------|  
|アクセラレータやメニュー ショートカットなどのコマンド キーの確認。|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|このメソッドはコマンド キーを処理します。コマンド キーは通常のキーよりも優先順位が上です。 このメソッドが `true` を返した場合、キー メッセージはディスパッチされず、キー イベントも発生しません。 が返さ`false`れた<xref:System.Windows.Forms.Control.IsInputKey%2A>場合、が呼び出されます。`.`|  
|プリプロセスを必要とする特殊なキー、またはイベントを<xref:System.Windows.Forms.Control.KeyDown>発生させてコントロールにディスパッチする必要がある通常の文字キーを確認します。|<xref:System.Windows.Forms.Control.IsInputKey%2A>|メソッドがを返す`true`場合、コントロールが通常の文字であり、イベント<xref:System.Windows.Forms.Control.KeyDown>が発生することを意味します。 の`false`場合<xref:System.Windows.Forms.Control.ProcessDialogKey%2A> 、が呼び出されます。 **注:** コントロールがキーまたはキーの組み合わせを取得できるようにするには<xref:System.Windows.Forms.Control.PreviewKeyDown> 、必要なキーに<xref:System.Windows.Forms.PreviewKeyDownEventArgs>対し`true`てイベントを処理し、のをに設定<xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A>します。|  
|移動キー (Esc、Tab、Return、または方向キー) の確認。|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|このメソッドはコントロール内で特別な機能 (コントロールとその親コントロールの間のフォーカスの切り替えなど) を実行する物理キーを処理します。 イミディエイトコントロールがキーを処理しない場合、 <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>は親コントロールで呼び出され、階層内の最上位のコントロールに対して呼び出されます。 このメソッドが `true` を返した場合、前処理は完了し、キー イベントは生成されません。 が返さ`false`れた場合<xref:System.Windows.Forms.Control.KeyDown> 、イベントが発生します。|  
  
### <a name="preprocessing-for-a-keypress-event"></a>KeyPress イベントの前処理  
  
|アクション|関連メソッド|メモ|  
|------------|--------------------|-----------|  
|キーがコントロールによって処理される通常の文字であるかどうかの確認|<xref:System.Windows.Forms.Control.IsInputChar%2A>|文字が通常の文字の場合、このメソッドは`true`を返し<xref:System.Windows.Forms.Control.KeyPress> 、イベントが発生し、それ以降のプリプロセスは実行されません。 それ<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>以外の場合は、が呼び出されます。|  
|文字がニーモニック (ボタン上の &OK など) かどうかの確認|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|このメソッドは、に<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>似ていますが、コントロール階層の上位に呼び出されます。 コントロールがコンテナーコントロールである場合は、それ自体とその子<xref:System.Windows.Forms.Control.ProcessMnemonic%2A>コントロールでを呼び出すことによって、ニーモニックを確認します。 が<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>を`true`返した<xref:System.Windows.Forms.Control.KeyPress>場合、イベントは発生しません。|  
  
## <a name="processing-keyboard-messages"></a>キーボード メッセージの処理  
 キーボードメッセージは、フォーム<xref:System.Windows.Forms.Control.WndProc%2A>またはコントロールのメソッドに到着した後、オーバーライドできる一連のメソッドによって処理されます。 これらの各メソッドは、 <xref:System.Boolean>キーボードメッセージがコントロールによって処理および使用されたかどうかを示す値を返します。 いずれかのメソッドが `true` を返した場合は、メッセージが処理されたと判断されるため、ベース コントロールまたは親コントロールにメッセージが渡されることはありません。 そうでない場合は、メッセージがメッセージ キューに残り、場合によってはそのコントロールのベースまたは親に含まれる別のメソッドで処理されます。 次の表に、キーボード メッセージを処理するメソッドを示します。  
  
|メソッド|メモ|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|このメソッドは、コントロールの<xref:System.Windows.Forms.Control.WndProc%2A>メソッドによって受信されたすべてのキーボードメッセージを処理します。|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|このメソッドは、キーボード メッセージを親コントロールに送信します。 が<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>を`true`返す場合、キーイベントは生成さ<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>れません。それ以外の場合は、が呼び出されます。|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|このメソッドは<xref:System.Windows.Forms.Control.KeyDown>、 <xref:System.Windows.Forms.Control.KeyPress>必要に応じ<xref:System.Windows.Forms.Control.KeyUp>て、、、およびの各イベントを発生させます。|  
  
## <a name="overriding-keyboard-methods"></a>キーボード メソッドのオーバーライド  
 キーボード メッセージを処理するためにオーバーライドできるメソッドは多数ありますが、どのメソッドを選ぶかが非常に重要です。 次の表に、実行するタスクと、キーボード メソッドをオーバーライドする最善の方法を示します。 メソッドのオーバーライドの詳細については、「[派生クラスのプロパティとメソッドのオーバーライド](../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes)」を参照してください。  
  
|タスク|メソッド|  
|----------|------------|  
|ナビゲーションキーをインターセプトし、イベント<xref:System.Windows.Forms.Control.KeyDown>を発生させます。 たとえば、テキスト ボックス内で Tab や Return を処理するなど。|<xref:System.Windows.Forms.Control.IsInputKey%2A> をオーバーライドします。 **注:** <xref:System.Windows.Forms.Control.PreviewKeyDown>または、イベントを処理し、必要なキーに`true`対してのセット<xref:System.Windows.Forms.PreviewKeyDownEventArgs>をに設定<xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A>することもできます。|  
|コントロールで特別な入力処理や移動処理を実行する。 たとえば、リスト コントロールで方向キーを使用して選択項目を変更するなど。|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A> をオーバーライドします。|  
|ナビゲーションキーをインターセプトし、イベント<xref:System.Windows.Forms.Control.KeyPress>を発生させます。 たとえば、スピン ボックス コントロールで方向キーを複数回押して、項目の移動を加速するなど。|<xref:System.Windows.Forms.Control.IsInputChar%2A> をオーバーライドします。|  
|イベント中に特殊な入力または<xref:System.Windows.Forms.Control.KeyPress>ナビゲーション処理を実行します。 たとえば、リスト コントロール内で "r" キーを押し続けると、r の文字で始まる項目にスキップするなど。|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A> をオーバーライドします。|  
|カスタムなニーモニックの処理を実行する。たとえば、ツール バーに配置されたオーナー描画ボタンのニーモニックを処理するなど。|<xref:System.Windows.Forms.Control.ProcessMnemonic%2A> をオーバーライドします。|  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.WndProc%2A>
- <xref:System.Windows.Forms.Control.PreProcessMessage%2A>
- [My.Computer.Keyboard オブジェクト](../../visual-basic/language-reference/objects/my-computer-keyboard-object.md)
- [キーボードへのアクセス](../../visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)
- [キーボード イベントの使用](using-keyboard-events.md)
