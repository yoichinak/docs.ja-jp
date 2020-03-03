---
title: 組み込みのオーナー描画サポートを備えたコントロール
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [Windows Forms], owner
- drawing [Windows Forms], custom
- controls [Windows Forms], changing appearance
- custom drawing
- owner drawing
ms.assetid: 3823d01e-9610-43e6-864d-99f9b7c2b351
ms.openlocfilehash: f0d4b99f9ee0134fc7334a941dd5ef4fd7ba3df3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930190"
---
# <a name="controls-with-built-in-owner-drawing-support"></a>組み込みのオーナー描画サポートを備えたコントロール
Windows フォームのオーナー描画 (カスタム描画とも呼ばれます) は、特定のコントロールの外観を変更するための手法です。  
  
> [!NOTE]
> このトピックの "コントロール" という語は、 <xref:System.Windows.Forms.Control>または<xref:System.ComponentModel.Component>から派生したクラスを意味するために使用されます。  
  
 通常、コントロールの外観を決定するためになど<xref:System.Windows.Forms.Control.BackColor%2A>のプロパティ設定を使用して、ウィンドウの描画を自動的に処理します。 オーナー描画では、描画プロセスを引き継いで、プロパティでは設定できない外観の要素を変更できます。 たとえば、多くのコントロールでは表示されるテキストの色を設定できますが、1 つの色に制限されます。 オーナー描画では、テキストの一部分を黒で表示し、別の部分を赤で表示する、といったことができます。  
  
 実際には、オーナー描画はフォームでのグラフィックスの描画に似ています。 たとえば、フォームの<xref:System.Windows.Forms.Control.Paint>イベントのハンドラーでグラフィックスメソッドを使用して`ListBox`コントロールをエミュレートすることができますが、すべてのユーザー操作を処理する独自のコードを記述する必要があります。 オーナー描画では、コントロールは独自のコードを使って内容を描画しますが、それ以外については組み込み機能がすべて保持されます。 グラフィックス メソッドを使うと、コントロール内の各項目を描画したり、各項目の一部だけカスタマイズして他の部分は既定の外観を使ったりすることができます。  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Windows フォーム コントロールでのオーナー描画  
 オーナー描画をサポートしているコントロールでオーナー描画を実行するには、通常、1 つのプロパティを設定し、1 つまたは複数のイベントを処理します。  
  
 オーナー描画をサポートしているほとんどのコントロールには、コントロールの描画時に描画関連のイベントが発生するかどうかを示す `OwnerDraw` または `DrawMode` プロパティがあります。  
  
 `OwnerDraw` または `DrawMode` プロパティを持たないコントロールには、自動的に発生する描画イベントを提供する `DataGridView` コントロールと、独自の描画関連イベントを持つ外部レンダリング クラスを使って描画される `ToolStrip` コントロールが含まれます。  
  
 さまざまな種類の描画イベントがありますが、標準的な描画イベントはコントロール内の 1 つの項目を描画するために発生します。 イベント ハンドラーは、描画される項目に関する情報と、その描画に使用できるツールを含む、`EventArgs` オブジェクトを受け取ります。 たとえば、このオブジェクトには通常、親コレクション内の項目のインデックス番号、項目<xref:System.Drawing.Rectangle>の表示境界を示す、 <xref:System.Drawing.Graphics>および描画メソッドを呼び出すためのオブジェクトが含まれます。 一部のイベントの `EventArgs` オブジェクトでは、項目に関する追加情報と、背景やフォーカス四角形などの項目の一部分を既定で描画するために呼び出すことができるメソッドが提供されます。  
  
 オーナー描画のカスタマイズを含む再利用可能なコントロールを作成するには、オーナー描画をサポートするコントロール クラスから派生する新しいクラスを作成します。 描画イベントを処理するのではなく、新しいクラスの適切な `On`<*イベント名*> メソッドのオーバーライドにオーナー描画のコードを組み込みます。 この場合、コントロールのユーザーがオーナー描画イベントを処理して追加のカスタマイズを提供できるように、基底クラスの `On`<*イベント名*> メソッドを呼び出す必要があります。  
  
 次の Windows フォーム コントロールは、すべてのバージョンの .NET Framework でオーナー描画をサポートします。  
  
- <xref:System.Windows.Forms.ListBox>  
  
- <xref:System.Windows.Forms.ComboBox>  
  
- <xref:System.Windows.Forms.MenuItem>(および<xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu>で使用)  
  
- <xref:System.Windows.Forms.TabControl>  
  
 次のコントロールは、.NET Framework 2.0 でのみ所有者の描画をサポートします。  
  
- <xref:System.Windows.Forms.ToolTip>  
  
- <xref:System.Windows.Forms.ListView>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 次のコントロールはオーナー描画をサポートしており、.NET Framework 2.0 で新しく追加されています。  
  
- <xref:System.Windows.Forms.DataGridView>  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
 以下のセクションでは、これらの各コントロールについてさらに詳しく説明します。  
  
### <a name="listbox-and-combobox-controls"></a>ListBox コントロールと ComboBox コントロール  
 コントロールとコントロールを使用すると<xref:System.Windows.Forms.ComboBox> 、コントロール内の個々の項目を1つのサイズで、またはさまざまなサイズで描画できます。 <xref:System.Windows.Forms.ListBox>  
  
