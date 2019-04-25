---
title: '方法: Windows フォーム TabControl のタブを追加および削除する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tabs [Windows Forms], removing from pages
- TabPage control
- TabControl control [Windows Forms], adding and removing tabs
- tabs [Windows Forms], adding to pages
- tab pages
ms.assetid: 66d4dfca-41e8-44e3-9c80-fb7ac4cb1619
ms.openlocfilehash: 723e05803b1f7d2bc56476248987085dbe5e23f0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101602"
---
# <a name="how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol"></a>方法: Windows フォーム TabControl のタブを追加および削除する
既定で、<xref:System.Windows.Forms.TabControl>コントロールでは、2 つ含まれている<xref:System.Windows.Forms.TabPage>コントロール。 を通じてこれらのタブにアクセスすることができます、<xref:System.Windows.Forms.TabControl.TabPages%2A>プロパティ。  
  
### <a name="to-add-a-tab-programmatically"></a>プログラムでタブを追加するには  
  
-   使用して、<xref:System.Windows.Forms.TabControl.TabPageCollection.Add%2A>のメソッド、<xref:System.Windows.Forms.TabControl.TabPages%2A>プロパティ。  
  
    ```vb  
    Dim myTabPage As New TabPage()  
    myTabPage.Text = "TabPage" & (TabControl1.TabPages.Count + 1)  
    TabControl1.TabPages.Add(myTabPage)  
    ```  
  
    ```csharp  
    string title = "TabPage " + (tabControl1.TabCount + 1).ToString();  
    TabPage myTabPage = new TabPage(title);  
    tabControl1.TabPages.Add(myTabPage);  
    ```  
  
    ```cpp  
    String^ title = String::Concat("TabPage ",  
       (tabControl1->TabCount + 1).ToString());  
    TabPage^ myTabPage = gcnew TabPage(title);  
    tabControl1->TabPages->Add(myTabPage);  
    ```  
  
### <a name="to-remove-a-tab-programmatically"></a>プログラムにより、タブを削除するには  
  
-   選択したタブを削除するを使用して、<xref:System.Windows.Forms.TabControl.TabPageCollection.Remove%2A>のメソッド、<xref:System.Windows.Forms.TabControl.TabPages%2A>プロパティ。  
  
     - または -  
  
-   すべてのタブを削除するには、使用、<xref:System.Windows.Forms.TabControl.TabPageCollection.Clear%2A>のメソッド、<xref:System.Windows.Forms.TabControl.TabPages%2A>プロパティ。  
  
    ```vb  
    ' Removes the selected tab:  
    TabControl1.TabPages.Remove(TabControl1.SelectedTab)  
    ' Removes all the tabs:  
    TabControl1.TabPages.Clear()  
    ```  
  
    ```csharp  
    // Removes the selected tab:  
    tabControl1.TabPages.Remove(tabControl1.SelectedTab);  
    // Removes all the tabs:  
    tabControl1.TabPages.Clear();  
    ```  
  
    ```cpp  
    // Removes the selected tab:  
    tabControl1->TabPages->Remove(tabControl1->SelectedTab);  
    // Removes all the tabs:  
    tabControl1->TabPages->Clear();  
    ```  
  
## <a name="see-also"></a>関連項目

- [TabControl コントロールの概要](tabcontrol-control-overview-windows-forms.md)
- [方法: タブ ページにコントロールを追加します。](how-to-add-a-control-to-a-tab-page.md)
- [方法: タブ ページを無効にします。](how-to-disable-tab-pages.md)
- [方法: Windows フォーム TabControl の外観を変更します。](how-to-change-the-appearance-of-the-windows-forms-tabcontrol.md)
