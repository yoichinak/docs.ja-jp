---
title: Windows フォーム DataGridView コントロール内の列の並べ替えモード
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], sort modes
- DataGridView control [Windows Forms], sort mode
ms.assetid: 43715887-2df9-4da7-bcf1-b9c7c842b2bf
ms.openlocfilehash: d0d743ccae38d101eda5bb9780b33ae18dfb608a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918449"
---
# <a name="column-sort-modes-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロール内の列の並べ替えモード
<xref:System.Windows.Forms.DataGridView>列には3つの並べ替えモードがあります。 各列の並べ替えモードは、次<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> <xref:System.Windows.Forms.DataGridViewColumnSortMode>の列挙値のいずれかに設定できる、列のプロパティによって指定されます。  
  
|`DataGridViewColumnSortMode` の値|説明|  
|----------------------------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>|テキストボックスの列の既定値。 列ヘッダーを選択に使用しない限り、列ヘッダーをクリックする<xref:System.Windows.Forms.DataGridView>と、自動的にこの列によってが並べ替えられ、並べ替え順序を示すグリフが表示されます。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>|テキストボックス以外の列の既定値。 この列はプログラムで並べ替えることができます。ただし、並べ替えのためのものではないため、並べ替えグリフ用の領域は予約されていません。|  
|<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>|この列はプログラムで並べ替えることができ、領域は並べ替えグリフ用に予約されています。|  
  
 意味のある順序付けが可能な値が含まれている<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>場合は、既定の列の並べ替えモードを変更することができます。 たとえば、アイテムの状態を表す数値を含むデータベース列がある場合は、データベース列に画像列をバインドすることで、これらの数値を対応するアイコンとして表示できます。 その後、 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>イベントのハンドラーで数値セル値を画像表示値に変更できます。 この場合、 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>プロパティをに設定する<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>と、ユーザーが列を並べ替えることができるようになります。 自動並べ替えを使用すると、ユーザーは、数値に対応する状態に自然な順序が設定されていない場合でも、同じ状態の項目をグループ化できます。 チェックボックスの列は、同じ状態の項目をグループ化するために自動並べ替えが役立つもう1つの例です。  
  
 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>設定に関係なく<xref:System.Windows.Forms.DataGridView> 、任意の列または複数の列の値によって、プログラムによってを並べ替えることができます。 プログラムによる並べ替えは、並べ替えに独自のユーザーインターフェイス (UI) を提供したり、カスタムの並べ替えを実装したりする場合に便利です。 列ヘッダーの選択を有効にするように<xref:System.Windows.Forms.DataGridView>選択モードを設定する場合などに、独自の並べ替え UI を提供すると便利です。 この場合、列ヘッダーは並べ替えに使用できませんが、ヘッダーに適切な並べ替えグリフが表示されるようにするには、 <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>プロパティをに<xref:System.Windows.Forms.DataGridViewColumnSortMode.Programmatic>設定します。  
  
 プログラムによる並べ替えモードに設定されている列は、並べ替えグリフを自動的に表示しません。 これらの列では、 <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>プロパティを設定することによって、自分でグリフを表示する必要があります。 これは、カスタムの並べ替えの柔軟性を必要とする場合に必要です。 たとえば、複数の列でを<xref:System.Windows.Forms.DataGridView>並べ替える場合は、複数の並べ替えグリフを表示するか、並べ替えグリフを使用しないようにすることができます。  
  
 プログラムを使用して、 <xref:System.Windows.Forms.DataGridView>任意の列でを並べ替えることができますが、ボタン列などの一部の列には、意味のある順序付けが可能な値が含まれていない場合があります。 これらの列の場合<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> 、の<xref:System.Windows.Forms.DataGridViewColumnSortMode.NotSortable>プロパティ設定は、並べ替えに使用されないことを示します。したがって、並べ替えグリフのヘッダーに領域を予約する必要はありません。  
  
 が並べ替えられている場合は、プロパティ<xref:System.Windows.Forms.DataGridView.SortedColumn%2A>と<xref:System.Windows.Forms.DataGridView.SortOrder%2A>プロパティの値を確認することで、並べ替え列と並べ替え順序の両方を確認できます。 <xref:System.Windows.Forms.DataGridView> これらの値は、カスタムの並べ替え操作の後に意味がありません。 カスタム並べ替えの詳細については、このトピックで後述する「カスタム並べ替え」セクションを参照してください。  
  
 バインドされた列とバインドされていない列の両方を含むコントロールを並べ替える場合、バインドされていない列の値は自動的に保持されません。<xref:System.Windows.Forms.DataGridView> これらの値を維持<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>するには、プロパティをに`true`設定し、イベント<xref:System.Windows.Forms.DataGridView.CellValueNeeded>と<xref:System.Windows.Forms.DataGridView.CellValuePushed>イベントを処理することによって、仮想モードを実装する必要があります。 詳細については、「[方法 :Windows フォーム DataGridView コントロール](how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)で仮想モードを実装します。 バインドモードでの非バインド列による並べ替えはサポートされていません。  
  