> [!NOTE]
> コントロールはコントロール<xref:System.Windows.Forms.ListBox>から派生しますが、オーナー描画をサポートしていません。 <xref:System.Windows.Forms.CheckedListBox>  
  
 各項目を同じサイズで描画するには`DrawMode` 、プロパティ<xref:System.Windows.Forms.DrawMode.OwnerDrawFixed>をに設定`DrawItem`し、イベントを処理します。  
  
 異なるサイズを使用して各項目を描画する`DrawMode`には<xref:System.Windows.Forms.DrawMode.OwnerDrawVariable> 、プロパティをに`MeasureItem`設定`DrawItem`し、イベントとイベントの両方を処理します。 `MeasureItem` イベントを使うと、項目の `DrawItem` イベントが発生する前に、その項目のサイズを指定できます。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
- [方法: ComboBox コントロールでの可変サイズのテキストの作成](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>MenuItem コンポーネント  
 コンポーネントは、コンポーネント<xref:System.Windows.Forms.MainMenu>または<xref:System.Windows.Forms.ContextMenu>コンポーネントの1つのメニュー項目を表します。 <xref:System.Windows.Forms.MenuItem>  
  
 を描画<xref:System.Windows.Forms.MenuItem>するには、 `OwnerDraw`その`DrawItem`プロパティ`true`をに設定し、イベントを処理します。 `DrawItem` イベントが発生する前にメニュー項目のサイズをカスタマイズするには、項目の`MeasureItem` イベントを処理します。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl コントロール  
 <xref:System.Windows.Forms.TabControl>コントロールを使用すると、コントロールに個々のタブを描画できます。 オーナー描画は、タブのみに影響します。<xref:System.Windows.Forms.TabPage>コンテンツは影響を受けません。  
  
 で<xref:System.Windows.Forms.TabControl>各タブを描画するには、 `DrawMode` `DrawItem`プロパティを<xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>に設定し、イベントを処理します。 このイベントは、コントロールにタブが表示されている場合にのみ、タブごとに 1 回発生します。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip コンポーネント  
 <xref:System.Windows.Forms.ToolTip>コンポーネントを使用すると、表示されるときにツールヒント全体を描画できます。  
  
 を描画<xref:System.Windows.Forms.ToolTip>するには、 `OwnerDraw`その`Draw`プロパティ`true`をに設定し、イベントを処理します。 イベント<xref:System.Windows.Forms.ToolTip>が発生`Draw`する前にのサイズをカスタマイズするには`Popup` 、イベントを処理<xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A>し、イベントハンドラーのプロパティを設定します。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>ListView コントロール  
 <xref:System.Windows.Forms.ListView>コントロールを使用すると、コントロールに個々の項目、サブ項目、および列ヘッダーを描画できます。  
  
 コントロールのオーナー描画を有効にするには、`OwnerDraw` プロパティを `true` に設定します。  
  
 コントロール内の各項目を描画するには、`DrawItem` イベントを処理します。  
  
 <xref:System.Windows.Forms.ListView.View%2A>プロパティがに<xref:System.Windows.Forms.View.Details>設定されている場合に、コントロール内の各サブ項目または`DrawSubItem`列`DrawColumnHeader`ヘッダーを描画するには、イベントおよびイベントを処理します。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView コントロール  
 <xref:System.Windows.Forms.TreeView>コントロールを使用すると、コントロールに個々のノードを描画できます。  
  
 各ノードに表示されているテキストのみを描画`DrawMode`するに<xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText>は、プロパティ`DrawNode`をに設定し、イベントを処理してテキストを描画します。  
  
 各ノードのすべての要素を描画するに`DrawMode`は、 <xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll>プロパティをに`DrawNode`設定し、イベントを処理して必要な要素を描画します。たとえば、テキスト、アイコン、チェックボックス、プラス記号とマイナス記号、ノードを接続する線などです。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView コントロール  
 <xref:System.Windows.Forms.DataGridView>コントロールを使用すると、コントロールに個々のセルと行を描画できます。  
  
 個別のセルを描画するには、`CellPainting` イベントを処理します。  
  
 個別の行または行の要素を描画するには、`RowPrePaint` イベントと `RowPostPaint` イベントの一方または両方を処理します。 `RowPrePaint` イベントは行内のセルが描画される前に発生し、`RowPostPaint` イベントはセルが描画された後で発生します。 両方のイベントと `CellPainting` イベントを処理して、行の背景、個々のセル、行の前景を個別に描画できます。または、必要な部分については個別にカスタマイズを提供し、行の他の要素には既定の表示を使うこともできます。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
- <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
- <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
- [方法: Windows フォーム DataGridView コントロールでのセルの外観のカスタマイズ](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
- [方法: Windows フォーム DataGridView コントロールでの行の外観のカスタマイズ](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip コントロール  
 <xref:System.Windows.Forms.ToolStrip>また、派生したコントロールを使用すると、外観の任意の側面をカスタマイズできます。  
  
 <xref:System.Windows.Forms.ToolStrip>コントロールのカスタム表示を提供するには`Renderer` 、 <xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.ToolStripManager>、 <xref:System.Windows.Forms.ToolStripPanel>、または<xref:System.Windows.Forms.ToolStripContentPanel>のプロパティを`ToolStripRenderer`オブジェクトに設定し、によって提供される多数の描画イベントの1つ以上を処理します。`ToolStripRenderer`クラス。 または、特定`Renderer` <xref:System.Windows.Forms.ToolStripProfessionalRenderer> <xref:System.Windows.Forms.ToolStripSystemRenderer> `ToolStripRenderer`の`On` *EventName*メソッドを実装またはオーバーライドする、、またはから派生した独自のクラスのインスタンスにプロパティを設定します。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.ToolStripRenderer>  
  
- [方法: Windows フォームで ToolStrip コントロールのカスタムレンダラーを作成して設定する](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
- [方法: ToolStrip コントロールのカスタム描画](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>関連項目

- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
