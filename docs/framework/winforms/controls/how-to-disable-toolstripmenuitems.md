---
title: '方法: ToolStripMenuItems を無効にします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
ms.openlocfilehash: 3c18935239a4355d5416a0a79d0fa9f5c504cc7e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720213"
---
# <a name="how-to-disable-toolstripmenuitems"></a>方法: ToolStripMenuItems を無効にします。
制限またはユーザーが実行を有効にして、ユーザーのアクティビティへの応答でのメニュー項目を無効にすると、コマンドの範囲を広げることができます。 これらが作成されますが、これで調整時にメニュー項目が既定で有効に、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティ。 デザイン時にこのプロパティを操作することができます、**プロパティ**ウィンドウまたはプログラムによってコードで設定します。  
  
### <a name="to-disable-a-menu-item-programmatically"></a>メニュー項目をプログラムで無効にするには  
  
-   メニュー項目のプロパティを設定するメソッド内で設定するコードを追加、<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティを`false`します。  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    >  メニューの最初または最上位のメニュー項目を無効にすると、メニュー内に含まれるすべてのメニュー項目を非表示になりますが、それらを無効にしません。 同様に、サブメニュー項目を持つメニュー項目を無効にする項目のサブメニュー項目を非表示になりますが、それらを無効にしません。 指定されたメニューのすべてのコマンドがユーザーに使用可能な場合は、これは、ユーザー インターフェイスを簡潔に非表示にして、メニュー全体を無効にすることをお勧めプログラミングと見なされます。 非表示にして、メニューを無効にして、単独で非表示にしてもアクセスするショートカット キーを使用してメニュー コマンドのために、すべてのアイテムと、メニューのサブメニュー項目を無効にするください。 設定、<xref:System.Windows.Forms.ToolStripItem.Visible%2A>トップレベルのメニュー項目のプロパティ`false`メニュー全体を非表示にします。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [方法: ToolStripMenuItems を非表示にします。](how-to-hide-toolstripmenuitems.md)
- [MenuStrip コントロールの概要](menustrip-control-overview-windows-forms.md)
