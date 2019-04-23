---
title: Windows フォーム DataGridView コントロールを拡張するための推奨される手順
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sharing
- data grids [Windows Forms], best practices
- DataGridView control [Windows Forms], shared rows
- DataGridView control [Windows Forms], best practices
- best practices [Windows Forms], dataGridView control
- DataGridView control [Windows Forms], scaling
ms.assetid: 8321a8a6-6340-4fd1-b475-fa090b905aaf
ms.openlocfilehash: 76ac31e9082216d0024160c51a7495855eee5601
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142144"
---
# <a name="best-practices-for-scaling-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールを拡張するための推奨される手順
<xref:System.Windows.Forms.DataGridView>最大限のスケーラビリティを提供するコントロールは設計されています。 大量のデータを表示する場合は、大量のメモリを消費したり、ユーザー インターフェイス (UI) の応答性を低下させることを回避するには、このトピックで説明されているガイドラインに従ってください。 このトピックでは、次の問題について説明します。  
  
-   セルのスタイルを効率的に使用します。  
  
-   ショートカット メニューを効率的に使用します。  
  
-   自動サイズ変更の効率的に使用します。  
  
-   選択したセル、行、および列のコレクションの効率的な使用  
  
-   行の共有を使用します。  
  
-   行が非共有になることを防ぐ  
  
 特別なパフォーマンスのニーズがあれば、仮想モードを実装し、独自のデータ管理操作を提供できます。 詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールでのデータ表示モード](data-display-modes-in-the-windows-forms-datagridview-control.md)します。  
  
## <a name="using-cell-styles-efficiently"></a>セルのスタイルを効率的に使用します。  
 各セル、行、および列には、独自のスタイル情報を持つことができます。 スタイル情報が格納されている<xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクト。 多くの個々 のセルのスタイル オブジェクトを作成する<xref:System.Windows.Forms.DataGridView>大量のデータを使用する場合に特にに要素が、効率的にすることができます。 パフォーマンスに影響を回避するには、次のガイドラインを使用します。  
  
-   個々 のセル スタイル プロパティを設定しないでください<xref:System.Windows.Forms.DataGridViewCell>または<xref:System.Windows.Forms.DataGridViewRow>オブジェクト。 指定された行のオブジェクトが含まれます、<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>プロパティ。 新しい行のテンプレートから複製された各行は、テンプレートのセル スタイル オブジェクトのコピーを受け取ります。 スケーラビリティを最大にするでのセル スタイル プロパティを設定、<xref:System.Windows.Forms.DataGridView>レベル。 たとえば、設定、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>プロパティではなく、<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>プロパティ。  
  
-   一部のセルは、既定の書式設定よりもその他の書式設定を必要とする場合と同じ使用<xref:System.Windows.Forms.DataGridViewCellStyle>セル、行、または列のグループ間でのインスタンス。 型のプロパティを直接設定しないでください<xref:System.Windows.Forms.DataGridViewCellStyle>個々 のセル、行、および列にします。 セル スタイルの共有の例は、次を参照してください。[方法。Windows フォーム DataGridView コントロールの既定のセル スタイルを設定](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)します。 処理することによって個別のセルのスタイルを設定するときにも、パフォーマンス低下を避けることができます、<xref:System.Windows.Forms.DataGridView.CellFormatting>イベント ハンドラー。 例については、「[方法: Windows フォーム DataGridView コントロールでデータの書式設定をカスタマイズ](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)します。  
  
-   セルのスタイルを決定するときに使用して、<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>プロパティではなく、<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>プロパティ。 アクセス、<xref:System.Windows.Forms.DataGridViewCell.Style%2A>プロパティの新しいインスタンスを作成し、<xref:System.Windows.Forms.DataGridViewCellStyle>クラスのプロパティは既に使用されていない場合。 さらに、このオブジェクトの一部のスタイルは、行、列、またはコントロールから継承された場合、セルのスタイル情報を含まない場合があります。 セル スタイルの継承の詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールのセル スタイル](cell-styles-in-the-windows-forms-datagridview-control.md)します。  
  
## <a name="using-shortcut-menus-efficiently"></a>ショートカット メニューを効率的に使用します。  
 各セル、行、および列には、ショートカット メニューを持つことができます。 ショートカット メニューに、<xref:System.Windows.Forms.DataGridView>コントロールがによって表される<xref:System.Windows.Forms.ContextMenuStrip>コントロール。 セル スタイルのオブジェクトと同様に、多くの個々 のショートカット メニューを作成します。<xref:System.Windows.Forms.DataGridView>要素には、パフォーマンスが低下します。 この低下を回避するには、次のガイドラインを使用します。  
  
