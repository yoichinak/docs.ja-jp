---
title: '方法: どの修飾子キーが押されたかを判断する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- keyboard input
- shift keys
- events [Windows Forms], mouse
- Keys.ControlKey enumeration member
- keys [Windows Forms], control keys
- user input [Windows Forms], checking for keyboard
- keys [Windows Forms], determining last pressed
- keys [Windows Forms], shift keys
- keys [Windows Forms], modifier keys
- control keys
- keys [Windows Forms], alt keys
- alt keys
- Keys.Shift enumeration member
- events [Windows Forms], keyboard
- keyboards [Windows Forms], keyboard input
- Keys.Alt enumeration member
- modifier keys
ms.assetid: 1e184048-0ae3-4067-a200-d4ba31dbc2cb
ms.openlocfilehash: 37fa897f5a2e1c65cbd5db9189f1500e3427c920
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964315"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>方法: どの修飾子キーが押されたかを判断する
ユーザーのキーストロークを受け入れるアプリケーションを作成する場合、SHIFT キー、ALT キー、CTRL キーなどの修飾子キーを監視することもできます。 修飾子キーを他のキーと組み合わせて押すか、マウスをクリックすると、アプリケーションが適切に応答できるようになります。 たとえば、文字 S が押されている場合、画面に "s" が表示されることがありますが、CTRL + S キーを押すと、現在のドキュメントが保存されている可能性があります。 <xref:System.Windows.Forms.Control.KeyDown>イベントを処理する場合は、 <xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A>イベントハンドラーに<xref:System.Windows.Forms.KeyEventArgs>よって受信されるのプロパティによって、どの修飾子キーが押されたかが指定されます。 または、 <xref:System.Windows.Forms.KeyEventArgs.KeyData%2A>の<xref:System.Windows.Forms.KeyEventArgs>プロパティは、押された文字と、ビットごとの or を組み合わせた修飾子キーを指定します。 ただし、 <xref:System.Windows.Forms.Control.KeyPress>イベントまたはマウスイベントを処理している場合、イベントハンドラーはこの情報を受け取りません。 この場合は、 <xref:System.Windows.Forms.Control.ModifierKeys%2A> <xref:System.Windows.Forms.Control>クラスのプロパティを使用する必要があります。 どちらの場合も、適切<xref:System.Windows.Forms.Keys>な値とテストする値のビットごとの and を実行する必要があります。 列挙<xref:System.Windows.Forms.Keys>体は各修飾子キーのバリエーションを提供するので、ビットごとの and を正しい値で実行することが重要です。 たとえば、shift キーは<xref:System.Windows.Forms.Keys.Shift> <xref:System.Windows.Forms.Keys.RShiftKey> 、 <xref:System.Windows.Forms.Keys.ShiftKey>、およびによって表さ<xref:System.Windows.Forms.Keys.LShiftKey>れます。また、シフトを修飾子キーとし<xref:System.Windows.Forms.Keys.Shift>てテストするための正しい値はです。 同様に、CTRL と ALT を修飾子としてテストするに<xref:System.Windows.Forms.Keys.Control>は<xref:System.Windows.Forms.Keys.Alt> 、それぞれとの値をそれぞれ使用する必要があります。  
  
> [!NOTE]
> Visual Basic プログラマは、プロパティを使用し<xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A>てキー情報にアクセスすることもできます。  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>どの修飾子キーが押されたかを調べるには  
  
- ビットごと`AND`の演算子<xref:System.Windows.Forms.Control.ModifierKeys%2A>とプロパティを使用し、列挙体の値を使用して、特定の修飾子キーが押されているかどうかを判断します。<xref:System.Windows.Forms.Keys> 次のコード例は、 <xref:System.Windows.Forms.Control.KeyPress>イベントハンドラー内で SHIFT キーが押されているかどうかを確認する方法を示しています。  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [Windows フォーム アプリケーションにおけるキーボード入力](keyboard-input-in-a-windows-forms-application.md)
- [方法: Visual Basic で CapsLock がオンになっているかどうかを確認する](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))
