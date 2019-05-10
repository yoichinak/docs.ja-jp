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
ms.openlocfilehash: df3a61dae9ad926f56da4e9d15e0e8b8c6f1c8a3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648250"
---
# <a name="controls-with-built-in-owner-drawing-support"></a>組み込みのオーナー描画サポートを備えたコントロール
Windows フォームのオーナー描画 (カスタム描画とも呼ばれます) は、特定のコントロールの外観を変更するための手法です。  
  
> [!NOTE]
>  このトピックでは、"control"という単語がいずれかから派生するクラスを意味する使用<xref:System.Windows.Forms.Control>または<xref:System.ComponentModel.Component>します。  
  
 通常、Windows の描画を自動的に処理などのプロパティの設定を使用して<xref:System.Windows.Forms.Control.BackColor%2A>コントロールの外観を決定します。 オーナー描画では、描画プロセスを引き継いで、プロパティでは設定できない外観の要素を変更できます。 たとえば、多くのコントロールでは表示されるテキストの色を設定できますが、1 つの色に制限されます。 オーナー描画では、テキストの一部分を黒で表示し、別の部分を赤で表示する、といったことができます。  
  
 実際には、オーナー描画はフォームでのグラフィックスの描画に似ています。 フォームの例では、ハンドラーでグラフィックス メソッドを使用する可能性があります<xref:System.Windows.Forms.Control.Paint>をエミュレートするイベントを`ListBox`コントロールが、すべてのユーザー操作を処理するコードを記述します。 オーナー描画では、コントロールは独自のコードを使って内容を描画しますが、それ以外については組み込み機能がすべて保持されます。 グラフィックス メソッドを使うと、コントロール内の各項目を描画したり、各項目の一部だけカスタマイズして他の部分は既定の外観を使ったりすることができます。  
  
## <a name="owner-drawing-in-windows-forms-controls"></a>Windows フォーム コントロールでのオーナー描画  
 オーナー描画をサポートしているコントロールでオーナー描画を実行するには、通常、1 つのプロパティを設定し、1 つまたは複数のイベントを処理します。  
  
 オーナー描画をサポートしているほとんどのコントロールには、コントロールの描画時に描画関連のイベントが発生するかどうかを示す `OwnerDraw` または `DrawMode` プロパティがあります。  
  
 `OwnerDraw` または `DrawMode` プロパティを持たないコントロールには、自動的に発生する描画イベントを提供する `DataGridView` コントロールと、独自の描画関連イベントを持つ外部レンダリング クラスを使って描画される `ToolStrip` コントロールが含まれます。  
  
 さまざまな種類の描画イベントがありますが、標準的な描画イベントはコントロール内の 1 つの項目を描画するために発生します。 イベント ハンドラーは、描画される項目に関する情報と、その描画に使用できるツールを含む、`EventArgs` オブジェクトを受け取ります。 このオブジェクトが通常、その親コレクション内の項目のインデックス番号を含むなど、<xref:System.Drawing.Rectangle>アイテムの表示の境界を示す、<xref:System.Drawing.Graphics>描画メソッドを呼び出すためのオブジェクト。 一部のイベントの `EventArgs` オブジェクトでは、項目に関する追加情報と、背景やフォーカス四角形などの項目の一部分を既定で描画するために呼び出すことができるメソッドが提供されます。  
  
 オーナー描画のカスタマイズを含む再利用可能なコントロールを作成するには、オーナー描画をサポートするコントロール クラスから派生する新しいクラスを作成します。 描画イベントを処理するのではなく、新しいクラスの適切な `On`<*イベント名*> メソッドのオーバーライドにオーナー描画のコードを組み込みます。 この場合、コントロールのユーザーがオーナー描画イベントを処理して追加のカスタマイズを提供できるように、基底クラスの `On`<*イベント名*> メソッドを呼び出す必要があります。  
  
 次の Windows フォーム コントロールは、すべてのバージョンの .NET Framework でオーナー描画をサポートします。  
  
- <xref:System.Windows.Forms.ListBox>  
  
- <xref:System.Windows.Forms.ComboBox>  
  
- <xref:System.Windows.Forms.MenuItem> (で使用される<xref:System.Windows.Forms.MainMenu>と<xref:System.Windows.Forms.ContextMenu>)  
  
- <xref:System.Windows.Forms.TabControl>  
  
 次のコントロールは、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] でのみオーナー描画をサポートします。  
  
