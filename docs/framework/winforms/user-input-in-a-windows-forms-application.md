---
title: Windows フォーム アプリケーションにおけるユーザー入力
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, user input
ms.assetid: 9d61fa96-70f7-4754-885a-49a4a6316bdb
ms.openlocfilehash: 351c1e42bb775331cbe0e2005b6bea284716de75
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711929"
---
# <a name="user-input-in-a-windows-forms-application"></a>Windows フォーム アプリケーションにおけるユーザー入力
Windows フォームでは、ユーザー入力が Windows メッセージの形式でアプリケーションに送信されます。 一連のオーバーライド可能なメソッドは、フォーム、アプリケーションでこれらのメッセージを処理し、レベルを制御します。 これらのメソッドは、マウスとキーボード メッセージを受信するときに取得については、マウスやキーボード入力を処理できるイベントが発生します。 多くの場合、Windows フォーム アプリケーションはこれらのイベントを処理するだけですべてのユーザー入力を処理することになります。 それ以外の場合は、アプリケーションは、アプリケーション、フォーム、またはコントロールによって受信される前に、特定のメッセージをインターセプトするにはメッセージを処理する方法の 1 つをオーバーライドする必要があります。  
  
## <a name="mouse-and-keyboard-events"></a>マウスとキーボード イベント  
 すべての Windows フォーム コントロールは、マウスおよびキーボード入力に関連するイベントのセットを継承します。 など、コントロールで処理できる、<xref:System.Windows.Forms.Control.KeyPress>押されたキーの文字コードを確認するイベントまたはコントロールを処理できますが、<xref:System.Windows.Forms.Control.MouseClick>にマウスの位置をクリックします。 マウスとキーボード イベントの詳細については、次を参照してください。[キーボード イベントを使用した](using-keyboard-events.md)と[Windows フォームにおけるマウス イベント](mouse-events-in-windows-forms.md)します。  
  
## <a name="methods-that-process-user-input-messages"></a>ユーザーの入力メッセージを処理するメソッド  
 フォームとコントロールへのアクセスがある、<xref:System.Windows.Forms.IMessageFilter>インターフェイスと一連のメッセージ キュー内のさまざまな時点での Windows メッセージを処理するメソッドをオーバーライドします。 これらのメソッドがすべて、<xref:System.Windows.Forms.Message>パラメーターで、Windows メッセージの低レベルの詳細をカプセル化します。 実装したり、メッセージを確認しメッセージを使用するか、メッセージ キュー内の次のコンシューマーに渡し、これらのメソッドをオーバーライドできます。 次の表は、Windows フォーム内のすべての Windows メッセージを処理するメソッドを表示します。  
  
|メソッド|メモ|  
|------------|-----------|  
|<xref:System.Windows.Forms.IMessageFilter.PreFilterMessage%2A>|このメソッドは、アプリケーション レベルで (ポストされたとも呼ばれます) の Windows メッセージをキューに置かれたを受け取ります。|  
|<xref:System.Windows.Forms.Control.PreProcessMessage%2A>|このメソッドが処理される前に、フォームとコントロールのレベルでの Windows メッセージを受け取ります。|  
|<xref:System.Windows.Forms.Control.WndProc%2A>|このメソッドは、フォームとコントロールのレベルでの Windows メッセージを処理します。|  
|<xref:System.Windows.Forms.Control.DefWndProc%2A>|このメソッドは、フォームとコントロールのレベルでの Windows メッセージの既定の処理を実行します。 これは、ウィンドウの最小限の機能を提供します。|  
|<xref:System.Windows.Forms.Control.OnNotifyMessage%2A>|このメソッドは、処理された後に、フォームとコントロールのレベルでメッセージを受け取ります。 <xref:System.Windows.Forms.ControlStyles.EnableNotifyMessage>このメソッドが呼び出されるのスタイル ビットを設定する必要があります。|  
  
 キーボードとマウスのメッセージは、追加のメッセージの種類に固有のオーバーライド可能なメソッドのセットでも処理されます。 詳細については、次を参照してください。[キーボード入力のしくみ](how-keyboard-input-works.md)と[Windows フォームにおけるマウス入力動作方法](how-mouse-input-works-in-windows-forms.md)します。  
  
## <a name="see-also"></a>関連項目
- [Windows フォームでのユーザー入力](user-input-in-windows-forms.md)
- [Windows フォーム アプリケーションにおけるキーボード入力](keyboard-input-in-a-windows-forms-application.md)
- [Windows フォーム アプリケーションにおけるマウス入力](mouse-input-in-a-windows-forms-application.md)
