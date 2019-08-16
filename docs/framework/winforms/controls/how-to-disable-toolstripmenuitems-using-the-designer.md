---
title: '方法: デザイナーを使用して ToolStripMenuItems を無効にする'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: fd80a6543c83ae957cd9c51b068d0702559f0925
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040273"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>方法: デザイナーを使用して ToolStripMenuItems を無効にする
ユーザーの操作に応じてメニュー項目を有効または無効にすることによって、ユーザーが実行できるコマンドを制限または拡大できます。 メニュー項目は、作成時に既定で有効になりますが、プロパティを<xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>使用して調整できます。 このプロパティは、デザイン時に **[プロパティ]** ウィンドウで操作することも、コードで設定することによってプログラムで操作することもできます。 詳細については、「[方法 :ToolStripMenuItems](how-to-disable-toolstripmenuitems.md)を無効にします。

## <a name="to-disable-a-menu-item-at-design-time"></a>デザイン時にメニュー項目を無効にするには

1. フォームでメニュー項目を選択した状態で、 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>プロパティを`false`に設定します。

    > [!TIP]
    >  メニューの1つ目または最上位レベルのメニュー項目を無効にすると、メニュー内に含まれるすべてのメニュー項目が無効になります。 同様に、サブメニュー項目を含むメニュー項目を無効にすると、サブメニュー項目が無効になります。 特定のメニューのすべてのコマンドをユーザーが使用できない場合は、そのメニュー全体を非表示にして無効にすることをお勧めします。これにより、クリーンなユーザーインターフェイスが提供されます。 非表示にすると、ショートカットキーを使用してメニューコマンドにアクセスできなくなるため、メニューを非表示にしたり無効にしたりする必要があります。 トップレベルメニュー項目の`false` プロパティをに設定すると、メニュー全体が非表示になります。<xref:System.Windows.Forms.ToolStripItem.Visible%2A>

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [方法: ToolStripMenuItems の非表示](how-to-hide-toolstripmenuitems.md)
- [MenuStrip コントロールの概要](menustrip-control-overview-windows-forms.md)