-   個々 のセルと行のショートカット メニューを作成しないでください。 これには、行のテンプレートでは、コントロールに新しい行が追加されたときに、ショートカット メニューと複製が含まれます。 スケーラビリティを最大にするには、コントロールの使用のみの<xref:System.Windows.Forms.Control.ContextMenuStrip%2A>コントロール全体の 1 つのショートカット メニューを指定するプロパティ。  
  
-   複数の行またはセルに複数のショートカット メニューが必要な場合は、処理、<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded>または<xref:System.Windows.Forms.DataGridView.RowContextMenuStripNeeded>イベント。 これらのイベントでは、ショートカット メニュー オブジェクトを管理できます。 自分でパフォーマンスを調整することができます。  
  
## <a name="using-automatic-resizing-efficiently"></a>自動サイズ変更の効率的に使用します。  
 行、列、およびヘッダーに自動的にサイズを変更できるセルの内容の変更としてセルの内容全体がクリッピングなしに表示されるようします。 サイズ変更モードを変更すると、行、列、およびヘッダーも変更できます。 適切なサイズを決定する、<xref:System.Windows.Forms.DataGridView>コントロールに対応する必要がありますの各セルの値を調べる必要があります。 大規模なデータ セットを使用する場合この分析はパフォーマンスに悪影響コントロールの自動サイズ変更が発生した場合。 パフォーマンスの低下を回避するには、次のガイドラインを使用します。  
  
-   自動サイズ設定を使用しないでください、<xref:System.Windows.Forms.DataGridView>大量の行セットを持つコントロール。 自動サイズ変更、表示されている行に基づくサイズ変更のみを使用場合します。 仮想モードも表示されている行のみを使用します。  
  
    -   行と列を使用して、`DisplayedCells`または`DisplayedCellsExceptHeaders`のフィールド、 <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>、 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>、および<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>列挙体。  
  
    -   行のヘッダーを使用して、<xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToDisplayedHeaders>または<xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode.AutoSizeToFirstHeader>のフィールド、<xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>列挙体。  
  
-   最大限のスケーラビリティ、自動サイズ調整をオフにし、プログラムによるサイズ変更を使用します。  
  
 詳細については、次を参照してください。 [Windows フォームの DataGridView コントロールのサイズ変更オプション](sizing-options-in-the-windows-forms-datagridview-control.md)します。  
  
## <a name="using-the-selected-cells-rows-and-columns-collections-efficiently"></a>選択したセル、行、および列のコレクションの効率的な使用  
 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>大規模な選択範囲をコレクションが効率的に実行されません。 <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>と<xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>コレクション解除することも、効率的なほどには一般的なセルよりも多くの少ない行があるため、<xref:System.Windows.Forms.DataGridView>制御、および行よりも多くの少ない列です。 パフォーマンスの低下を避けるためには、これらのコレクションを使用する場合は、次のガイドラインを使用します。  
  
-   確認するかどうかのすべてのセル、<xref:System.Windows.Forms.DataGridView>の内容にアクセスする前に、選択されている、 <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> 、コレクションの戻り値を確認、<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>メソッド。 ただし、このメソッドは、共有が解除する行で発生することができます。 詳細については、次のセクションを参照してください。  
  
-   使用しないでください、<xref:System.Collections.ICollection.Count%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewSelectedCellCollection?displayProperty=nameWithType>選択したセルの数を決定します。 代わりに、使用、<xref:System.Windows.Forms.DataGridView.GetCellCount%2A?displayProperty=nameWithType>メソッドを渡します、<xref:System.Windows.Forms.DataGridViewElementStates.Selected?displayProperty=nameWithType>値。 同様に、使用、<xref:System.Windows.Forms.DataGridViewRowCollection.GetRowCount%2A?displayProperty=nameWithType>と<xref:System.Windows.Forms.DataGridViewColumnCollection.GetColumnCount%2A?displayProperty=nameWithType>メソッドを選択した行と列コレクションにアクセスするのではなく、選択した要素の数を決定します。  
  
-   セル ベースの選択モードを回避します。 代わりに、設定、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>プロパティを<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>または<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>します。  
  
