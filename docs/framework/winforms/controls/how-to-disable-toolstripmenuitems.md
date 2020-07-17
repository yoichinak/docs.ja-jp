---
title: '方法: ToolStripMenuItems を無効にする'
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
ms.openlocfilehash: f86a2934e799e4604693491dacbecc517d44d810
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046226"
---
# <a name="how-to-disable-toolstripmenuitems"></a>方法: ToolStripMenuItems を無効にする
ユーザーの操作に応じてメニュー項目を有効または無効にすることによって、ユーザーが実行できるコマンドを制限または拡大できます。 メニュー項目は、作成時に既定で有効になりますが、プロパティを<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>使用して調整できます。 このプロパティは、デザイン時に **[プロパティ]** ウィンドウで操作することも、コードで設定することによってプログラムで操作することもできます。  
  
### <a name="to-disable-a-menu-item-programmatically"></a>プログラムによってメニュー項目を無効にするには  
  
- メニュー項目のプロパティを設定するメソッド内で、 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティをに`false`設定するコードを追加します。  
  
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
    > メニューの1つ目または最上位レベルのメニュー項目を無効にすると、メニュー内に含まれるすべてのメニュー項目が非表示になりますが、無効にはなりません。 同様に、サブメニュー項目を含むメニュー項目を無効にしても、サブメニュー項目は非表示になりますが、無効にはなりません。 特定のメニューのすべてのコマンドをユーザーが使用できない場合は、そのメニュー全体を非表示にして無効にすることをお勧めします。これにより、クリーンなユーザーインターフェイスが提供されます。 メニューを非表示にして無効にし、メニューのすべての項目とサブメニュー項目を無効にする必要があります。非表示にしても、ショートカットキーを使用してメニューコマンドにアクセスすることはできないためです。 トップレベルメニュー項目の`false` プロパティをに設定すると、メニュー全体が非表示になります。<xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [方法: ToolStripMenuItems の非表示](how-to-hide-toolstripmenuitems.md)
- [MenuStrip コントロールの概要](menustrip-control-overview-windows-forms.md)
