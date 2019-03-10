---
title: '方法: どの修飾子キーが押されたかを決定します。'
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
ms.openlocfilehash: de8af53bbf065047541e030de7a174987e5785df
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715985"
---
# <a name="how-to-determine-which-modifier-key-was-pressed"></a>方法: どの修飾子キーが押されたかを決定します。
ユーザーのキーボード操作を許可しているアプリケーションを作成するときの SHIFT、ALT、CTRL キーなどの修飾子キーを監視することもできます。 他のキーまたはマウス クリックで、組み合わせて修飾子キーが押された、ときに、アプリケーションが適切に応答できます。 たとえば、s が押された場合、画面に表示する"s"が生じるだけですが、ctrl キーを押しながら S キーを押すと、現在のドキュメントが保存されます。 処理する場合、<xref:System.Windows.Forms.Control.KeyDown>イベント、<xref:System.Windows.Forms.KeyEventArgs.Modifiers%2A>のプロパティ、<xref:System.Windows.Forms.KeyEventArgs>受信したイベント ハンドラーを指定しますどの修飾子キーが押されました。 または、<xref:System.Windows.Forms.KeyEventArgs.KeyData%2A>プロパティの<xref:System.Windows.Forms.KeyEventArgs>もビットごとの OR と組み合わせると修飾子キーが押された文字を指定します。 ただし、処理する場合、<xref:System.Windows.Forms.Control.KeyPress>イベントまたはマウス イベント、イベント ハンドラーは、この情報を受信しません。 この場合、使用する必要があります、<xref:System.Windows.Forms.Control.ModifierKeys%2A>のプロパティ、<xref:System.Windows.Forms.Control>クラス。 どちらの場合、適切なビットごとの AND を実行する必要があります<xref:System.Windows.Forms.Keys>値およびテストする値。 <xref:System.Windows.Forms.Keys>列挙には、バリエーションの各修飾子キーは、ため、ビット演算を実行することが重要と適切な値が提供しています。 たとえば、SHIFT キーがによって表される<xref:System.Windows.Forms.Keys.Shift>、 <xref:System.Windows.Forms.Keys.ShiftKey>、<xref:System.Windows.Forms.Keys.RShiftKey>と<xref:System.Windows.Forms.Keys.LShiftKey>修飾子キーと shift キーをテストする適切な値<xref:System.Windows.Forms.Keys.Shift>します。 同様に、修飾子として ctrl キーと alt キーをテストする必要がありますを使用して、<xref:System.Windows.Forms.Keys.Control>と<xref:System.Windows.Forms.Keys.Alt>それぞれ値します。  
  
> [!NOTE]
>  Visual Basic プログラマにとっては、を通じてキーの情報にもアクセスできます、<xref:Microsoft.VisualBasic.Devices.Computer.Keyboard%2A>プロパティ  
  
### <a name="to-determine-which-modifier-key-was-pressed"></a>どの修飾子キーが押されたかを判断するには  
  
-   ビットごとの使用`AND`演算子と共に、<xref:System.Windows.Forms.Control.ModifierKeys%2A>プロパティと値の<xref:System.Windows.Forms.Keys>特定の修飾子キーが押されたかどうかを決定する列挙体。 次のコード例で、SHIFT キーが押されたかどうかを確認する方法を示しています、<xref:System.Windows.Forms.Control.KeyPress>イベント ハンドラー。  
  
     [!code-cpp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/cpp/form1.cpp#5)]
     [!code-csharp[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/CS/form1.cs#5)]
     [!code-vb[System.Windows.Forms.DetermineModifierKey#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DetermineModifierKey/VB/form1.vb#5)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.ModifierKeys%2A>
- [Windows フォーム アプリケーションにおけるキーボード入力](keyboard-input-in-a-windows-forms-application.md)
- [方法: 場合の CapsLock がオンに Visual Basic で確認します。](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9c9d1fz9(v=vs.100))
