---
title: '方法: ステータス バー パネルのサイズを設定する'
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
ms.openlocfilehash: 4ba0f7f02b548a5d9ea1a99605a668f449b3e4a9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923622"
---
# <a name="how-to-set-the-size-of-status-bar-panels"></a>方法: ステータス バー パネルのサイズを設定する
> [!NOTE]
> <xref:System.Windows.Forms.ToolStripStatusLabel> コントロールは、<xref:System.Windows.Forms.StatusBar> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.StatusBar> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。  
  
 [StatusBar コントロール](statusbar-control-windows-forms.md)コントロール内<xref:System.Windows.Forms.StatusBarPanel>のクラスの各インスタンスには、実行時の幅とサイズ変更動作を決定する動的プロパティが多数あります。  
  
### <a name="to-set-the-size-of-a-panel"></a>パネルのサイズを設定するには  
  
1. プロシージャでは、 <xref:System.Windows.Forms.StatusBarPanel.AutoSize%2A> <xref:System.Windows.Forms.StatusBarPanel.Width%2A> <xref:System.Windows.Forms.StatusBar.Panels%2A> <xref:System.Windows.Forms.StatusBarPanel.MinWidth%2A>コレクション<xref:System.Windows.Forms.StatusBarPanel>のプロパティを通じて渡されたインデックスを使用して、ステータスバーパネルの、、およびの各プロパティ (またはすべてのサブセット) を設定します。  
  
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
- [チュートリアル: 実行時のステータスバー情報の更新](walkthrough-updating-status-bar-information-at-run-time.md)
- [方法: Windows フォーム StatusBar コントロールでクリックされたパネルを確認する](determine-which-panel-wf-statusbar-control-was-clicked.md)
- [StatusBar コントロールの概要](statusbar-control-overview-windows-forms.md)
