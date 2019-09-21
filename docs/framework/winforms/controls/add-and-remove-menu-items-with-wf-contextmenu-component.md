---
title: '方法: Windows フォーム ContextMenu コンポーネントのメニュー項目を追加および削除する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- context menus [Windows Forms], removing items
- ContextMenu component [Windows Forms], adding items
- shortcut menus [Windows Forms], removing items
- shortcut menus [Windows Forms], examples
- context menus [Windows Forms], adding items
- shortcut menus [Windows Forms], adding items
- ContextMenu component [Windows Forms], removing items
- context menus [Windows Forms], examples
- examples [Windows Forms], context menus
ms.assetid: 426d1eaf-7fb8-4b0b-8a33-5e8721786ea4
ms.openlocfilehash: 5d1862b1fc1398f0f8c2217b51c4efb93db639af
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957019"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>方法: Windows フォーム ContextMenu コンポーネントのメニュー項目を追加および削除する
Windows フォームでショートカットメニュー項目を追加および削除する方法について説明します。  
  
 Windows フォーム<xref:System.Windows.Forms.ContextMenu>コンポーネントには、選択したオブジェクトに関連する頻繁に使用するコマンドのメニューが用意されています。 <xref:System.Windows.Forms.MenuItem> オブジェクト<xref:System.Windows.Forms.Menu.MenuItems%2A>をコレクションに追加することで、ショートカットメニューに項目を追加できます。  
  
 ショートカットメニューから項目を完全に削除することができます。ただし、実行時には、代わりに項目を非表示にしたり無効にしたりする方が適切な場合があります。  
  
> [!IMPORTANT]
> <xref:System.Windows.Forms.MainMenu> とは、<xref:System.Windows.Forms.ContextMenu>以前のバージョン<xref:System.Windows.Forms.MainMenu>のとのコントロールに置き換えて機能を追加しますが、を選択した場合は、下位互換性と将来の使用の両方で保持されます。<xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.ContextMenuStrip> <xref:System.Windows.Forms.MenuStrip>  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>ショートカットメニューから項目を削除するには  
  
1. 特定のメニュー <xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A>項目を削除<xref:System.Windows.Forms.Menu.MenuItems%2A>するに<xref:System.Windows.Forms.ContextMenu>は、コンポーネントのコレクションのメソッドまたはメソッドを使用します。 <xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A>  
  
    ```vb  
    ' Removes the first item in the shortcut menu.  
    ContextMenu1.MenuItems.RemoveAt(0)  
    ' Removes a particular object from the shortcut menu.  
    ContextMenu1.MenuItems.Remove(mnuItemNew)  
    ```  
  
    ```csharp  
    // Removes the first item in the shortcut menu.  
    contextMenu1.MenuItems.RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1.MenuItems.Remove(mnuItemNew);  
    ```  
  
    ```cpp  
    // Removes the first item in the shortcut menu.  
    contextMenu1->MenuItems->RemoveAt(0);  
    // Removes a particular object from the shortcut menu.  
    contextMenu1->MenuItems->Remove(mnuItemNew);  
    ```  
  
     \- または -  
  
2. コンポーネントの`MenuItems`コレクションのメソッドを使用して、メニューからすべての項目を削除します。 `Clear` <xref:System.Windows.Forms.ContextMenu>  
  
    ```vb  
    ContextMenu1.MenuItems.Clear()  
    ```  
  
    ```csharp  
    contextMenu1.MenuItems.Clear();  
    ```  
  
    ```cpp  
    contextMenu1->MenuItems->Clear();  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ContextMenu>
- [ContextMenu コンポーネント](contextmenu-component-windows-forms.md)
- [ContextMenu コンポーネントの概要](contextmenu-component-overview-windows-forms.md)
