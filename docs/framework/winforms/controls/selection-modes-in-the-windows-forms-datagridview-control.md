---
title: Windows フォーム DataGridView コントロールの選択モード
ms.date: 03/30/2017
helpviewer_keywords:
- selection [Windows Forms], modes in DataGridView control
- DataGridView control [Windows Forms], selection mode
ms.assetid: a3ebfd3d-0525-479d-9d96-d9e017289b36
ms.openlocfilehash: 79e13e65938252015e43b59a962d40f20963a5df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097279"
---
# <a name="selection-modes-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールの選択モード
アプリケーション内のユーザー選択に基づいてアクションを実行したい場合があります、<xref:System.Windows.Forms.DataGridView>コントロール。 によって、アクション可能な選択の種類を制限します。 たとえば、アプリケーションは、現在選択されているレコードのレポートを印刷できます。 ここでは、構成にする可能性があります、<xref:System.Windows.Forms.DataGridView>コントロールに常に、行内でクリックしてできるようには、全体の行を選択し、一度に 1 つだけその行を選択できるようにします。  
  
 設定で許可されている選択内容を指定することができます、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>プロパティを次のいずれか<xref:System.Windows.Forms.DataGridViewSelectionMode>列挙値。  
  
|DataGridViewSelectionMode 値|説明|  
|-------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>|セルをクリックするを選択します。 選択範囲の行および列ヘッダーを使用できません。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>|セルをクリックするを選択します。 列見出しをクリックすると、全体の列が選択されます。 列ヘッダーは、並べ替えに使用できません。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>|セルまたは列ヘッダーをクリックすると、列全体を選択します。 列ヘッダーは、並べ替えに使用できません。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>|セルまたは行ヘッダーをクリックすると、行全体を選択します。|  
|<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>|既定の選択モード。 セルをクリックするを選択します。 行ヘッダーをクリックすると、全体の行が選択されます。|  
  
> [!NOTE]
>  実行時に自動的に選択モードを変更すると、現在の選択が解除されます。  
  
 既定では、ユーザー選択できます複数の行、列、またはセル、マウスをドラッグして ctrl キーまたは shift キーを押しながらを拡張または変更、選択範囲を選択するか、コントロール内のすべてのセルの選択を左上のヘッダー セルをクリックします。 この動作を防ぐためには、設定、<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>プロパティを`false`します。  
  
 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>と<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>モードを選択し、DEL キーを押して行を削除するユーザーを許可します。 現在のセルが編集モードでない場合にのみ、ユーザーが行を削除できる、<xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A>プロパティに設定されて`true`、基になるデータ ソースは、ユーザーによる行の削除をサポートしています。 これらの設定では、プログラムによる行の削除されないことに注意してください。  
  
## <a name="programmatic-selection"></a>プログラムの選択  
 現在の選択モードでは、プログラムの選択とユーザーの選択の動作を制限します。 設定してプログラムで現在の選択範囲を変更することができます、`Selected`任意のセル、行、または表示されている列のプロパティ、<xref:System.Windows.Forms.DataGridView>コントロール。 使用してコントロールのすべてのセルを選択することも、<xref:System.Windows.Forms.DataGridView.SelectAll%2A>選択モードに応じてのメソッド。 選択範囲をクリアするには、使用、<xref:System.Windows.Forms.DataGridView.ClearSelection%2A>メソッド。  
  
 場合、<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>プロパティに設定されて`true`、追加することができます<xref:System.Windows.Forms.DataGridView>要素をまたは変更することで、選択範囲から削除、`Selected`要素のプロパティ。 それ以外の場合、設定、`Selected`プロパティを`true`の 1 つの要素は、選択範囲からの他の要素を自動的に削除されます。  
  
 値を変更することに注意してください、<xref:System.Windows.Forms.DataGridView.CurrentCell%2A>プロパティが現在の選択範囲を変更しません。  
  
 現在選択されているセル、行、または列のコレクションを取得することができます、 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>、 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>、および<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>のプロパティ、<xref:System.Windows.Forms.DataGridView>コントロール。 コントロール内のすべてのセルが選択されている場合は、これらのプロパティにアクセスする効率的です。 この場合、パフォーマンスの低下を避けるため、使用、<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>メソッド最初。 さらに、選択されたセルの数を決定するこれらのコレクションにアクセスする行、または列はできない効率的です。 代わりに、使用する必要があります、 <xref:System.Windows.Forms.DataGridView.GetCellCount%2A>、 <xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A>、または<xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A>に渡して、メソッド、<xref:System.Windows.Forms.DataGridViewElementStates.Selected>値。  
  
> [!TIP]
>  選択されたセルのプログラムによる使用方法を示すコード例が記載されて、<xref:System.Windows.Forms.DataGridView>クラスの概要。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridViewSelectionMode>
- [Windows フォーム DataGridView コントロールでの選択およびクリップボードの使用](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム DataGridView コントロールの選択モードを設定します。](how-to-set-the-selection-mode-of-the-windows-forms-datagridview-control.md)