## <a name="programmatic-sorting"></a>プログラムによる並べ替え  
 メソッド<xref:System.Windows.Forms.DataGridView.Sort%2A>を呼び出す<xref:System.Windows.Forms.DataGridView>ことによって、プログラムでを並べ替えることができます。  
  
 メソッドのオーバーロードは`Sort(DataGridViewColumn,ListSortDirection)` 、パラメーターと<xref:System.Windows.Forms.DataGridViewColumn>してと列挙値を受け取ります。<xref:System.ComponentModel.ListSortDirection> <xref:System.Windows.Forms.DataGridView.Sort%2A> このオーバーロードは、意味のある順序を指定できるが、自動並べ替えを構成しない値を持つ列で並べ替える場合に便利です。 このオーバーロードを呼び出し<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> 、プロパティ値がの<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic?displayProperty=nameWithType>列を渡すと、 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A>プロパティと<xref:System.Windows.Forms.DataGridView.SortOrder%2A>プロパティが自動的に設定され、適切な並べ替えグリフが列ヘッダーに表示されます。  
  
> [!NOTE]
> プロパティを設定して、 `Sort(DataGridViewColumn,ListSortDirection)` コントロールが外部データソースにバインドされている場合、バインドされていない列に対してはメソッドオーバーロードは機能しません。<xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.DataSource%2A> また、 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティが`true`の場合は、バインドされた列に対してのみこのオーバーロードを呼び出すことができます。 列がデータバインドされて<xref:System.Windows.Forms.DataGridViewColumn.IsDataBound%2A>いるかどうかを判断するには、プロパティ値を確認します。 バインドモードでの非バインド列の並べ替えはサポートされていません。  
  
## <a name="custom-sorting"></a>カスタム並べ替え  
 をカスタマイズ<xref:System.Windows.Forms.DataGridView>するには、 `Sort(IComparer)` <xref:System.Windows.Forms.DataGridView.Sort%2A>メソッドのオーバーロードを使用するか、 <xref:System.Windows.Forms.DataGridView.SortCompare>イベントを処理します。  
  
 メソッド`Sort(IComparer)`オーバーロードは、インターフェイスを<xref:System.Collections.IComparer>実装するクラスのインスタンスをパラメーターとして受け取ります。 このオーバーロードは、カスタムの並べ替えを提供する場合に便利です。たとえば、列の値に自然な並べ替え順序が設定されていない場合や、自然な並べ替え順序が適切でない場合などです。 この場合、自動並べ替えを使用することはできませんが、列ヘッダーをクリックしてユーザーが並べ替えられるようにすることもできます。 列ヘッダーを選択に使用しない場合は<xref:System.Windows.Forms.DataGridView.ColumnHeaderMouseClick> 、イベントのハンドラーでこのオーバーロードを呼び出すことができます。  
  
> [!NOTE]
> メソッド`Sort(IComparer)`オーバーロードは、 <xref:System.Windows.Forms.DataGridView>コントロールが<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>外部データソースにバインドされておらず、プロパティ値が`false`の場合にのみ機能します。 外部データソースにバインドされている列の並べ替えをカスタマイズするには、データソースによって提供される並べ替え操作を使用する必要があります。 仮想モードでは、バインドされていない列に対して独自の並べ替え操作を提供する必要があります。  
  
 `Sort(IComparer)`メソッドオーバーロードを使用するには、 <xref:System.Collections.IComparer>インターフェイスを実装する独自のクラスを作成する必要があります。 このインターフェイスで<xref:System.Collections.IComparer.Compare%2A?displayProperty=nameWithType>は、メソッドのオーバーロードが呼び出されたとき<xref:System.Windows.Forms.DataGridView> `Sort(IComparer)`に<xref:System.Windows.Forms.DataGridViewRow>がオブジェクトを入力として渡すメソッドを実装するために、クラスが必要です。 これにより、任意の列の値に基づいて、正しい行の順序を計算できます。  
  
 メソッドのオーバーロードでは、 <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> <xref:System.Windows.Forms.DataGridView.SortOrder%2A>プロパティとプロパティが設定されないため、並べ替えグリフを表示するようにプロパティを常に設定する必要があります。<xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType> `Sort(IComparer)`  
  
 メソッドオーバーロードの`Sort(IComparer)`代わりに、 <xref:System.Windows.Forms.DataGridView.SortCompare>イベントのハンドラーを実装することによって、カスタムの並べ替えを行うことができます。 このイベントは、自動並べ替えを行うように構成された列のヘッダーをユーザー `Sort(DataGridViewColumn,ListSortDirection)`がクリックし<xref:System.Windows.Forms.DataGridView.Sort%2A>たとき、またはメソッドのオーバーロードを呼び出したときに発生します。 イベントは、コントロール内の行の各ペアに対して発生し、正しい順序を計算できるようにします。  
  
> [!NOTE]
> プロパティが設定さ<xref:System.Windows.Forms.DataGridView.SortCompare>れている場合、`true`またはプロパティの値がの場合、イベントは発生しません。<xref:System.Windows.Forms.DataGridView.VirtualMode%2A> <xref:System.Windows.Forms.DataGridView.DataSource%2A>  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortedColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.SortOrder%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A?displayProperty=nameWithType>
- [Windows フォームの DataGridView コントロールでのデータの並べ替え](sorting-data-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム DataGridView コントロールの列の並べ替えモードを設定する](set-the-sort-modes-for-columns-wf-datagridview-control.md)
- [方法: Windows フォーム DataGridView コントロールでの並べ替えのカスタマイズ](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
