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
ms.openlocfilehash: 702a848631ce45c0efcb8eadfdf64074b454ac7d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097991"
---
# <a name="how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component"></a>方法: ショートカット メニューを Windows フォーム NotifyIcon コンポーネントに関連付ける
> [!NOTE]
>  <xref:System.Windows.Forms.MenuStrip>と<xref:System.Windows.Forms.ContextMenuStrip>が置換または追加する機能、<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>、以前のバージョン コントロール<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>を選択した場合に、旧バージョンとの互換性と将来の使用のため保持されます。  
  
 <xref:System.Windows.Forms.NotifyIcon>コンポーネントは、タスク バーの状態通知領域にアイコンを表示します。 一般的には、アプリケーションでは、コマンドが表すアプリケーションを送信するには、このアイコンを右クリックを有効にします。 関連付けることによって、<xref:System.Windows.Forms.ContextMenu>コンポーネントを<xref:System.Windows.Forms.NotifyIcon>コンポーネント、アプリケーションにこの機能を追加することができます。  
  
> [!NOTE]
>  インスタンスを表示するときに、起動時に最小化するアプリケーションの場合、<xref:System.Windows.Forms.NotifyIcon>タスク バーに、コンポーネント セットのメイン フォームの<xref:System.Windows.Forms.Form.WindowState%2A>プロパティを<xref:System.Windows.Forms.FormWindowState.Minimized>と必ず、<xref:System.Windows.Forms.NotifyIcon>コンポーネントの<xref:System.Windows.Forms.NotifyIcon.Visible%2A>プロパティ設定されている`true`します。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-at-design-time"></a>デザイン時に NotifyIcon コンポーネントのショートカット メニューを関連付ける  
  
1.  追加、<xref:System.Windows.Forms.NotifyIcon>をフォームにコンポーネントなど、重要なプロパティを設定し、<xref:System.Windows.Forms.NotifyIcon.Icon%2A>と<xref:System.Windows.Forms.NotifyIcon.Visible%2A>プロパティ。  
  
     詳細については、「[方法 :アプリケーション アイコンをタスク バーで、Windows フォームの NotifyIcon コンポーネントの追加](app-icons-to-the-taskbar-with-wf-notifyicon.md)します。  
  
2.  追加、<xref:System.Windows.Forms.ContextMenu>を Windows フォーム コンポーネント。  
  
     実行時に使用できるようにするコマンドを表すショートカット メニューにメニュー項目を追加します。 アクセス キーなど、これらのメニュー項目をメニューの拡張機能を追加するよい機会もです。  
  
3.  設定、<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>のプロパティ、<xref:System.Windows.Forms.NotifyIcon>コンポーネントを追加したショートカット メニュー。  
  
     このプロパティ設定すると、タスク バーのアイコンがクリックされたときに、ショートカット メニューが表示されます。  
  
### <a name="to-associate-a-shortcut-menu-with-the-notifyicon-component-programmatically"></a>NotifyIcon コンポーネントにプログラムでショートカット メニューを関連付ける  
  
1.  インスタンスを作成、<xref:System.Windows.Forms.NotifyIcon>クラスと<xref:System.Windows.Forms.ContextMenu>クラスのインスタンスとアプリケーションで必要なプロパティ設定 (<xref:System.Windows.Forms.NotifyIcon.Icon%2A>と<xref:System.Windows.Forms.NotifyIcon.Visible%2A>プロパティを<xref:System.Windows.Forms.NotifyIcon>コンポーネントのメニュー項目を<xref:System.Windows.Forms.ContextMenu>コンポーネントの場合)。  
  
2.  設定、<xref:System.Windows.Forms.NotifyIcon.ContextMenu%2A>のプロパティ、<xref:System.Windows.Forms.NotifyIcon>コンポーネントを追加したショートカット メニュー。  
  
     このプロパティ設定すると、タスク バーのアイコンがクリックされたときに、ショートカット メニューが表示されます。  
  
    > [!NOTE]
    >  次のコード例は、基本的なメニュー構造を作成します。 メニューの選択肢を開発しているアプリケーションに合わせてカスタマイズする必要があります。 さらに、処理するコードを記述するが、<xref:System.Windows.Forms.MenuItem.Click>これらのメニュー項目のイベント。  
  
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
>  初期化する必要があります`notifyIcon1`と`contextMenu1,`がフォームのコンス トラクターで、次のステートメントを含めることによって行うことができます。  
  
```cpp  
notifyIcon1 = gcnew System::Windows::Forms::NotifyIcon();  
contextMenu1 = gcnew System::Windows::Forms::ContextMenu();  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [方法: Windows フォームの NotifyIcon コンポーネントによってタスクバーにアプリケーション アイコンを追加する](app-icons-to-the-taskbar-with-wf-notifyicon.md)
- [NotifyIcon コンポーネント](notifyicon-component-windows-forms.md)
- [NotifyIcon コンポーネントの概要](notifyicon-component-overview-windows-forms.md)
