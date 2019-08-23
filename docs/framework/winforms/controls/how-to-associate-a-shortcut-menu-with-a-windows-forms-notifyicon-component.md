---
title: '方法: ショートカット メニューを Windows フォーム NotifyIcon コンポーネントに関連付ける'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], for background processes
- NotifyIcon component [Windows Forms], associating shortcut menus
- shortcut menus [Windows Forms], for background processes
ms.assetid: d68f3926-08d3-4f7d-949f-1981b29cf188
ms.openlocfilehash: bf5602d0526fdd97f0cc14382339095a793f13c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922764"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>方法: ショートカット メニューを Windows フォーム NotifyIcon コンポーネントに関連付ける
> [!NOTE]
> <xref:System.Windows.Forms.MainMenu> とは、<xref:System.Windows.Forms.ContextMenu>以前のバージョン<xref:System.Windows.Forms.MainMenu>のとのコントロールに置き換えて機能を追加しますが、を選択した場合は、下位互換性と将来の使用の両方で保持されます。<xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.ContextMenuStrip> <xref:System.Windows.Forms.MenuStrip>  
  
 コンポーネント<xref:System.Windows.Forms.NotifyIcon>は、タスクバーの状態通知領域にアイコンを表示します。 一般的に、アプリケーションでは、このアイコンを右クリックして、表示されるアプリケーションにコマンドを送信することができます。 コンポーネントを<xref:System.Windows.Forms.NotifyIcon>コンポーネント<xref:System.Windows.Forms.ContextMenu>に関連付けることによって、この機能をアプリケーションに追加できます。  
  
> [!NOTE]
> タスクバーに<xref:System.Windows.Forms.NotifyIcon>コンポーネントのインスタンスを表示しているときに、起動時にアプリケーションを最小化する場合は、メインフォームの<xref:System.Windows.Forms.Form.WindowState%2A>プロパティ<xref:System.Windows.Forms.NotifyIcon>を<xref:System.Windows.Forms.FormWindowState.Minimized>に設定し、コンポーネントの<xref:System.Windows.Forms.NotifyIcon.Visible%2A>プロパティを確認します。がに`true`設定されています。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>デザイン時にショートカットメニューを NotifyIcon コンポーネントに関連付けるには  
  
1. コンポーネントを<xref:System.Windows.Forms.NotifyIcon>フォームに追加し、プロパティ<xref:System.Windows.Forms.NotifyIcon.Icon%2A>や<xref:System.Windows.Forms.NotifyIcon.Visible%2A>プロパティなどの重要なプロパティを設定します。  
  
     詳細については、「[方法 :Windows フォーム NotifyIcon コンポーネント](app-icons-to-the-taskbar-with-wf-notifyicon.md)を使用して、アプリケーションアイコンをタスクバーに追加します。  
  
2. コンポーネントを<xref:System.Windows.Forms.ContextMenu> Windows フォームに追加します。  
  
     実行時に使用できるようにするコマンドを表すメニュー項目をショートカットメニューに追加します。 これは、アクセスキーなどのメニュー項目にメニューの機能強化を追加する場合にも適しています。  
  
3. コンポーネントのプロパティを、追加したショートカットメニューに設定します。 <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> <xref:System.Windows.Forms.NotifyIcon>  
  
     このプロパティを設定すると、タスクバーのアイコンがクリックされたときにショートカットメニューが表示されます。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>プログラムによってショートカットメニューを NotifyIcon コンポーネントに関連付けるには  
  
1. <xref:System.Windows.Forms.NotifyIcon>クラスのインスタンス<xref:System.Windows.Forms.ContextMenu>とクラスを作成します。このとき、アプリケーションに必要なプロパティ設定<xref:System.Windows.Forms.NotifyIcon> (<xref:System.Windows.Forms.NotifyIcon.Icon%2A>および<xref:System.Windows.Forms.NotifyIcon.Visible%2A>コンポーネントのプロパティ、メニュー項目<xref:System.Windows.Forms.ContextMenu> 、コンポーネント)。  
  
