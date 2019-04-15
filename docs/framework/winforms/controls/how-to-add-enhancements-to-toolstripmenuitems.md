---
title: '方法: ToolStripMenuItems に拡張機能を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- commands [Windows Forms], grouping on menus
- check marks [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], displaying access keys
- menus [Windows Forms], grouping commands
- menu items [Windows Forms], displaying shortcut keys
- ToolStripMenuItems
- separators [Windows Forms], displaying on menus
- menu items [Windows Forms], showing separators
- menu items [Windows Forms], adding check marks
- ToolStripMenuItems [Windows Forms], adding check marks
- menu items [Windows Forms], adding images
- ToolStripSeparators [Windows Forms], displaying on MenuStrips
- menu items [Windows Forms], displaying access keys
- ToolStripMenuItems [Windows Forms], displaying shortcut keys
- ToolStripMenuItems [Windows Forms], adding images
- keyboard shortcuts [Windows Forms], displaying on menus
- images [Windows Forms], adding to menus
- ToolStripMenuItems [Windows Forms], showing separator bars
ms.assetid: aa5f19bb-b545-4378-bfa6-36ba592f0d7c
ms.openlocfilehash: 458347df7e17aabc1e9e21d66ad1b5a96200fe28
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198557"
---
# <a name="how-to-add-enhancements-to-toolstripmenuitems"></a>方法: ToolStripMenuItems に拡張機能を追加する
使いやすさを強化する<xref:System.Windows.Forms.MenuStrip>と<xref:System.Windows.Forms.ContextMenuStrip>次の方法でコントロール。  
  
-   ワード プロセッシング アプリケーションでは、余白に、ルーラーを表示するかどうかなど、オンまたはオフ、機能を有効になっているかどうかを指定する、またはファイルの一覧で、どのファイルが表示されてこのようなのかを示すチェック マークを追加、**ウィンドウ**メニュー。  
  
-   視覚的にメニュー コマンドを表すイメージを追加します。  
  
-   コマンドを実行するために、マウスの代わりにキーボードを提供するショートカット キーを表示します。 たとえば、実行 CTRL + C キーを押して、**コピー**コマンド。  
  
-   メニュー ナビゲーションのマウス、キーボードの代わりを提供するアクセス キーを表示します。 たとえば、alt キーを押しながら F キーを押してが選択、**ファイル**メニュー。  
  
-   関連するコマンドをグループ化し、メニューを読みやすくのセパレーター バーを表示します。  
  
### <a name="to-display-a-check-mark-on-a-menu-command"></a>メニュー コマンドにチェック マークを表示するには  
  
-   設定の<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>プロパティを`true`します。  
  
     これも設定、<xref:System.Windows.Forms.ToolStripMenuItem.CheckState%2A>プロパティを`true`します。 メニュー コマンドが選択されているかどうかに関係なく、既定でチェック マークを付けて表示をする場合にのみ、この手順を使用します。  
  
### <a name="to-display-a-check-mark-that-changes-state-with-each-click"></a>クリックするたびに状態を変更するチェック マークを表示するには  
  
-   設定、メニュー コマンドの<xref:System.Windows.Forms.ToolStripMenuItem.CheckOnClick%2A>プロパティを`true`します。  
  
### <a name="to-add-an-image-to-a-menu-command"></a>メニュー コマンドにイメージを追加するには  
  
-   設定、メニュー コマンドの<xref:System.Windows.Forms.ToolStripItem.Image%2A>プロパティをイメージの名前にします。 場合、<xref:System.Windows.Forms.ToolStripItemDisplayStyle>このメニュー コマンドのプロパティに設定されて<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>または<xref:System.Windows.Forms.ToolStripItemDisplayStyle.None>イメージを表示することはできません。  
  
> [!NOTE]
>  イメージの余白も表示できます、チェック マークできます。 また、設定、<xref:System.Windows.Forms.ToolStripMenuItem.Checked%2A>するイメージのプロパティ`true`、およびイメージは、実行時にハッチ境界線と共に表示されます。  
  
