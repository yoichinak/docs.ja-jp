---
title: '方法: Windows フォームの StatusBar コントロールでクリックされたパネルを確認する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- status bars [Windows Forms], determining panel clicked
- panels [Windows Forms], determining clicked
- StatusBar control [Windows Forms], coding panel click events
- StatusBar control [Windows Forms], determining panel clicked
- PanelClick event [Windows Forms], determining panel clicked
- Panel control [Windows Forms], determining click
ms.assetid: d14c6092-04b2-4a07-8ddf-0dd11277ff5f
ms.openlocfilehash: 6229d8965949641105cd0e9708474c3249d52d1d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965717"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>方法: Windows フォームの StatusBar コントロールでクリックされたパネルを確認する
> [!IMPORTANT]
> <xref:System.Windows.Forms.StatusBar> <xref:System.Windows.Forms.StatusBarPanel> <xref:System.Windows.Forms.StatusBar>コントロール<xref:System.Windows.Forms.StatusStrip>と<xref:System.Windows.Forms.ToolStripStatusLabel>コントロールは、および<xref:System.Windows.Forms.StatusBarPanel>コントロールに対して、機能の置き換えと追加を行います。ただし、コントロールとコントロールは、下位互換性と将来の使用の両方のために保持されます。し.  
  
 ユーザーのクリックに応答するように[StatusBar コントロール](statusbar-control-windows-forms.md)コントロールをプログラミングするには、 <xref:System.Windows.Forms.StatusBar.PanelClick>イベント内で case ステートメントを使用します。 イベントには、クリック<xref:System.Windows.Forms.StatusBarPanel>されたへの参照を含む引数 (パネル引数) が含まれています。 この参照を使用して、クリックされたパネルのインデックスを特定し、それに応じてプログラムを作成できます。  
  
> [!NOTE]
> <xref:System.Windows.Forms.StatusBar>コントロール`true`の<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>プロパティがに設定されていることを確認します。  
  
### <a name="to-determine-which-panel-was-clicked"></a>クリックされたパネルを確認するには  
  
1. `switch case` `Select Case` C# C++イベントハンドラーでは、(Visual Basic) または (visual または visual) ステートメントを使用して、クリックされたパネルを判別します。これを行うには、イベント引数でクリックしたパネルのインデックスを調べます。 <xref:System.Windows.Forms.StatusBar.PanelClick>  
  
     次のコード例では<xref:System.Windows.Forms.StatusBar> 、コントロール、 `StatusBarPanel1` `StatusBar1`、 `StatusBarPanel2`およびという2つ<xref:System.Windows.Forms.StatusBarPanel>のオブジェクトのプレゼンスをフォームに指定する必要があります。  
  
    ```vb  
    Private Sub StatusBar1_PanelClick(ByVal sender As System.Object, ByVal e As System.Windows.Forms.StatusBarPanelClickEventArgs) Handles StatusBar1.PanelClick  
       Select Case StatusBar1.Panels.IndexOf(e.StatusBarPanel)  
         Case 0  
           MessageBox.Show("You have clicked Panel One.")  
         Case 1  
           MessageBox.Show("You have clicked Panel Two.")  
       End Select  
    End Sub  
    ```  
  
    ```csharp  
    private void statusBar1_PanelClick(object sender,   
    System.Windows.Forms.StatusBarPanelClickEventArgs e)  
    {  
       switch (statusBar1.Panels.IndexOf(e.StatusBarPanel))  
       {  
          case 0 :  
             MessageBox.Show("You have clicked Panel One.");  
             break;  
          case 1 :  
             MessageBox.Show("You have clicked Panel Two.");  
             break;  
       }  
    }  
    ```  
  
    ```cpp  
    private:  
       void statusBar1_PanelClick(System::Object ^  sender,  
          System::Windows::Forms::StatusBarPanelClickEventArgs ^  e)  
       {  
          switch (statusBar1->Panels->IndexOf(e->StatusBarPanel))  
          {  
             case 0 :  
                MessageBox::Show("You have clicked Panel One.");  
                break;  
             case 1 :  
                MessageBox::Show("You have clicked Panel Two.");  
                break;  
          }  
       }  
    ```  
  
     (ビジュアルC#、ビジュアルC++)フォームのコンストラクターに次のコードを配置して、イベントハンドラーを登録します。  
  
    ```csharp  
    this.statusBar1.PanelClick += new   
       System.Windows.Forms.StatusBarPanelClickEventHandler   
       (this.statusBar1_PanelClick);  
    ```  
  
    ```cpp  
    this->statusBar1->PanelClick += gcnew  
       System::Windows::Forms::StatusBarPanelClickEventHandler  
       (this, &Form1::statusBar1_PanelClick);  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.StatusBar>
- <xref:System.Windows.Forms.ToolStripStatusLabel>
- [方法: ステータスバーパネルのサイズを設定する](how-to-set-the-size-of-status-bar-panels.md)
- [チュートリアル: 実行時のステータスバー情報の更新](walkthrough-updating-status-bar-information-at-run-time.md)
- [StatusBar コントロールの概要](statusbar-control-overview-windows-forms.md)
