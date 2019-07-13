---
title: ComboBox コントロールの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- ComboBox
helpviewer_keywords:
- drop-down lists [Windows Forms], Windows Forms
- ComboBox control [Windows Forms], about ComboBox control
- drop-down lists [Windows Forms], ComboBox control
- combo boxes [Windows Forms], about combo boxes
ms.assetid: a58b393f-a614-45d1-8961-857a024b5acd
ms.openlocfilehash: 80056771744c9b97828a024adf32638e545a839e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956170"
---
# <a name="combobox-control-overview-windows-forms"></a>ComboBox コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.ComboBox>ドロップダウン コンボ ボックスにデータを表示するコントロールを使用します。 既定では、<xref:System.Windows.Forms.ComboBox>コントロールは、2 つの部分が表示されます。 最上位部分は、ユーザーがリスト項目を入力できるテキスト ボックス。 2 番目の部分は、元のユーザーが選択できる 1 つの項目の一覧を表示するリスト ボックスです。 コンボ ボックスの他のスタイルの詳細については、次を参照してください。 [Windows フォーム ComboBox Instead of リスト ボックスを使用するときに](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)します。  
  
 <xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>プロパティは、選択した項目に対応する整数値を返します。 プログラムで変更することで、選択した項目を変更することができます、<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>コード内の値は、対応する項目の一覧では、コンボ ボックスのテキスト ボックスの部分に表示されます。 項目が選択されていない場合、<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>値は-1 です。 一覧の最初の項目が選択されている場合、<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>値は 0 です。 <xref:System.Windows.Forms.ComboBox.SelectedItem%2A>プロパティは<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>文字列値では、通常は、アイテム自体が返されます。 <xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A>プロパティには、リスト内の項目の数との値が反映されます、<xref:System.Windows.Forms.ComboBox.ObjectCollection.Count%2A>プロパティは、常に 1 つ以上の最大の可能な限り<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>ため、その値<xref:System.Windows.Forms.ComboBox.SelectedIndex%2A>は 0 から始まります。  
  
 項目を追加または削除、<xref:System.Windows.Forms.ComboBox>コントロールを使用して、 <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A>、 <xref:System.Windows.Forms.ComboBox.ObjectCollection.Insert%2A>、<xref:System.Windows.Forms.ComboBox.ObjectCollection.Clear%2A>または<xref:System.Windows.Forms.ComboBox.ObjectCollection.Remove%2A>メソッド。 使用して、リストに項目を追加することができます、<xref:System.Windows.Forms.ComboBox.Items%2A>デザイナーのプロパティ。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.ComboBox>
- [ListBox コントロールの概要](listbox-control-overview-windows-forms.md)
- [ListBox の代わりに Windows フォーム ComboBox を使用する場合](when-to-use-a-windows-forms-combobox-instead-of-a-listbox.md)
- [方法: 追加および削除項目、Windows からフォーム ComboBox、ListBox、または CheckedListBox コントロール](add-and-remove-items-from-a-wf-combobox.md)
- [方法: Windows の内容を並べ替えるフォーム ComboBox、ListBox、または CheckedListBox コントロール](sort-the-contents-of-a-wf-combobox-listbox-or-checkedlistbox-control.md)
- [方法: 特定のアクセス フォーム ComboBox、ListBox、または CheckedListBox コントロールの項目を Windows](access-specific-items-in-a-wf-combobox-listbox-or-checkedlistbox.md)
- [方法: Windows フォームの ComboBox または ListBox コントロールをデータにバインドします。](how-to-bind-a-windows-forms-combobox-or-listbox-control-to-data.md)
- [オプションのリストを表示するための Windows フォーム コントロール](windows-forms-controls-used-to-list-options.md)
- [方法: Windows フォーム ComboBox、ListBox、または CheckedListBox コントロールのルックアップ テーブルを作成します。](create-a-lookup-table-for-a-wf-combobox-listbox.md)
