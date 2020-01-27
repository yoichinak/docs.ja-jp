---
title: DataGridView コントロールの新しいレコードに対して行を使用する
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], adding rows for new records
- rows [Windows Forms], new records
- DataGridView control [Windows Forms], data entry
ms.assetid: 6110f1ea-9794-442c-a98a-f104a1feeaf4
ms.openlocfilehash: 2fcd35f8c4d04909cdbc26f6a4293fdd570385b8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728340"
---
# <a name="using-the-row-for-new-records-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールにおける新規レコード行の使用
アプリケーションのデータを編集するために <xref:System.Windows.Forms.DataGridView> を使用する場合、多くの場合、ユーザーがデータストアに新しいデータ行を追加できるようにする必要があります。 <xref:System.Windows.Forms.DataGridView> コントロールは、常に最後の行として表示される新しいレコードの行を提供することによって、この機能をサポートします。 行ヘッダーにアスタリスク (*) 記号が付いています。 次のセクションでは、新しいレコードを有効にする行をプログラミングするときに考慮する必要がある事項について説明します。  
  
## <a name="displaying-the-row-for-new-records"></a>新しいレコードの行を表示する  
 新しいレコードの行を表示するかどうかを指定するには、<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> プロパティを使用します。 このプロパティの既定値は `true` です。  
  
 データバインドケースでは、コントロールの <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> プロパティとデータソースの <xref:System.ComponentModel.IBindingList.AllowNew%2A?displayProperty=nameWithType> プロパティの両方が `true`場合、新しいレコードの行が表示されます。 どちらかが `false` の場合、行は表示されません。  
  
## <a name="populating-the-row-for-new-records-with-default-data"></a>既定のデータを使用して新しいレコードの行を設定する  
 ユーザーが新しいレコードの行を現在の行として選択すると、<xref:System.Windows.Forms.DataGridView> コントロールによって <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> イベントが発生します。  
  
 このイベントは、新しい <xref:System.Windows.Forms.DataGridViewRow> へのアクセスを提供し、新しい行に既定のデータを設定できるようにします。 詳細については、「[方法: Windows フォーム DataGridView コントロールで新しい行の既定値を指定する](specify-default-values-for-new-rows-in-the-datagrid.md)」を参照してください。  
  
## <a name="the-rows-collection"></a>Rows コレクション  
 新しいレコードの行は <xref:System.Windows.Forms.DataGridView> コントロールの <xref:System.Windows.Forms.DataGridView.Rows%2A> コレクションに含まれていますが、次の2つの点で動作が異なります。  
  
- 新しいレコードの行は、プログラムで <xref:System.Windows.Forms.DataGridView.Rows%2A> コレクションから削除することはできません。 このような場合は、<xref:System.InvalidOperationException> がスローされます。 ユーザーは、新しいレコードの行を削除することもできません。 <xref:System.Windows.Forms.DataGridViewRowCollection.Clear%2A?displayProperty=nameWithType> メソッドでは、この行が <xref:System.Windows.Forms.DataGridView.Rows%2A> コレクションから削除されることはありません。  
  
- 新しいレコードの行の後に行を追加することはできません。 An <xref:System.InvalidOperationException> is raised if this is attempted. その結果、新しいレコードの行は常に <xref:System.Windows.Forms.DataGridView> コントロールの最後の行になります。 行を追加する <xref:System.Windows.Forms.DataGridViewRowCollection> のメソッド (<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>、<xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>、および <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>) は、新しいレコードの行が存在する場合に、すべての挿入メソッドを内部的に呼び出します。  
  
## <a name="visual-customization-of-the-row-for-new-records"></a>新しいレコードの行のビジュアルカスタマイズ  
 新しいレコードの行が作成されると、その行は <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> プロパティによって指定された行に基づいて作成されます。 この行に対して指定されていないセルスタイルは、他のプロパティから継承されます。 For more information about cell style inheritance, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 The initial values displayed by cells in the row for new records are retrieved from each cell's <xref:System.Windows.Forms.DataGridViewCell.DefaultNewRowValue%2A> property. For cells of type <xref:System.Windows.Forms.DataGridViewImageCell>, this property returns a placeholder image. Otherwise, this property returns `null`. You can override this property to return a custom value. However, these initial values can be replaced by a <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event handler when focus enters the row for new records.  
  
 The standard icons for this row's header, which are an arrow or an asterisk, are not exposed publicly. If you want to customize the icons, you will need to create a custom <xref:System.Windows.Forms.DataGridViewRowHeaderCell> class.  
  
 The standard icons use the <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> property of the <xref:System.Windows.Forms.DataGridViewCellStyle> in use by the row header cell. The standard icons are not rendered if there is not enough space to display them completely.  
  
 If the row header cell has a string value set, and if there is not enough room for both the text and icon, the icon is dropped first.  
  
## <a name="sorting"></a>並べ替え  
 In unbound mode, new records will always be added to the end of the <xref:System.Windows.Forms.DataGridView> even if the user has sorted the content of the <xref:System.Windows.Forms.DataGridView>. The user will need to apply the sort again in order to sort the row to the correct position; this behavior is similar to that of the <xref:System.Windows.Forms.ListView> control.  
  
 In data bound and virtual modes, the insertion behavior when a sort is applied will be dependent on the implementation of the data model. For ADO.NET, the row is immediately sorted into the correct position.  
  
## <a name="other-notes-on-the-row-for-new-records"></a>Other Notes on the Row for New Records  
 You cannot set the <xref:System.Windows.Forms.DataGridViewRow.Visible%2A> property of this row to `false`. An <xref:System.InvalidOperationException> is raised if this is attempted.  
  
 The row for new records is always created in the unselected state.  
  
## <a name="virtual-mode"></a>Virtual Mode  
 If you are implementing virtual mode, you will need to track when a row for new records is needed in the data model and when to roll back the addition of the row. The exact implementation of this functionality depends on the implementation of the data model and its transaction semantics, for example, whether commit scope is at the cell or row level. For more information, see [Virtual Mode in the Windows Forms DataGridView Control](virtual-mode-in-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [Windows フォーム DataGridView コントロールでのデータ入力](data-entry-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム DataGridView コントロールの新しい行に既定値を指定する](specify-default-values-for-new-rows-in-the-datagrid.md)
