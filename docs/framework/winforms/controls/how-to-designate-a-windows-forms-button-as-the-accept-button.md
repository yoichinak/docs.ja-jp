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
ms.openlocfilehash: 8e608bb2cb4635ef1d29fd7a0aff3ac95fcd9af5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61943911"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button"></a>方法: Windows フォームの Button コントロールを承認ボタンとして指定する
任意の Windows フォームで指定することができます、<xref:System.Windows.Forms.Button>コントロールを承認ボタン、既定のボタンとも呼ばれます。 ユーザーが ENTER キーを押すと、フォームの他のコントロールにフォーカスがあるの既定のボタンがクリックされました。  
  
> [!NOTE]
>  フォーカスを持つコントロールが別のボタン例外:、フォーカスのあるボタンをクリックする場合、-複数行テキスト ボックス、または ENTER キーをトラップするカスタム コントロール。  
  
### <a name="to-designate-the-accept-button"></a>同意する ボタンを指定するには  
  
1. フォームの設定<xref:System.Windows.Forms.Form.AcceptButton%2A>プロパティを適切な<xref:System.Windows.Forms.Button>コントロール。  
  
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
- [方法: Windows フォームのボタン クリックに応答するには](how-to-respond-to-windows-forms-button-clicks.md)
- [方法: Windows フォームの Button をキャンセル ボタンとして指定します。](how-to-designate-a-windows-forms-button-as-the-cancel-button.md)
- [Button コントロール](button-control-windows-forms.md)
