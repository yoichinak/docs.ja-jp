---
title: ユーザーの入力の処理
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: f92b742c3f6feec72e5b3150204d7d984636281d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934090"
---
# <a name="handling-user-input"></a>ユーザーの入力の処理
このトピックでは、によっ<xref:System.Windows.Forms.Control?displayProperty=nameWithType>て提供される主なキーボードイベントとマウスイベントについて説明します。 イベントを処理するときに、コントロール作成者はイベントにデリゲートを結び付けるのではなく、保護された `On`*EventName* メソッドをオーバーライドする必要があります。 イベントのレビューについては、「[コンポーネントからのイベントの生成](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120))」を参照してください。  
  
> [!NOTE]
> イベントに関連付けられているデータがない場合は、基底クラス<xref:System.EventArgs>のインスタンスが引数として`On` *EventName*メソッドに渡されます。  
  
## <a name="keyboard-events"></a>キーボード イベント  
 コントロールで処理できる一般的なキーボードイベントは<xref:System.Windows.Forms.Control.KeyDown>、、 <xref:System.Windows.Forms.Control.KeyPress>、および<xref:System.Windows.Forms.Control.KeyUp>です。  
  
|イベント名|オーバーライドするメソッド|イベントの説明|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|キーが最初に押されたときにのみ発生します。|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|キーが押されるたびに発生します。 キーが保持されている場合<xref:System.Windows.Forms.Control.KeyPress>は、オペレーティングシステムで定義されている繰り返し速度でイベントが発生します。|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|キーが離されたときに発生します。|  
  
> [!NOTE]
> キーボード入力の処理は、前の表のイベントをオーバーライドするよりもかなり複雑であり、このトピックでは触れていません。 詳細については、「 [Windows フォームでのユーザー入力](../user-input-in-windows-forms.md)」を参照してください。  
  
## <a name="mouse-events"></a>マウス イベント  
 コントロールが処理できるマウスイベントは<xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseHover>、 <xref:System.Windows.Forms.Control.MouseEnter> <xref:System.Windows.Forms.Control.MouseLeave> <xref:System.Windows.Forms.Control.MouseMove>、、、、、および<xref:System.Windows.Forms.Control.MouseUp>です。  
  
|イベント名|オーバーライドするメソッド|イベントの説明|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|ポインターがコントロール上にある状態でマウス ボタンが押されると発生します。|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|ポインターがコントロールの領域に初めて入ったときに発生します。|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|ポインターがコントロールの上に置かれたときに発生します。|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|ポインターがコントロールの領域から離れると発生します。|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|ポインターがコントロールの領域内で移動すると発生します。|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|ポインターがコントロールの上にある状態でマウス ボタンが離されるか、ポインターがコントロールの領域から離れると発生します。|  
  
 次のコードフラグメントは、イベントを<xref:System.Windows.Forms.Control.MouseDown>オーバーライドする例を示しています。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 次のコードフラグメントは、イベントを<xref:System.Windows.Forms.Control.MouseMove>オーバーライドする例を示しています。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 次のコードフラグメントは、イベントを<xref:System.Windows.Forms.Control.MouseUp>オーバーライドする例を示しています。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 `FlashTrackBar`サンプルの完全なソースコードについては[、「方法:進行状況](how-to-create-a-windows-forms-control-that-shows-progress.md)を表示する Windows フォームコントロールを作成します。  
  
## <a name="see-also"></a>関連項目

- [Windows フォーム コントロールのイベント](events-in-windows-forms-controls.md)
- [イベントの定義](defining-an-event-in-windows-forms-controls.md)
- [イベント](../../../standard/events/index.md)
- [Windows フォームでのユーザー入力](../user-input-in-windows-forms.md)
