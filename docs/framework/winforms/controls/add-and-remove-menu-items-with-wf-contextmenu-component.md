---
title: '方法: 追加し、Windows フォーム ContextMenu コンポーネントのメニュー項目の削除'
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
ms.openlocfilehash: 8b63182bdb37e47a71bee2d22500263cd4889ac9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57725065"
---
# <a name="how-to-add-and-remove-menu-items-with-the-windows-forms-contextmenu-component"></a>方法: 追加し、Windows フォーム ContextMenu コンポーネントのメニュー項目の削除
追加し、Windows フォームのショートカット メニュー項目を削除する方法について説明します。  
  
 Windows フォーム<xref:System.Windows.Forms.ContextMenu>コンポーネントは、選択したオブジェクトに関連するよく使用するコマンドのメニューを提供します。 ショートカット メニューに項目を追加するには追加することで<xref:System.Windows.Forms.MenuItem>オブジェクトを<xref:System.Windows.Forms.Menu.MenuItems%2A>コレクション。  
  
 項目を完全に; ショートカット メニューから削除することができます。ただし、実行時に非表示にするか、代わりに、項目を無効にするのには適切な時間がられます。  
  
> [!IMPORTANT]
>  <xref:System.Windows.Forms.MenuStrip>と<xref:System.Windows.Forms.ContextMenuStrip>が置換または追加する機能、<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>、以前のバージョン コントロール<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>を選択した場合に、旧バージョンとの互換性と将来の使用のため保持されます。  
  
### <a name="to-remove-items-from-a-shortcut-menu"></a>ショートカット メニューから項目を削除するには  
  
1.  使用して、<xref:System.Windows.Forms.Menu.MenuItemCollection.Remove%2A>または<xref:System.Windows.Forms.Menu.MenuItemCollection.RemoveAt%2A>のメソッド、<xref:System.Windows.Forms.Menu.MenuItems%2A>のコレクション、<xref:System.Windows.Forms.ContextMenu>特定のメニュー項目を削除するコンポーネント。  
  
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
  
     - または -  
  
2.  使用して、`Clear`のメソッド、`MenuItems`のコレクション、 <xref:System.Windows.Forms.ContextMenu>  メニューからすべての項目を削除するコンポーネント。  
  
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
