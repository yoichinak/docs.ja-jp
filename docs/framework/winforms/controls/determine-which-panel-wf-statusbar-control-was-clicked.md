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
ms.openlocfilehash: 1c28f8eaba5c35f762d6fc57ebbddbbb71769c81
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304286"
---
# <a name="how-to-determine-which-panel-in-the-windows-forms-statusbar-control-was-clicked"></a>方法: Windows フォームの StatusBar コントロールでクリックされたパネルを確認する
> [!IMPORTANT]
>  <xref:System.Windows.Forms.StatusStrip>と<xref:System.Windows.Forms.ToolStripStatusLabel>コントロールの置換し、する機能を追加、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>を制御しますただし、、<xref:System.Windows.Forms.StatusBar>と<xref:System.Windows.Forms.StatusBarPanel>場合、下位互換性と将来の使用の両方のコントロールが保持されますします。選択します。  
  
 プログラムを[StatusBar コントロール](statusbar-control-windows-forms.md)コントロールをユーザーのクリックに応答する、内の case ステートメントを使用して、<xref:System.Windows.Forms.StatusBar.PanelClick>イベント。 イベント、クリックされたへの参照を含む引数 (パネル引数) に含まれる<xref:System.Windows.Forms.StatusBarPanel>します。 この参照を使用して、クリックされたパネルのインデックスを確認し、それに応じたプログラミングできます。  
  
> [!NOTE]
>  いることを確認、<xref:System.Windows.Forms.StatusBar>コントロールの<xref:System.Windows.Forms.StatusBar.ShowPanels%2A>プロパティに設定されて`true`します。  
  
### <a name="to-determine-which-panel-was-clicked"></a>クリックしてされたパネルを確認するには  
  
1. <xref:System.Windows.Forms.StatusBar.PanelClick>イベント ハンドラーを使用して、 `Select Case` (Visual Basic) でまたは`switch case`(VisualC#または[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]) イベントの引数でクリックされたパネルのインデックスを調べることでクリックしてされたパネルを判断するステートメント。  
  
     次のコード例のフォームで、存在が必要です、<xref:System.Windows.Forms.StatusBar>コントロール、 `StatusBar1`、2 つと<xref:System.Windows.Forms.StatusBarPanel>オブジェクト、`StatusBarPanel1`と`StatusBarPanel2`します。  
  
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
  
     (Visual c#、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターで、次のコードを配置します。  
  
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
- [方法: ステータス バー パネルのサイズを設定する](how-to-set-the-size-of-status-bar-panels.md)
- [チュートリアル: ステータス バー情報の実行時更新](walkthrough-updating-status-bar-information-at-run-time.md)
- [StatusBar コントロールの概要](statusbar-control-overview-windows-forms.md)