- <xref:System.Windows.Forms.ToolTip>  
  
- <xref:System.Windows.Forms.ListView>  
  
- <xref:System.Windows.Forms.TreeView>  
  
 次のコントロールはオーナー描画をサポートし、[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)] での新機能です。  
  
- <xref:System.Windows.Forms.DataGridView>  
  
- <xref:System.Windows.Forms.ToolStrip>  
  
 以下のセクションでは、これらの各コントロールについてさらに詳しく説明します。  
  
### <a name="listbox-and-combobox-controls"></a>ListBox コントロールと ComboBox コントロール  
 <xref:System.Windows.Forms.ListBox>と<xref:System.Windows.Forms.ComboBox>コントロールを使用すると、さまざまなサイズでまたは 1 つのサイズですべてのコントロールの個々 の項目を描画します。  
  
> [!NOTE]
>  ですが、<xref:System.Windows.Forms.CheckedListBox>から派生したコントロールは、<xref:System.Windows.Forms.ListBox>コントロール、それがオーナー描画をサポートします。  
  
 各項目は同じサイズで描画するには、設定、`DrawMode`プロパティを<xref:System.Windows.Forms.DrawMode.OwnerDrawFixed>を処理し、`DrawItem`イベント。  
  
 さまざまなサイズを使用して各項目を描画する設定、`DrawMode`プロパティを<xref:System.Windows.Forms.DrawMode.OwnerDrawVariable>両方を処理し、`MeasureItem`と`DrawItem`イベント。 `MeasureItem` イベントを使うと、項目の `DrawItem` イベントが発生する前に、その項目のサイズを指定できます。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.ListBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListBox.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.MeasureItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ComboBox.DrawItem?displayProperty=nameWithType>  
  
- [方法: コンボ ボックス コントロールにサイズ設定されたテキストを作成します。](how-to-create-variable-sized-text-in-a-combobox-control.md)  
  
### <a name="menuitem-component"></a>MenuItem コンポーネント  
 <xref:System.Windows.Forms.MenuItem>コンポーネント内の 1 つのメニュー項目を表す、<xref:System.Windows.Forms.MainMenu>または<xref:System.Windows.Forms.ContextMenu>コンポーネント。  
  
 描画するために、<xref:System.Windows.Forms.MenuItem>に設定して、その`OwnerDraw`プロパティを`true`処理とその`DrawItem`イベント。 `DrawItem` イベントが発生する前にメニュー項目のサイズをカスタマイズするには、項目の`MeasureItem` イベントを処理します。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.MenuItem.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.MenuItem.MeasureItem?displayProperty=nameWithType>  
  
### <a name="tabcontrol-control"></a>TabControl コントロール  
 <xref:System.Windows.Forms.TabControl>コントロールでは、コントロール内の個々 のタブを描画することができます。 オーナー描画タブのみに影響を与えます<xref:System.Windows.Forms.TabPage>内容には影響しません。  
  
 各タブを描画するために、 <xref:System.Windows.Forms.TabControl>、設定、`DrawMode`プロパティを<xref:System.Windows.Forms.TabDrawMode.OwnerDrawFixed>を処理し、`DrawItem`イベント。 このイベントは、コントロールにタブが表示されている場合にのみ、タブごとに 1 回発生します。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.TabControl.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TabControl.DrawItem?displayProperty=nameWithType>  
  
### <a name="tooltip-component"></a>ToolTip コンポーネント  
 <xref:System.Windows.Forms.ToolTip>コンポーネントでは、表示される場合は、ToolTip 全体を描画することができます。  
  
 描画するために、<xref:System.Windows.Forms.ToolTip>に設定して、その`OwnerDraw`プロパティを`true`処理とその`Draw`イベント。 サイズをカスタマイズする、<xref:System.Windows.Forms.ToolTip>する前に、`Draw`処理イベントが発生する、`Popup`イベントとセット、<xref:System.Windows.Forms.PopupEventArgs.ToolTipSize%2A>イベント ハンドラーのプロパティ。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.ToolTip.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Draw?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ToolTip.Popup?displayProperty=nameWithType>  
  
