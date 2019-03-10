---
title: '方法: ステータス バー パネルのサイズを設定します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- StatusBar control [Windows Forms], panel size
- status bars [Windows Forms], setting panel size
- panels [Windows Forms], setting size in status bars
ms.assetid: a01bee43-d9eb-4954-84e6-45a93532d08d
ms.openlocfilehash: 5b78463ca273f089f036166f5339977be435ccc9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711942"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a>方法: ステータス バー パネルのサイズを設定します。
> [!NOTE]
>  
  <xref:System.Windows.Forms.ToolStripStatusLabel> コントロールは、<xref:System.Windows.Forms.StatusBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.StatusBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 各インスタンス、<xref:System.Windows.Forms.StatusBarPanel>クラス内で、 [StatusBar コントロール](statusbar-control-windows-forms.md)コントロールにさまざまな動的プロパティは、幅を特定し、実行時の動作のサイズを変更します。  
  
### <a name="to-set-the-size-of-a-panel"></a>パネルのサイズを設定するには  
  
1.  プロシージャでは、次のように設定します。、 <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A>、 <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>、と<xref:System.Windows.Forms.StatusBarPanel.Width%2A>プロパティ (または任意のサブセット内) のインデックスを使用するパネルが通過ステータス バーの、<xref:System.Windows.Forms.StatusBar.Panels%2A>のプロパティ、<xref:System.Windows.Forms.StatusBarPanel>コレクション。  
  
    ```vb  
    Public Sub SetStatusBarPanelSize()  
    ' Create panel and set text property.  
       StatusBar1.Panels.Add("One")  
    ' Set properties of panels.  
       StatusBar1.Panels(0).AutoSize = StatusBarPanelAutoSize.Spring  
       StatusBar1.Panels(0).Width = 200  
    ' Enable the StatusBar control to display panels.  
       StatusBar1.ShowPanels = True  
        End Sub  
    ```  
  
    ```csharp  
    public void SetStatusBarPanelSize()  
    {  
       // Create panel and set text property.  
       statusBar1.Panels.Add("One");  
       // Set properties of panels.  
       statusBar1.Panels[0].AutoSize = StatusBarPanelAutoSize.Spring;  
       statusBar1.Panels[0].Width = 200;  
       statusBar1.ShowPanels = true;  
    }  
    ```  
  
    ```cpp  
    public:  
       void SetStatusBarPanelSize()  
       {  
          // Create panel and set text property.  
          statusBar1->Panels->Add("One");  
          // Set properties of panels.  
          statusBar1->Panels[0]->AutoSize =  
             StatusBarPanelAutoSize::Spring;  
          statusBar1->Panels[0]->Width = 200;  
          statusBar1->ShowPanels = true;  
       }  
    ```  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [チュートリアル: 実行時にステータス バー情報の更新](walkthrough-updating-status-bar-information-at-run-time.md)
- [方法: Windows フォームの StatusBar コントロール パネルのクリックを確認します。](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar コントロールの概要](statusbar-control-overview-windows-forms.md)
