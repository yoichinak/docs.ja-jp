---
title: ListBox の代わりに Windows フォーム ComboBox を使用する場合
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox control [Windows Forms], adding and removing items
- ListBox control [Windows Forms], vs. ComboBox
- bound controls [Windows Forms], combo boxes
- Windows Forms controls, data binding
- ComboBox control [Windows Forms], compared to ListBox
- combo boxes [Windows Forms], compared to list boxes
- ListBox control [Windows Forms], accessing items
- ListCount property
ms.assetid: 7bcaea58-1cfa-46db-9baf-b75a69d8f9ec
ms.openlocfilehash: 8a2429049acf1a22edde8d132ece17da4e91f1db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59111424"
---
# <a name="when-to-use-a-windows-forms-combobox-instead-of-a-listbox"></a>ListBox の代わりに Windows フォーム ComboBox を使用する場合
<xref:System.Windows.Forms.ComboBox>と<xref:System.Windows.Forms.ListBox>コントロールが似たような動作、およびいくつかの場合は互換性にあります。 ただしはどちらか一方のタスクをより適切な時間があります。  
  
 一般に、コンボ ボックスは、推奨される選択肢は、の一覧があるし、リスト ボックスは、一覧にあるものへの入力を制限する場合に適切なときに適しています。 コンボ ボックスには、一覧にない選択肢を入力するためのテキスト ボックスのフィールドが含まれています。 例外は、<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>プロパティに設定されて<xref:System.Windows.Forms.ComboBoxStyle.DropDownList>します。 その場合は、コントロールによって項目が選択の最初の文字を入力する場合。  
  
 さらに、コンボ ボックスは、フォームの領域を節約します。 下矢印をクリックするまでは完全な一覧が表示されないため、コンボ ボックスに簡単にリスト ボックスが収まらない小さなスペースに収まります。 例外は、ときに、<xref:System.Windows.Forms.ComboBox.DropDownStyle%2A>プロパティに設定されて<xref:System.Windows.Forms.ComboBoxStyle.Simple>: 完全な一覧が表示され、コンボ ボックスは、リスト ボックスよりも領域を増やす。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ComboBox>
- <xref:System.Windows.Forms.ListBox>
- [方法: Windows フォームの ComboBox、ListBox、または CheckedListBox コントロールに項目を追加または削除する](add-and-remove-items-from-a-wf-combobox.md)
- [方法: Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールを並べ替える](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [オプションのリストを表示するための Windows フォーム コントロール](windows-forms-controls-used-to-list-options.md)