2. コンポーネントのプロパティを、追加したショートカットメニューに設定します。 <xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A> <xref:System.Windows.Forms.NotifyIcon>  
  
     このプロパティを設定すると、タスクバーのアイコンがクリックされたときにショートカットメニューが表示されます。  
  
    > [!NOTE]
    > 次のコード例では、基本的なメニュー構造を作成します。 メニューの選択肢は、開発中のアプリケーションに適したものにカスタマイズする必要があります。 また、これらのメニュー項目の<xref:System.Windows.Forms.MenuItem.Click>イベントを処理するコードを記述することもできます。  
  
    ```vb  
    Public ContextMenu1 As New ContextMenu  
    Public NotifyIcon1 As New NotifyIcon  
  
    Public Sub CreateIconMenuStructure()  
       ' Add menu items to shortcut menu.  
       ContextMenu1.MenuItems.Add("&Open Application")  
       ContextMenu1.MenuItems.Add("S&uspend Application")  
       ContextMenu1.MenuItems.Add("E&xit")  
  
       ' Set properties of NotifyIcon component.  
       NotifyIcon1.Icon = New System.Drawing.Icon _   
          (System.Environment.GetFolderPath _   
          (System.Environment.SpecialFolder.Personal)  _   
          & "\Icon.ico")  
       NotifyIcon1.Text = "Right-click me!"  
       NotifyIcon1.Visible = True  
       NotifyIcon1.ContextMenu = ContextMenu1  
    End Sub  
    ```  
  
```csharp  
public NotifyIcon notifyIcon1 = new NotifyIcon();  
public ContextMenu contextMenu1 = new ContextMenu();  
  
public void createIconMenuStructure()  
{  
   // Add menu items to shortcut menu.  
   contextMenu1.MenuItems.Add("&Open Application");  
   contextMenu1.MenuItems.Add("S&uspend Application");  
   contextMenu1.MenuItems.Add("E&xit");  
  
   // Set properties of NotifyIcon component.  
   notifyIcon1.Icon = new System.Drawing.Icon  
      (System.Environment.GetFolderPath  
      (System.Environment.SpecialFolder.Personal)  
      + @"\Icon.ico");  
   notifyIcon1.Visible = true;  
   notifyIcon1.Text = "Right-click me!";  
   notifyIcon1.Visible = true;  
   notifyIcon1.ContextMenu = contextMenu1;  
}  
```  
  
```cpp  
public:  
   System::Windows::Forms::NotifyIcon ^ notifyIcon1;  
   System::Windows::Forms::ContextMenu ^ contextMenu1;  
  
   void createIconMenuStructure()  
   {  
      // Add menu items to shortcut menu.  
      contextMenu1->MenuItems->Add("&Open Application");  
      contextMenu1->MenuItems->Add("S&uspend Application");  
      contextMenu1->MenuItems->Add("E&xit");  
  
      // Set properties of NotifyIcon component.  
      notifyIcon1->Icon = gcnew System::Drawing::Icon  
          (String::Concat(System::Environment::GetFolderPath  
          (System::Environment::SpecialFolder::Personal),  
          "\\Icon.ico"));  
      notifyIcon1->Text = "Right-click me!";  
      notifyIcon1->Visible = true;  
      notifyIcon1->ContextMenu = contextMenu1;  
   }  
```  
  
> [!NOTE]
> を初期化`notifyIcon1` `contextMenu1,`する必要があります。これを行うには、フォームのコンストラクターに次のステートメントを追加します。  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [方法: Windows フォーム NotifyIcon コンポーネントを使用してアプリケーションアイコンをタスクバーに追加する](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [NotifyIcon コンポーネント](notifyicon-component-windows-forms.md)
- [NotifyIcon コンポーネントの概要](notifyicon-component-overview-windows-forms.md)
