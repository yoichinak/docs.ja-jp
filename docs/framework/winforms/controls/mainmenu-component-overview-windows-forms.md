---
title: MainMenu コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: 6c2c33c8c03751e87d71e65523b82d92b18f31c4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709872"
---
# <a name="mainmenu-component-overview-windows-forms"></a>MainMenu コンポーネントの概要 (Windows フォーム)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.MenuStrip>と<xref:System.Windows.Forms.ContextMenuStrip>が置換または追加する機能、<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>、以前のバージョン コントロール<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>を選択した場合に、旧バージョンとの互換性と将来の使用のため保持されます。  
  
 Windows フォーム<xref:System.Windows.Forms.MainMenu>コンポーネントには、実行時にメニューが表示されます。 メイン メニューおよび個々 の項目のすべてのサブメニューは<xref:System.Windows.Forms.MenuItem>オブジェクト。  
  
## <a name="key-properties"></a>キー プロパティ  
 メニュー項目は、設定して既定の項目として指定できる、<xref:System.Windows.Forms.MenuItem.DefaultItem%2A>プロパティを`true`します。 メニューをクリックすると、太字のテキストで、既定の項目が表示されます。 メニュー項目の<xref:System.Windows.Forms.MenuItem.Checked%2A>プロパティが`true`または`false`、メニュー項目が選択されているかどうかを示します。 メニュー項目の<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>プロパティが選択された項目の外観をカスタマイズ: 場合<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>に設定されている`true`場合に、項目の横にあるラジオ ボタンが表示されます<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>に設定されている`false`項目の横にあるチェック マークが表示されます。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [MenuStrip コントロールの概要](menustrip-control-overview-windows-forms.md)
