---
title: '方法: Windows フォームの NotifyIcon コンポーネントによってタスクバーにアプリケーション アイコンを追加します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- TrayIcon
helpviewer_keywords:
- status area icons
- icons [Windows Forms], adding to taskbar
- NotifyIcon component
- taskbar [Windows Forms], adding icons
ms.assetid: d28c0fe6-aaf2-4df7-ad74-928d861a8510
ms.openlocfilehash: 04f6b98a2206371a2838b3a6952feeafcd788309
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714256"
---
# <a name="how-to-add-application-icons-to-the-taskbar-with-the-windows-forms-notifyicon-component"></a>方法: Windows フォームの NotifyIcon コンポーネントによってタスクバーにアプリケーション アイコンを追加します。
Windows フォーム<xref:System.Windows.Forms.NotifyIcon>コンポーネントは、タスク バーの状態通知領域に 1 つのアイコンを表示します。 を、ステータス領域に複数のアイコンを表示するには、複数がする必要があります<xref:System.Windows.Forms.NotifyIcon>フォーム上のコンポーネント。 コントロールに表示されるアイコンを設定するには、使用、<xref:System.Windows.Forms.NotifyIcon.Icon%2A>プロパティ。 コードを記述することも、<xref:System.Windows.Forms.NotifyIcon.DoubleClick>ユーザー アイコンをダブルクリックしたときの動作のためのイベント ハンドラー。 たとえば、アイコンで表される、バック グラウンド プロセスを構成するユーザーの表示 ダイアログ ボックスを行うことができます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.NotifyIcon>コンポーネントは、通知の目的でのみ、アクションまたはイベントが発生したアラートのユーザーに使用または何らかのステータスの変更が発生しました。 によるアプリケーションの標準的な操作のメニューのツールバー、およびその他のユーザー インターフェイス要素を使用する必要があります。  
  
### <a name="to-set-the-icon"></a>アイコンを設定するには  
  
1.  値を割り当てる、<xref:System.Windows.Forms.NotifyIcon.Icon%2A>プロパティ。 値型でなければなりません`System.Drawing.Icon`.ico ファイルから読み込むことができるとします。 コードで、または、省略記号ボタンをクリックして、アイコン ファイルを指定できます (![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")) 横に、<xref:System.Windows.Forms.NotifyIcon.Icon%2A>プロパティ、 **プロパティ**ウィンドウとでファイルを選択し、**オープン**表示されるダイアログ ボックス。  
  
2.  <xref:System.Windows.Forms.NotifyIcon.Visible%2A> プロパティを `true`に設定します。  
  
3.  設定、<xref:System.Windows.Forms.NotifyIcon.Text%2A>プロパティを適切なツールヒント文字列。  
  
     アイコンの場所は次のコード例で、パスが設定、 **My Documents**フォルダー。 この場所は、Windows オペレーティング システムを実行しているほとんどのコンピューターにはでこのフォルダーが含まれていると想定できるために使用されます。 この場所を選択すると、ユーザーは最小限のシステム アクセスのレベルでアプリケーションを安全に実行もできます。 次の例では、使用して、フォームが必要です、<xref:System.Windows.Forms.NotifyIcon>コントロールが既に追加されています。 という名前のアイコン ファイルも必要があります。`Icon.ico`します。  
  
    ```vb  
    ' You should replace the bold icon in the sample below  
    ' with an icon of your own choosing.  
    NotifyIcon1.Icon = New _   
       System.Drawing.Icon(System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Icon.ico")  
    NotifyIcon1.Visible = True  
    NotifyIcon1.Text = "Antivirus program"  
    ```  
  
    ```csharp  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    // Note the escape character used (@) when specifying the path.  
    notifyIcon1.Icon =   
       new System.Drawing.Icon (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Icon.ico");  
    notifyIcon1.Visible = true;  
    notifyIcon1.Text = "Antivirus program";  
    ```  
  
    ```cpp  
    // You should replace the bold icon in the sample below  
    // with an icon of your own choosing.  
    notifyIcon1->Icon = gcnew   
       System::Drawing::Icon(String::Concat  
       (System::Environment::GetFolderPath  
       (System::Environment::SpecialFolder::Personal),  
       "\\Icon.ico"));  
    notifyIcon1->Visible = true;  
    notifyIcon1->Text = "Antivirus program";  
    ```  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.NotifyIcon>
- <xref:System.Windows.Forms.NotifyIcon.Icon%2A>
- [方法: ショートカット メニューを Windows フォームの NotifyIcon コンポーネントに関連付ける](how-to-associate-a-shortcut-menu-with-a-windows-forms-notifyicon-component.md)
- [NotifyIcon コンポーネント](notifyicon-component-windows-forms.md)
- [NotifyIcon コンポーネントの概要](notifyicon-component-overview-windows-forms.md)