### <a name="listview-control"></a>ListView コントロール  
 <xref:System.Windows.Forms.ListView>コントロールでは、コントロール内の個々 の項目、サブ項目、および列ヘッダーを描画することができます。  
  
 コントロールのオーナー描画を有効にするには、`OwnerDraw` プロパティを `true` に設定します。  
  
 コントロール内の各項目を描画するには、`DrawItem` イベントを処理します。  
  
 コントロール内の各サブ項目または列ヘッダーを描画するときに、<xref:System.Windows.Forms.ListView.View%2A>プロパティに設定されて<xref:System.Windows.Forms.View.Details>、処理、`DrawSubItem`と`DrawColumnHeader`イベント。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.ListView.OwnerDraw%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawSubItem?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.ListView.DrawColumnHeader?displayProperty=nameWithType>  
  
### <a name="treeview-control"></a>TreeView コントロール  
 <xref:System.Windows.Forms.TreeView>コントロールでは、コントロール内の個々 のノードを描画することができます。  
  
 各ノードに表示されるテキストのみを描画する設定、`DrawMode`プロパティを<xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawText>を処理し、`DrawNode`テキストを描画するイベント。  
  
 各ノードのすべての要素を描画する設定、`DrawMode`プロパティを<xref:System.Windows.Forms.TreeViewDrawMode.OwnerDrawAll>を処理し、`DrawNode`など、テキスト、アイコン、チェック ボックス、プラスとマイナス記号、およびノードを接続する線に必要な要素を描画するイベントです。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.TreeView.DrawMode%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.TreeView.DrawNode?displayProperty=nameWithType>  
  
### <a name="datagridview-control"></a>DataGridView コントロール  
 <xref:System.Windows.Forms.DataGridView>コントロールでは、コントロール内の個々 のセルと行を描画することができます。  
  
 個別のセルを描画するには、`CellPainting` イベントを処理します。  
  
 個別の行または行の要素を描画するには、`RowPrePaint` イベントと `RowPostPaint` イベントの一方または両方を処理します。 `RowPrePaint` イベントは行内のセルが描画される前に発生し、`RowPostPaint` イベントはセルが描画された後で発生します。 両方のイベントと `CellPainting` イベントを処理して、行の背景、個々のセル、行の前景を個別に描画できます。または、必要な部分については個別にカスタマイズを提供し、行の他の要素には既定の表示を使うこともできます。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.DataGridView.CellPainting>  
  
- <xref:System.Windows.Forms.DataGridView.RowPrePaint>  
  
- <xref:System.Windows.Forms.DataGridView.RowPostPaint>  
  
- [方法: Windows フォームの DataGridView コントロール内のセルの外観をカスタマイズします。](customize-the-appearance-of-cells-in-the-datagrid.md)  
  
- [方法: Windows フォームの DataGridView コントロール内の行の外観をカスタマイズします。](customize-the-appearance-of-rows-in-the-datagrid.md)  
  
### <a name="toolstrip-control"></a>ToolStrip コントロール  
 <xref:System.Windows.Forms.ToolStrip> および派生コントロールでは、のどの側面の外観をカスタマイズできます。  
  
 カスタム レンダリングを提供する<xref:System.Windows.Forms.ToolStrip>コントロール、設定、`Renderer`のプロパティを<xref:System.Windows.Forms.ToolStrip>、 <xref:System.Windows.Forms.ToolStripManager>、 <xref:System.Windows.Forms.ToolStripPanel>、または<xref:System.Windows.Forms.ToolStripContentPanel>を`ToolStripRenderer`オブジェクトし、1 つ以上のによって提供される多くの描画イベントの処理、`ToolStripRenderer`クラス。 また、設定、`Renderer`から派生した独自のクラスのインスタンスにプロパティ`ToolStripRenderer`、 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>、または<xref:System.Windows.Forms.ToolStripSystemRenderer>を実装またはオーバーライド特定`On` *EventName*メソッド。  
  
 サンプル コードなど詳細については、次のトピックをご覧ください。  
  
- <xref:System.Windows.Forms.ToolStripRenderer>  
  
- [方法: 作成し、Windows フォームで ToolStrip コントロールのカスタム レンダラーを設定](create-and-set-a-custom-renderer-for-the-toolstrip-control-in-wf.md)  
  
- [方法: ToolStrip コントロールをカスタム描画します。](how-to-custom-draw-a-toolstrip-control.md)  
  
## <a name="see-also"></a>関連項目

- [Windows フォームで使用するコントロール](controls-to-use-on-windows-forms.md)
