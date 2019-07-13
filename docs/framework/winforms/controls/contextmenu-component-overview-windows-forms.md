---
title: ContextMenu コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 2acbcc9197a630a993471c22e572a4f3ed682c64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956053"
---
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu コンポーネントの概要 (Windows フォーム)
> [!IMPORTANT]
>  <xref:System.Windows.Forms.MenuStrip>と<xref:System.Windows.Forms.ContextMenuStrip>が置換または追加する機能、<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>、以前のバージョン コントロール<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>を選択した場合に、旧バージョンとの互換性と将来の使用のため保持されます。  
  
 Windows フォームで<xref:System.Windows.Forms.ContextMenu>コンポーネントを選択したオブジェクトに関連付けられているコマンドを頻繁に使用されるを簡単にアクセスできるショートカット メニューをユーザーに提供できます。 ショートカット メニュー内の項目は、多くの場合、アプリケーションで別の場所に表示されるメインのメニューから項目のサブセットです。 ユーザーは、マウスを右クリックしてショートカット メニューを通常はアクセスできます。 Windows フォームには、ショートカット メニューは、コントロールに関連付けられます。  
  
## <a name="key-properties"></a>キー プロパティ  
 コントロールにするには、コントロールのショートカット メニューを関連付けることができます<xref:System.Windows.Forms.Control.ContextMenu%2A>プロパティを<xref:System.Windows.Forms.ContextMenu>コンポーネント。 単一のショートカット メニューが複数のコントロールに関連付けることができますが、各コントロールは、1 つだけのショートカット メニューを持つことができます。  
  
 キー プロパティ、<xref:System.Windows.Forms.ContextMenu>コンポーネントは、<xref:System.Windows.Forms.Menu.MenuItems%2A>プロパティ。 メニュー項目を追加するにはプログラムで作成して<xref:System.Windows.Forms.MenuItem>オブジェクトと追加すること、<xref:System.Windows.Forms.Menu.MenuItemCollection>のショートカット メニュー。 ショートカット メニュー内の項目は、その他のメニューから描画は通常、ためは、コピーすることで項目のショートカット メニューを最も頻繁に追加します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
