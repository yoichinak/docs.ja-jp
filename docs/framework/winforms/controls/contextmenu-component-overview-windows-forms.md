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
ms.openlocfilehash: 6ae7817bc158f30fbf55b5f6228ecdf134d6657d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962182"
---
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu コンポーネントの概要 (Windows フォーム)
> [!IMPORTANT]
> <xref:System.Windows.Forms.MainMenu> とは、<xref:System.Windows.Forms.ContextMenu>以前のバージョン<xref:System.Windows.Forms.MainMenu>のとのコントロールに置き換えて機能を追加しますが、を選択した場合は、下位互換性と将来の使用の両方で保持されます。<xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.ContextMenuStrip> <xref:System.Windows.Forms.MenuStrip>  
  
 Windows フォーム<xref:System.Windows.Forms.ContextMenu>コンポーネントを使用すると、選択したオブジェクトに関連付けられている頻繁に使用するコマンドのショートカットメニューをユーザーに提供できます。 ショートカットメニューの項目は、多くの場合、アプリケーションの他の場所に表示されるメインメニューの項目のサブセットです。 ユーザーは、通常、マウスを右クリックしてショートカットメニューにアクセスできます。 Windows フォームでは、ショートカットメニューはコントロールに関連付けられています。  
  
## <a name="key-properties"></a>キー プロパティ  
 コントロールの<xref:System.Windows.Forms.Control.ContextMenu%2A>プロパティを<xref:System.Windows.Forms.ContextMenu>コンポーネントに設定することによって、ショートカットメニューをコントロールに関連付けることができます。 1つのショートカットメニューを複数のコントロールに関連付けることができますが、各コントロールにはショートカットメニューを1つしか含めることができません。  
  
 <xref:System.Windows.Forms.ContextMenu>コンポーネントのキープロパティは、 <xref:System.Windows.Forms.Menu.MenuItems%2A>プロパティです。 プログラムによってオブジェクトを作成<xref:System.Windows.Forms.MenuItem>し、ショートカットメニューのに追加することによって、 <xref:System.Windows.Forms.Menu.MenuItemCollection>メニュー項目を追加できます。 ショートカットメニュー内の項目は通常、他のメニューから描画されるので、ほとんどの場合、項目をコピーすることでショートカットメニューに追加します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
