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
ms.openlocfilehash: 2203511e91254c270c59b5d298dd87a5b3737109
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59308361"
---
# <a name="how-to-move-toolstripmenuitems"></a>方法: ToolStripMenuItems を移動する
デザイン時に移動できますトップレベル メニュー全体とそのメニュー項目を別の場所、<xref:System.Windows.Forms.MenuStrip>します。 トップレベル メニュー間で個々 のメニュー項目を移動またはメニュー内でのメニュー項目の位置を変更することもできます。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a>トップレベル メニューとメニュー項目を最上位レベルの別の場所に移動するには  
  
1. クリックして、移動するメニューにマウスの左ボタンを押したままにします。  
  
2. 新しい場所の前にあるトップレベル メニューにカーソルをドラッグし、マウスの左ボタンを放します。  
  
     選択したメニューは、カーソルの右側に移動します。  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a>トップレベル メニューとメニュー項目をドロップダウン リストの場所に移動するには  
  
1. 移動、CTRL + X キーを押すとメニューを右クリックしてや選択するメニューを左クリックして**切り取り**ショートカット メニューから。  
  
2. 宛先のトップレベル メニューで新しい場所の上のメニュー項目を左クリックし CTRL + V キーを押して新しい場所の上のメニュー項目を右クリックしてや選択**貼り付け**ショートカット メニューから。  
  
     切り取ったメニューは、選択したメニュー項目の後に挿入されます。  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a>項目コレクション エディターを使用してメニュー内のメニュー項目を移動するには  
  
1. 移動するメニュー項目を含むメニューを右クリックします。  
  
2. ショートカット メニューの**編集ドロップダウン項目です**します。  
  
3. **Items コレクション エディター**、移動するメニュー項目を左クリックします。  
  
4. メニュー内のメニュー項目を移動する、上下矢印キーをクリックします。  
  
5. **[OK]** をクリックします。  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a>キーボードを使用してメニュー内のメニュー項目を移動するには  
  
1. キーを押して、ALT キーを押したままにします。  
  
2. 移動するメニュー項目をマウスの左ボタンを押したままにします。  
  
3. メニュー項目を新しい場所にドラッグし、マウスの左ボタンを離します。  
  
### <a name="to-move-a-menu-item-to-another-menu"></a>別のメニューにメニュー項目を移動するには  
  
1. 移動、CTRL + X キーを押すとメニュー項目を右クリックしてや選択するメニュー項目を左クリックして**切り取り**ショートカット メニューから。  
  
2. 切り取りメニュー項目を含むメニューをクリックします。  
  
3. 新しい場所の前にあるメニュー項目を左クリックし、ctrl キーを押しながら V キーを押してまたはクリックし、新しい場所の前にあるメニュー項目を右クリックして**貼り付け**ショートカット メニューから。  
  
     切り取りメニュー項目が選択されているメニュー項目の後に挿入されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [MenuStrip コントロールの概要 (Windows フォーム)](menustrip-control-overview-windows-forms.md)
