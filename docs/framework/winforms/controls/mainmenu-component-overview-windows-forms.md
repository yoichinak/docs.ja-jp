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
ms.openlocfilehash: fe46683faee13bad951d5a7185aad8a687c290ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952135"
---
# <a name="mainmenu-component-overview-windows-forms"></a>MainMenu コンポーネントの概要 (Windows フォーム)
> [!IMPORTANT]
> <xref:System.Windows.Forms.MainMenu> とは、<xref:System.Windows.Forms.ContextMenu>以前のバージョン<xref:System.Windows.Forms.MainMenu>のとのコントロールに置き換えて機能を追加しますが、を選択した場合は、下位互換性と将来の使用の両方で保持されます。<xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.ContextMenuStrip> <xref:System.Windows.Forms.MenuStrip>  
  
 Windows フォーム<xref:System.Windows.Forms.MainMenu>コンポーネントは、実行時にメニューを表示します。 メインメニューのすべてのサブメニューと個々の<xref:System.Windows.Forms.MenuItem>項目はオブジェクトです。  
  
## <a name="key-properties"></a>キー プロパティ  
 メニュー項目は、 <xref:System.Windows.Forms.MenuItem.DefaultItem%2A>プロパティをに設定する`true`ことによって、既定の項目として指定できます。 メニューがクリックされると、既定の項目が太字で表示されます。 メニュー項目の<xref:System.Windows.Forms.MenuItem.Checked%2A>プロパティは、また`true`は`false`のいずれかで、メニュー項目が選択されているかどうかを示します。 メニュー <xref:System.Windows.Forms.MenuItem.RadioCheck%2A>項目のプロパティは、選択した項目の外観をカスタマイズ<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>します。 `true`がに設定されている場合、項目の<xref:System.Windows.Forms.MenuItem.RadioCheck%2A>横にオプション`false`ボタンが表示されます。がに設定されている場合は、項目の横にチェックマークが表示されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [MenuStrip コントロールの概要](menustrip-control-overview-windows-forms.md)