### <a name="to-display-a-shortcut-key-for-a-menu-command"></a>メニュー コマンドのショートカット キーを表示するには  
  
-   設定、メニュー コマンドの<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys%2A>プロパティの CTRL + O など、目的のキーボードの組み合わせを**オープン**メニュー コマンド、およびセット、<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>プロパティを`true`します。  
  
### <a name="to-display-custom-shortcut-keys-for-a-menu-command"></a>メニュー コマンドのカスタム ショートカット キーを表示するには  
  
-   設定、メニュー コマンドの<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A>プロパティ SHIFT + CTRL + O とセットではなく、CTRL + SHIFT + O など、目的のキーボードの組み合わせを<xref:System.Windows.Forms.ToolStripMenuItem.ShowShortcutKeys%2A>プロパティを`true`します。  
  
### <a name="to-display-an-access-key-for-a-menu-command"></a>メニュー コマンドのアクセス キーを表示するには  
  
-   設定すると、<xref:System.Windows.Forms.ToolStripItem.Text%2A>メニュー コマンドは、プロパティは、アンパサンドを入力します。 (&) は、アクセス キーと下線付きで表示する文字の前にします。 たとえば、入力`&Open`として、<xref:System.Windows.Forms.ToolStripItem.Text%2A>として表示されるメニュー コマンドとメニュー項目のプロパティ、 <u>O</u>ペン。
  
     このメニュー コマンドに移動する、フォーカスを移す ALT キーを押し、<xref:System.Windows.Forms.MenuStrip>メニュー名のアクセス キーを押します。 メニューが開きアクセス キーを持つ項目が表示されます、ときにのみ、メニュー コマンドを選択するアクセス キーを押す必要があります。  
  
> [!NOTE]
>  同じメニュー システムで 2 回 ALT キーを押しながら F キーを定義するなどの重複するアクセス キーを定義しないでください。 重複するアクセス キーの選択順序を保証できません。  
  
### <a name="to-display-a-separator-bar-between-menu-commands"></a>メニュー コマンドの間の区切り線を表示するには  
  
-   定義した後、<xref:System.Windows.Forms.MenuStrip>と項目が含まれます使用して、<xref:System.Windows.Forms.ToolStripItemCollection.AddRange%2A>または<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>メニュー コマンドを追加するメソッドをおよび<xref:System.Windows.Forms.ToolStripSeparator>にコントロールを<xref:System.Windows.Forms.MenuStrip>順序で。  
  
    ```vb  
    ' This code adds a top-level File menu to the MenuStrip.  
    Me.menuStrip1.Items.Add(New ToolStripMenuItem() _  
    {Me.fileToolStripMenuItem})  
  
    ' This code adds the New and Open menu commands, a separator bar,   
    ' and the Save and Exit menu commands to the top-level File menu,   
    ' in that order.  
    Me.fileToolStripMenuItem.DropDownItems.AddRange(New _  
    ToolStripMenuItem() {Me.newToolStripMenuItem, _  
    Me.openToolStripMenuItem, Me.toolStripSeparator1, _  
    Me.saveToolStripMenuItem, Me.exitToolStripMenuItem})  
    ```  
  
    ```csharp  
    // This code adds a top-level File menu to the MenuStrip.  
    this.menuStrip1.Items.Add(new ToolStripItem[]_  
    {this.fileToolStripMenuItem});  
  
    // This code adds the New and Open menu commands, a separator bar,   
    // and the Save and Exit menu commands to the top-level File menu,   
    // in that order.  
    this.fileToolStripMenuItem.DropDownItems.AddRange(new _  
    ToolStripItem[] {  
    this.newToolStripMenuItem,  
    this.openToolStripMenuItem,  
    this.toolStripSeparator1,  
    this.saveToolStripMenuItem,  
    this.exitToolStripMenuItem});  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip コントロールの概要](menustrip-control-overview-windows-forms.md)
