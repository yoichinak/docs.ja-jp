---
title: Windows フォーム DataGridView コントロールでのセルのスタイル
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: 98e0ed5f4fe7b0c016b4477ac9f646037b0877ec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593424"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールでのセルのスタイル
内の各セル、<xref:System.Windows.Forms.DataGridView>コントロールがテキスト形式、背景色、前景色、およびフォントなどの独自のスタイルを持つことができます。 通常、ただし、複数のセルが共有の特定のスタイル特性。  
  
 スタイルを共有するセルのグループは、コントロールの特定の行または列、特定の値を含むすべてのセルまたはすべてのセル内のすべてのセルを含めることができます。 これらのグループが重なるために、各セルは、複数の場所からスタイル情報を取得する可能性があります。 たとえばのすべてのセルをする可能性があります、<xref:System.Windows.Forms.DataGridView>赤い前景の色を使用する負の数値を同じフォントがのみ通貨の形式を使用する通貨の列のセルと通貨のセルのみを使用するコントロール。  
  
## <a name="the-datagridviewcellstyle-class"></a>DataGridViewCellStyle クラス  
 <xref:System.Windows.Forms.DataGridViewCellStyle>クラスには、次の visual スタイルに関連するプロパティが含まれています。  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 このクラスには、書式設定に関連する次のプロパティも含まれています。  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 これらのプロパティとその他のセル スタイル プロパティの詳細については、次を参照してください。、<xref:System.Windows.Forms.DataGridViewCellStyle>リファレンス ドキュメントとトピックでは、「参照」セクションに表示します。  
  
## <a name="using-datagridviewcellstyle-objects"></a>DataGridViewCellStyle オブジェクトを使用します。  
 取得することができます<xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクトのさまざまなプロパティから、 <xref:System.Windows.Forms.DataGridView>、 <xref:System.Windows.Forms.DataGridViewColumn>、 <xref:System.Windows.Forms.DataGridViewRow>、および<xref:System.Windows.Forms.DataGridViewCell>クラスとその派生クラス。 これらのプロパティのいずれかがまだ設定されていない場合、その値を取得する方が、新規に作成されます<xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクト。 インスタンス化できる独自<xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクトし、これらのプロパティに割り当てます。  
  
 共有することでスタイル情報が不要な重複を避ける<xref:System.Windows.Forms.DataGridViewCellStyle>複数の間でオブジェクト<xref:System.Windows.Forms.DataGridView>要素。 コントロール、列、およびセル レベルの各レベルをダウン行レベルのフィルターで設定されたスタイル、ため、上位のレベルが異なるの各レベルでそれらのスタイル プロパティを設定してもスタイルの重複を回避できます。 これは、次のスタイルの継承のセクションで詳しく説明します。  
  
 次の表に、プライマリ プロパティを取得または設定<xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクト。  
  
|プロパティ|クラス|説明|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>、 <xref:System.Windows.Forms.DataGridViewColumn>、 <xref:System.Windows.Forms.DataGridViewRow>、および派生クラス|取得またはコントロール全体 (ヘッダー セルを含む)、列、または行のすべてのセルで使用される既定のスタイルを設定します。|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得またはコントロール内のすべての行で使用される既定のセル スタイルを設定します。 これは、ヘッダー セルには含まれません。|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得またはコントロール内の行を交互に使用される既定のセル スタイルを設定します。 帳簿のような効果を作成するために使用します。|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得またはコントロールの行ヘッダーで使用される既定のセル スタイルを設定します。 Visual スタイルが有効になっている場合に、現在のテーマでオーバーライドされます。|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|取得またはコントロールの列ヘッダーで使用される既定のセル スタイルを設定します。 Visual スタイルが有効になっている場合に、現在のテーマでオーバーライドされます。|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell> クラスと派生クラス|取得またはセル レベルで指定されたスタイルを設定します。 これらのスタイルより高いレベルから継承されたものをオーバーライドします。|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>、 <xref:System.Windows.Forms.DataGridViewRow>、 <xref:System.Windows.Forms.DataGridViewColumn>、および派生クラス|現在のセル、行、またはより高いレベルから継承したスタイルを含む列に適用されているすべてのスタイルを取得します。|  
  
 前述のように、新しいインスタンスにスタイル プロパティの値を自動的に取得する<xref:System.Windows.Forms.DataGridViewCellStyle>かどうか、プロパティが設定されていない以前のオブジェクトします。 行と列のクラスを不必要にこれらのオブジェクトを作成しないようにするが、<xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A>プロパティか決定を確認できるかどうか、<xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A>プロパティが設定されています。 同様に、セル クラスがある、<xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A>プロパティを示すかどうか、<xref:System.Windows.Forms.DataGridViewCell.Style%2A>プロパティが設定されています。  
  
 各スタイル プロパティが、対応する*PropertyName* `Changed`上のイベント、<xref:System.Windows.Forms.DataGridView>コントロール。 行、列、およびセルのプロパティ、イベントの名前の先頭に"`Row`「,」`Column`"、または"`Cell`"(たとえば、 <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>)。 これらの各イベントは別に、対応するスタイル プロパティが設定されている場合に発生します。<xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクト。 取得するときに、これらのイベントが発生しない、<xref:System.Windows.Forms.DataGridViewCellStyle>スタイル プロパティからオブジェクトし、そのプロパティ値を変更します。 セルのスタイル オブジェクト自体への変更に応答して、処理、<xref:System.Windows.Forms.DataGridView.CellStyleContentChanged>イベント。  
  
