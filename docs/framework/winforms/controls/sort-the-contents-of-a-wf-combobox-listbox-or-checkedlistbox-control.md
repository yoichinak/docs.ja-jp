---
title: '方法: Windows の内容を並べ替えるフォーム ComboBox、ListBox、または CheckedListBox コントロール'
ms.date: 03/30/2017
helpviewer_keywords:
- CheckedListBox control [Windows Forms], sorting
- ComboBox control [Windows Forms], sorting contents
- combo boxes [Windows Forms], sorting contents
- list boxes [Windows Forms], sorting contents
- ListBox control [Windows Forms], sorting contents
ms.assetid: c268e387-3d1d-4d86-a940-19f6673c8d06
ms.openlocfilehash: 4c00e853299c6eea2c97adb7f94cd7753ffa3d93
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705266"
---
# <a name="how-to-sort-the-contents-of-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>方法: Windows の内容を並べ替えるフォーム ComboBox、ListBox、または CheckedListBox コントロール
Windows フォーム コントロールでは、データ バインドされるときに並べ替えられません。 並べ替えられたデータを表示するには、並べ替えをサポートするデータ ソースを使用して、並べ替え、データ ソース。 並べ替えをサポートするデータ ソースはデータ ビュー、データのビュー マネージャー、および並べ替えられた配列。  
  
 コントロールがデータ バインドでない場合は、それを並べ替えることができます。  
  
### <a name="to-sort-the-list"></a>一覧を並べ替える  
  
1.  `Sorted` プロパティを `true`に設定します。  
  
     この設定は、並べ替えられた順序ですべての既存のリスト アイテムを再配置します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- <xref:System.Windows.Forms.CheckedListBox>
- [Windows フォームでのデータ バインディング](../windows-forms-data-binding.md)
- [方法: 追加および削除項目、Windows からフォーム ComboBox、ListBox、または CheckedListBox コントロール](add-and-remove-items-from-a-wf-combobox.md)
- [ListBox の代わりに Windows フォーム ComboBox を使用する場合](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [オプションのリストを表示するための Windows フォーム コントロール](windows-forms-controls-used-to-list-options.md)
