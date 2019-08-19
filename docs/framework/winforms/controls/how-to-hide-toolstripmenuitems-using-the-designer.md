---
title: '方法: デザイナーを使用して ToolStripMenuItems を非表示にする'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
ms.openlocfilehash: 968d34a5f79d469ef62beaa8ac96742d73391b22
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039742"
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>方法: デザイナーを使用して ToolStripMenuItems を非表示にする
メニュー項目を非表示にすることは、アプリケーションのユーザーインターフェイス (UI) を制御し、ユーザーコマンドを制限する方法です。 多くの場合、メニュー項目がすべて使用できなくなると、メニュー全体を非表示にすることができます。 これにより、ユーザーの取られるが減少します。 さらに、メニューまたはメニュー項目を非表示にしたり無効にしたりすることもできます。非表示にしても、ユーザーがショートカットキーを使用してメニューコマンドにアクセスするのを防ぐことはできません。 メニュー項目を無効にする方法の詳細[については、「方法:デザイナー](how-to-disable-toolstripmenuitems-using-the-designer.md)を使用して ToolStripMenuItems を無効にします。

## <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>トップレベルメニューとそのサブメニュー項目を非表示にするには

1. トップレベルのメニュー項目を選択し、その<xref:System.Windows.Forms.ToolStripItem.Visible%2A>プロパティ<xref:System.Windows.Forms.ToolStripItem.Available%2A>または`false`プロパティをに設定します。

     トップレベルメニュー項目を非表示にすると、そのメニュー内のすべてのメニュー項目も非表示になります。 [ <xref:System.Windows.Forms.MenuStrip> After] をに`false`設定<xref:System.Windows.Forms.ToolStripItem.Visible%2A>している以外の場所をクリックすると、最上位レベルのメニュー項目とそのサブメニュー項目全体がフォームから消え、アクションの実行時効果が表示されます。 デザイン時に、表示されていないトップレベルメニュー項目を表示<xref:System.Windows.Forms.MenuStrip>するには、**コンポーネントトレイ**、**ドキュメントアウトライン**、またはプロパティグリッドの上部で、をクリックします。

> [!NOTE]
>  マージシナリオでは、マルチドキュメントインターフェイス (MDI) 子メニューを除き、メニュー全体を非表示にすることはめったにありません。

## <a name="to-hide-a-submenu-item"></a>サブメニュー項目を非表示にするには

1. サブメニュー項目を選択し、 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>そのプロパティ`false`をに設定します。

     サブメニュー項目を非表示にすると、デザイン時にフォームに表示されたままになり、作業のために簡単に選択できるようになります。 実際には、実行時に非表示になります。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ToolStripItem.Visible%2A>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>
- <xref:System.Windows.Forms.ToolStripItem.Available%2A>
- <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>
- [MenuStrip コントロールの概要](menustrip-control-overview-windows-forms.md)
- [方法: デザイナーを使用して ToolStripMenuItems を無効にする](how-to-disable-toolstripmenuitems-using-the-designer.md)
