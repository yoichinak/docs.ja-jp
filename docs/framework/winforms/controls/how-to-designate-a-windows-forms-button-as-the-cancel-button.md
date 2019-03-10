---
title: '方法: Windows フォームの Button をキャンセル ボタンとして指定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- buttons [Windows Forms], cancel buttons
- Button control [Windows Forms], designating as cancel button
ms.assetid: 252f0834-e54b-44d9-96f7-ee5f50e94f2c
ms.openlocfilehash: f8eacea0d21159d30d48e48be3093ddf8ca3d7d7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722384"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-cancel-button"></a>方法: Windows フォームの Button をキャンセル ボタンとして指定します。
任意の Windows フォームで指定することができます、<xref:System.Windows.Forms.Button>コントロールをキャンセル ボタン。 ユーザーがフォーム上の他のコントロールにフォーカスがあるか、ESC キーを押すと [キャンセル] ボタンをクリックします。 このようなボタンは通常、ユーザーは、すばやく操作をコミットせずに操作を終了できるようにする設定します。  
  
### <a name="to-designate-the-cancel-button"></a>[キャンセル] ボタンを指定するには  
  
1.  フォームの設定<xref:System.Windows.Forms.Form.CancelButton%2A>プロパティを適切な<xref:System.Windows.Forms.Button>コントロール。  
  
    ```vb  
    Private Sub SetCancelButton(ByVal myCancelBtn As Button)  
       Me.CancelButton = myCancelBtn  
    End Sub  
    ```  
  
    ```csharp  
    private void SetCancelButton(Button myCancelBtn)  
    {  
       this.CancelButton = myCancelBtn;  
    }  
    ```  
  
    ```cpp  
    private:  
       void SetCancelButton(Button ^ myCancelBtn)  
       {  
          this->CancelButton = myCancelBtn;  
       }  
    ```  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.Form.CancelButton%2A>
- [Button コントロールの概要](button-control-overview-windows-forms.md)
- [Windows フォームの Button コントロールを選択する方法](ways-to-select-a-windows-forms-button-control.md)
- [方法: Windows フォームのボタン クリックに応答するには](how-to-respond-to-windows-forms-button-clicks.md)
- [方法: Windows フォームの Button を承認ボタンとして指定します。](how-to-designate-a-windows-forms-button-as-the-accept-button.md)
- [Button コントロール](button-control-windows-forms.md)
