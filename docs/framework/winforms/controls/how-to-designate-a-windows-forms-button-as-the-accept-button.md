---
title: '方法: Windows フォームの Button コントロールを承認ボタンとして指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: 22cc9da6-b913-4e04-9554-dee443ac5c3a
ms.openlocfilehash: 5b21ee7da7a666a391be3bc5be57855eaa7ec8b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967369"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>方法: Windows フォームの Button コントロールを承認ボタンとして指定する
任意の Windows フォームで、[accept] <xref:System.Windows.Forms.Button>ボタンとしてコントロールを指定できます (既定のボタンとも呼ばれます)。 ユーザーが ENTER キーを押すたびに、フォーム上の他のコントロールにフォーカスがあるかどうかに関係なく、既定のボタンがクリックされます。  
  
> [!NOTE]
> この例外は、フォーカスのあるコントロールが別のボタンである場合です。この場合、フォーカスがあるボタン (複数行のテキストボックス)、または ENTER キーをトラップするカスタムコントロールがクリックされます。  
  
### <a name="to-designate-the-accept-button"></a>Accept ボタンを指定するには  
  
1. フォームの<xref:System.Windows.Forms.Form.AcceptButton%2A>プロパティを適切な<xref:System.Windows.Forms.Button>コントロールに設定します。  
  
    ```vb  
    Private Sub SetDefault(ByVal myDefaultBtn As Button)  
      Me.AcceptButton = myDefaultBtn   
    End Sub  
    ```  
  
    ```csharp  
    private void SetDefault(Button myDefaultBtn)  
    {  
       this.AcceptButton = myDefaultBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetDefault(Button ^ myDefaultBtn)  
       {  
          this->AcceptButton = myDefaultBtn;  
       }  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Button コントロールの概要](button-control-overview-windows-forms.md)
- [Windows フォームの Button コントロールを選択する方法](ways-to-select-a-windows-forms-button-control.md)
- [方法: Windows フォームボタンのクリックに応答する](how-to-respond-to-windows-forms-button-clicks.md)
- [方法: [キャンセル] ボタンとして Windows フォームボタンを指定する](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Button コントロール](button-control-windows-forms.md)