## <a name="using-shared-rows"></a>使用して行を共有  
 効率的なメモリの使用が実現されます、<xref:System.Windows.Forms.DataGridView>共有行を制御します。 行のインスタンスを共有することで可能な外観と動作について多くの情報を共有、<xref:System.Windows.Forms.DataGridViewRow>クラス。  
  
 行インスタンスの共有メモリを削減できますが、行を非共有になることができます簡単に。 たとえば、たびに、ユーザーがセルを直接操作、その行は非共有になります。 これを回避できないため、このトピックのガイドラインは、ユーザーがプログラムを実行するたびに、データの比較的小さな部分に操作する場合にのみ、非常に大量のデータを使用する場合にのみ役立ちます。  
  
 行を共有することはできません、バインドされていないで<xref:System.Windows.Forms.DataGridView>のセルの値が含まれている場合は、制御します。 ときに、<xref:System.Windows.Forms.DataGridView>コントロールの外部データ ソースにバインドするか、セル オブジェクトであり、共有する行ではなく、コントロールの外側に、セルの値が格納されます仮想モードを実装して、独自のデータ ソースを提供するとします。  
  
 すべてのセルの状態は、行の状態と、セルを含む列の状態から決定できる場合、行オブジェクトを共有のみできます。 その行と列の状態から不要になった推測できるように、セルの状態を変更する場合、行は共有できません。  
  
 たとえば、行は、次の状況で共有ことはできません。  
  
-   行には、選択した列ではない 1 つの選択したセルが含まれています。  
  
-   行のセルに含まれるその<xref:System.Windows.Forms.DataGridViewCell.ToolTipText%2A>または<xref:System.Windows.Forms.DataGridViewCell.ContextMenuStrip%2A>プロパティを設定します。  
  
-   行に含まれる、<xref:System.Windows.Forms.DataGridViewComboBoxCell>でその<xref:System.Windows.Forms.DataGridViewComboBoxCell.Items%2A>プロパティ セット。  
  
 バインド モードまたは仮想モードで行うことができますツールヒントとショートカット メニューの個々 のセルを処理することによって、<xref:System.Windows.Forms.DataGridView.CellToolTipTextNeeded>と<xref:System.Windows.Forms.DataGridView.CellContextMenuStripNeeded>イベント。  
  
 <xref:System.Windows.Forms.DataGridView>コントロールは、自動的に行が追加されるたびに、共有行を使用する試行、<xref:System.Windows.Forms.DataGridViewRowCollection>します。 行を共有することを確認するのにには、次のガイドラインを使用します。  
  
-   呼び出すことは避け、`Add(Object[])`のオーバー ロード、<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>メソッドと`Insert(Object[])`のオーバー ロード、<xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A>のメソッド、<xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>コレクション。 これらのオーバー ロードは、共有されていない行を自動的に作成します。  
  
-   必ずで指定された行、<xref:System.Windows.Forms.DataGridView.RowTemplate%2A?displayProperty=nameWithType>プロパティは、次の場合に共有できます。  
  
    -   呼び出すときに、`Add()`または`Add(Int32)`のオーバー ロード、<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>メソッドまたは`Insert(Int32,Int32)`のオーバー ロード、<xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A>のメソッド、<xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>コレクション。  
  
    -   値を増やすときに、<xref:System.Windows.Forms.DataGridView.RowCount%2A?displayProperty=nameWithType>プロパティ。  
  
    -   設定するときに、<xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>プロパティ。  
  
-   必ずによって示される行、`indexSource`を呼び出すときに、パラメーターを共有できる、 <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopy%2A>、 <xref:System.Windows.Forms.DataGridViewRowCollection.AddCopies%2A>、 <xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopy%2A>、および<xref:System.Windows.Forms.DataGridViewRowCollection.InsertCopies%2A>のメソッド、<xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>コレクション。  
  
-   指定された行または行を共有できることを呼び出すときに必ず、`Add(DataGridViewRow)`のオーバー ロード、<xref:System.Windows.Forms.DataGridViewRowCollection.Add%2A>メソッド、<xref:System.Windows.Forms.DataGridViewRowCollection.AddRange%2A>メソッド、`Insert(Int32,DataGridViewRow)`のオーバー ロード、<xref:System.Windows.Forms.DataGridViewRowCollection.Insert%2A>メソッド、および<xref:System.Windows.Forms.DataGridViewRowCollection.InsertRange%2A>のメソッド<xref:System.Windows.Forms.DataGridView.Rows%2A?displayProperty=nameWithType>コレクション。  
  
 行が共有されているかどうかを調べるには、<xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType>メソッドを行オブジェクトを取得し、オブジェクトの<xref:System.Windows.Forms.DataGridViewBand.Index%2A>プロパティ。 共有の行が常にある、<xref:System.Windows.Forms.DataGridViewBand.Index%2A>プロパティの値は-1。  
  
## <a name="preventing-rows-from-becoming-unshared"></a>行が非共有になることを防ぐ  
 共有された行はコードまたはユーザーのアクションの結果として非共有になります。 パフォーマンスに影響を避けるためには、共有が解除する行の原因を避ける必要があります。 処理できるアプリケーションの開発中、<xref:System.Windows.Forms.DataGridView.RowUnshared>行が非共有になるかのイベント。 これは、機能は、行の共有の問題をデバッグするときに便利です。  
  
 行が非共有になることを防ぐためには、次のガイドラインを使用します。  
  
