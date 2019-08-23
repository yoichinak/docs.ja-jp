---
title: Windows フォーム DataGridView コントロールの選択モード
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: dfe26e4749e6bff2d0ccdff47c6ea0b301880772
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960467"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールの選択モード
場合によっては、アプリケーションで、 <xref:System.Windows.Forms.DataGridView>コントロール内のユーザーの選択に基づいてアクションを実行する必要があります。 アクションによっては、可能な選択の種類を制限することができます。 たとえば、現在選択されているレコードのレポートをアプリケーションで印刷できるとします。 この場合は、行内の任意の場所<xref:System.Windows.Forms.DataGridView>をクリックすると常に行全体が選択されるようにコントロールを構成し、一度に1行しか選択できないようにすることができます。  
  
 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>プロパティを次<xref:System.Windows.Forms.DataGridViewSelectionMode>の列挙値のいずれかに設定することによって、許可される選択を指定できます。  
  
|DataGridViewSelectionMode 値|説明|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|セルをクリックすると、そのセルが選択されます。 行と列のヘッダーを選択に使用することはできません。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|セルをクリックすると、そのセルが選択されます。 列ヘッダーをクリックすると、列全体が選択されます。 列ヘッダーを並べ替えに使用することはできません。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|セルまたは列ヘッダーをクリックすると、列全体が選択されます。 列ヘッダーを並べ替えに使用することはできません。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|セルまたは行ヘッダーをクリックすると、行全体が選択されます。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|既定の選択モード。 セルをクリックすると、そのセルが選択されます。 行ヘッダーをクリックすると、行全体が選択されます。|  
  
> [!NOTE]
> 実行時に選択モードを変更すると、現在の選択範囲が自動的にクリアされます。  
  
 既定では、複数の行、列、またはセルを選択してマウスでドラッグしたり、CTRL キーまたは SHIFT キーを押しながら選択範囲を拡張または変更したり、左上のヘッダーセルをクリックしてコントロール内のすべてのセルを選択したりすることができます。 この動作を回避するには<xref:System.Windows.Forms.DataGridView.MultiSelect%2A> 、プロパティ`false`をに設定します。  
  
 モード<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> と<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>モードでは、ユーザーが行を選択して del キーを押すことにより、行を削除できます。 ユーザーが行を削除できるのは、現在のセルが編集モード<xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A>ではなく、プロパティがに`true`設定されていて、基になるデータソースがユーザーによる行の削除をサポートしている場合のみです。 これらの設定では、プログラムによる行の削除が妨げられないことに注意してください。  
  
## <a name="programmatic-selection"></a>プログラムによる選択  
 現在の選択モードでは、ユーザーが選択するだけでなく、プログラムによる選択の動作が制限されます。 コントロールに存在するセル、行、または`Selected`列のプロパティを設定することにより、現在の選択項目をプログラムで変更できます。 <xref:System.Windows.Forms.DataGridView> 選択モードに応じて、 <xref:System.Windows.Forms.DataGridView.SelectAll%2A>メソッドを使用してコントロール内のすべてのセルを選択することもできます。 選択範囲をクリアするには<xref:System.Windows.Forms.DataGridView.ClearSelection%2A> 、メソッドを使用します。  
  
 プロパティがに`true`設定されている場合は<xref:System.Windows.Forms.DataGridView> 、要素の`Selected`プロパティを変更することによって、要素を追加したり、選択から削除したりできます。 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> それ以外の場合`Selected` 、1 `true`つの要素に対してプロパティをに設定すると、その他の要素が自動的に選択から削除されます。  
  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A>プロパティの値を変更しても、現在の選択内容は変更されないことに注意してください。  
  
 現在選択されているセル、行、または列のコレクションを取得<xref:System.Windows.Forms.DataGridView.SelectedCells%2A>する<xref:System.Windows.Forms.DataGridView.SelectedRows%2A>には<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> 、 <xref:System.Windows.Forms.DataGridView>コントロールの、、の各プロパティを使用します。 コントロールのすべてのセルが選択されている場合、これらのプロパティへのアクセスは非効率的です。 この場合、パフォーマンスが低下しないようにする<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>には、最初にメソッドを使用します。 また、選択したセル、行、または列の数を決定するために、これらのコレクションにアクセスするのは効率的ではありません。 代わりに、、 <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>、または<xref:System.Windows.Forms.DataGridView.GetCellCount%2A>のいずれか<xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A>のメソッドを使用し<xref:System.Windows.Forms.DataGridViewElementStates.Selected>て、値を渡す必要があります。  
  
> [!TIP]
>  選択したセルのプログラムによる使用方法を示すコード例に<xref:System.Windows.Forms.DataGridView>ついては、「クラスの概要」を参照してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Windows フォーム DataGridView コントロールでの選択およびクリップボードの使用](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム DataGridView コントロールの選択モードを設定する](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
