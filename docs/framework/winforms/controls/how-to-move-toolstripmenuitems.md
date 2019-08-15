---
title: '方法: ToolStripMenuItems を移動する'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
ms.openlocfilehash: adf25973fde790937461007bd0106cca02dd83be
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039798"
---
# <a name="how-to-move-toolstripmenuitems"></a>方法: ToolStripMenuItems を移動する
デザイン時に、トップレベルのメニューとそのメニュー項目全体を上<xref:System.Windows.Forms.MenuStrip>の別の場所に移動できます。 また、トップレベルメニュー間で個々のメニュー項目を移動したり、メニュー内のメニュー項目の位置を変更したりすることもできます。

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>トップレベルメニューとそのメニュー項目を別のトップレベルの場所に移動するには

1. 移動するメニューのマウスの左ボタンをクリックして、押したままにします。

2. 挿入ポイントを、目的の新しい位置の前にあるトップレベルメニューにドラッグし、マウスの左ボタンを離します。

     選択したメニューがカーソル位置の右に移動します。

## <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>トップレベルメニューとそのメニュー項目をドロップダウン位置に移動するには

1. 移動するメニューを左クリックし、CTRL + X キーを押します。または、メニューを右クリックし、ショートカットメニューの **[切り取り]** を選択します。

2. 移動先のトップレベルメニューで、目的の新しい場所の上にあるメニュー項目を左クリックし、CTRL + V キーを押すか、または目的の新しい場所の上にあるメニュー項目を右クリックして、ショートカットメニューから **[貼り付け]** を選択します。

     切り取ったメニューは、選択したメニュー項目の後に挿入されます。

## <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>項目コレクションエディターを使用してメニュー内のメニュー項目を移動するには

1. 移動するメニュー項目が含まれているメニューを右クリックします。

2. ショートカットメニューの **[DropDownItems の編集]** をクリックします。

3. **Items コレクションエディター**で、移動するメニュー項目を左クリックします。

4. メニュー内のメニュー項目を移動するには、上下の方向キーをクリックします。

5. **[OK]** をクリックします。

## <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>キーボードを使用してメニュー内のメニュー項目を移動するには

1. ALT キーを押したままにします。

2. 移動するメニュー項目のマウスの左ボタンをクリックしたままにします。

3. メニュー項目を新しい位置にドラッグし、マウスの左ボタンを離します。

## <a name="to-move-a-menu-item-to-another-menu"></a>メニュー項目を別のメニューに移動するには

1. 移動するメニュー項目を左クリックし、CTRL + X キーを押します。または、メニュー項目を右クリックし、ショートカットメニューの **[切り取り]** をクリックします。

2. 切り取ったメニュー項目を含むメニューを左クリックします。

3. 目的の新しい場所の前にあるメニュー項目を左クリックし、CTRL + V キーを押します。または、新しい場所の前にあるメニュー項目を右クリックし、ショートカットメニューから **[貼り付け]** を選択します。

     切り取ったメニュー項目は、選択したメニュー項目の後に挿入されます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip コントロールの概要](menustrip-control-overview-windows-forms.md)