-   インデックス作成を避けるため、<xref:System.Windows.Forms.DataGridView.Rows%2A>コレクションまたは反復処理に使用して、`foreach`ループします。 行に直接アクセスする通常必要はありません。 <xref:System.Windows.Forms.DataGridView> 行を操作するメソッドは、行のインスタンスではなく、行のインデックスの引数を受け取ります。 さらに、行に関連するイベント ハンドラーは、行を非共有になることを発生させることがなく操作に使用できる行のプロパティを持つイベント引数オブジェクトを受け取ります。  
  
-   行オブジェクトにアクセスする必要がある場合、<xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType>メソッドと行の実際のインデックスを渡します。 ただし、このメソッドを使用して取得共有行オブジェクトを変更すると、このオブジェクトを共有するすべての行が変更することに注意してください。 新しいレコードの行とは共有されません他の行では、ただし、他の任意の行を変更するときに影響ありません。 共有行で表される別の行が別のショートカット メニューにあることにも注意してください。 行の共有インスタンスから正しいショートカット メニューを取得するには使用、<xref:System.Windows.Forms.DataGridViewRow.GetContextMenuStrip%2A>メソッドと行の実際のインデックスを渡します。 行の共有にアクセスする場合<xref:System.Windows.Forms.DataGridViewRow.ContextMenuStrip%2A>プロパティ代わりに、-1 の場合、共有行インデックスを使用し、正しいショートカット メニューは取得しません。  
  
-   インデックス作成を避けるため、<xref:System.Windows.Forms.DataGridViewRow.Cells%2A?displayProperty=nameWithType>コレクション。 セルに直接アクセスすると、その親の行が解除された場合、新しくインスタンス化する<xref:System.Windows.Forms.DataGridViewRow>します。 セルに関連するイベント ハンドラーは、共有が解除する行を発生させることがなくセルを操作するのに使用できるセルのプロパティを持つイベント引数オブジェクトを受け取ります。 使用することも、<xref:System.Windows.Forms.DataGridView.CurrentCellAddress%2A>セルに直接アクセスすることがなく現在のセルの行と列のインデックスを取得するプロパティ。  
  
-   セル ベースの選択モードを回避します。 これらのモードでは、共有が解除する行が発生します。 代わりに、設定、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>プロパティを<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>または<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect?displayProperty=nameWithType>します。  
  
-   処理できない、<xref:System.Windows.Forms.DataGridViewRowCollection.CollectionChanged?displayProperty=nameWithType>または<xref:System.Windows.Forms.DataGridView.RowStateChanged?displayProperty=nameWithType>イベント。 これらのイベントが発生する行を非共有になります。 また、呼び出さないでください、<xref:System.Windows.Forms.DataGridViewRowCollection.OnCollectionChanged%2A?displayProperty=nameWithType>または<xref:System.Windows.Forms.DataGridView.OnRowStateChanged%2A?displayProperty=nameWithType>メソッドで、これらのイベントを発生させます。  
  
-   アクセスしない、<xref:System.Windows.Forms.DataGridView.SelectedCells%2A?displayProperty=nameWithType>コレクション時に、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>プロパティの値が<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>、 <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>、 <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>、または<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>します。 これにより、すべての選択した行を非共有になります。  
  
-   呼び出すのではない、<xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A?displayProperty=nameWithType>メソッド。 このメソッドは、共有が解除する行が発生することができます。  
  
-   呼び出すのではない、<xref:System.Windows.Forms.DataGridView.SelectAll%2A?displayProperty=nameWithType>メソッドと、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A?displayProperty=nameWithType>プロパティの値が<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>します。 これにより、すべての行を非共有になります。  
  
-   設定しないでください、<xref:System.Windows.Forms.DataGridViewCell.ReadOnly%2A>または<xref:System.Windows.Forms.DataGridViewCell.Selected%2A>プロパティに、セルの`false`その列に対応するプロパティを設定すると`true`します。 これにより、すべての行を非共有になります。  
  
-   アクセスしない、<xref:System.Windows.Forms.DataGridViewRowCollection.List%2A?displayProperty=nameWithType>プロパティ。 これにより、すべての行を非共有になります。  
  
-   呼び出すのではない、`Sort(IComparer)`のオーバー ロード、<xref:System.Windows.Forms.DataGridView.Sort%2A>メソッド。 並べ替えるカスタム比較子を使用すると、すべての行を非共有になります。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- [Windows フォーム DataGridView コントロールでのパフォーマンス チューニング](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでの仮想モード](virtual-mode-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのデータ表示モード](data-display-modes-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのセルのスタイル](cell-styles-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォームの DataGridView コントロールの既定のセル スタイルを設定します。](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールのサイズ変更オプション](sizing-options-in-the-windows-forms-datagridview-control.md)