## <a name="style-inheritance"></a>スタイルの継承  
 各<xref:System.Windows.Forms.DataGridViewCell>からその外観を取得します。 その<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>プロパティ。 <xref:System.Windows.Forms.DataGridViewCellStyle>型のプロパティの階層からこのプロパティによって返されるオブジェクトがその値を継承<xref:System.Windows.Forms.DataGridViewCellStyle>します。 これらのプロパティがする順序で以下、<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>非ヘッダー セルの値を取得します。  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (奇数のインデックス番号を含む行のセル) の場合のみ  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 行と列のヘッダー セルで、<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>プロパティは次のような特定の順序でソースのプロパティのリストから値によって設定されます。  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> または <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 このプロセスを説明する図を次に示します。  
  
 ![DataGridViewCellStyle 型のプロパティ](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "DataGridViewCells 継承ダイアグラム")  
  
 特定の行と列によって継承されるスタイルをアクセスすることもできます。 列<xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A>プロパティは、次のプロパティからその値を継承します。  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 行<xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A>プロパティは、次のプロパティからその値を継承します。  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType> (奇数のインデックス番号を含む行のセル) の場合のみ  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 各プロパティについて、<xref:System.Windows.Forms.DataGridViewCellStyle>によって返されるオブジェクトを`InheritedStyle`プロパティ、プロパティの値は以外の値に設定した対応するプロパティを持つ、該当する一覧で、最初のセル スタイルから取得した、<xref:System.Windows.Forms.DataGridViewCellStyle>クラスの既定値。  
  
 次の表は方法、<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>例のセルに対してプロパティの値は、含んでいる列から継承されます。  
  
|型のプロパティ `DataGridViewCellStyle`|例`ForeColor`取得したオブジェクトの値|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 ここで、<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>セルの行から値がリストの最初の実際の値。 これは、<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>プロパティ値のセルの<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>します。  
  
 次の図はさまざまな<xref:System.Windows.Forms.DataGridViewCellStyle>プロパティは、さまざまな場所から値を継承することができます。  
  
 ![DataGridView プロパティ&#45;値の継承](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "DataGridViewCells 値の継承図")  
  
 スタイルの継承を利用して複数の場所で同じ情報を指定することがなく、コントロール全体の適切なスタイルを指定できます。  
  
 によって返されるオブジェクトの説明に従って、ヘッダー セルはスタイルの継承に参加が、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>と<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>のプロパティ、<xref:System.Windows.Forms.DataGridView>コントロールによって返されるオブジェクトのプロパティ値を上書きするプロパティの初期値があります。<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>プロパティ。 プロパティによって返されるオブジェクトを設定するかどうか、<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>行および列のヘッダーに適用するプロパティによって返されるオブジェクトの対応するプロパティを設定する必要があります、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>と<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>プロパティを既定値が示されます<xref:System.Windows.Forms.DataGridViewCellStyle>クラス。  
  
> [!NOTE]
>  Visual スタイルが有効な場合、行および列ヘッダー (以外の<xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) は、これらのプロパティで指定された任意のスタイルをオーバーライドする、現在のテーマで自動的にスタイル指定します。  
  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>、 <xref:System.Windows.Forms.DataGridViewImageColumn>、および<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>型の列によって返されるオブジェクトのいくつかの値も初期化<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>プロパティ。 詳細については、これらの型のリファレンス ドキュメントを参照してください。  
  
## <a name="setting-styles-dynamically"></a>動的なスタイルを設定  
 特定の値を持つセルのスタイルをカスタマイズするには、実装のハンドラー、<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>イベント。 このイベントのハンドラーの引数を受け取る、<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>型。 このオブジェクトには内の場所と書式設定されるセルの値を決定するプロパティが含まれています、<xref:System.Windows.Forms.DataGridView>コントロール。 このオブジェクトにも含まれています、<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A>プロパティの値に初期化される、<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>書式設定されるセルのプロパティ。 セルの値と場所に適切なスタイル情報を指定するセルのスタイル プロパティを変更することができます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView.RowPrePaint>と<xref:System.Windows.Forms.DataGridView.RowPostPaint>イベントが受信も、<xref:System.Windows.Forms.DataGridViewCellStyle>オブジェクト、データをイベントが、その場合は、行のコピーを<xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A>読み取り専用のために変更し、プロパティ、コントロールには影響しません。  
  
 などのイベントに応答して個々 のセルのスタイルを変更することができますも動的に、<xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType>と<xref:System.Windows.Forms.DataGridView.CellMouseLeave>イベント。 ハンドラーでなど、<xref:System.Windows.Forms.DataGridView.CellMouseEnter>イベント、セルの背景色の現在の値を格納できます (セルを使用して取得<xref:System.Windows.Forms.DataGridViewCell.Style%2A>プロパティ)、上にマウスを重ねると、セルが強調表示を新しい色に設定します。 ハンドラーで、<xref:System.Windows.Forms.DataGridView.CellMouseLeave>イベント、背景色を元の値に復元できます。  
  
> [!NOTE]
>  格納されたセルの値をキャッシュ<xref:System.Windows.Forms.DataGridViewCell.Style%2A>プロパティが特定のスタイル値が設定されているかに関係なく重要です。 スタイル設定を一時的に交換する場合は、セルがより高いレベルからスタイル設定の継承に戻すに移動により元の「設定なし」状態に復元すること。 有効なスタイルを継承するかどうかに関係なく、セルの実際のスタイルを決定する必要がある場合は、セルを使用して<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>プロパティ。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPrePaint?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowPostPaint?displayProperty=nameWithType>
- [Windows フォームの DataGridView コントロールの基本的な書式設定およびスタイル設定](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォームの DataGridView コントロールの既定のセル スタイルを設定します。](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのデータの書式設定](data-formatting-in-the-windows-forms-datagridview-control.md)
