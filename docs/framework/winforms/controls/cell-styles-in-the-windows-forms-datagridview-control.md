---
title: Windows フォーム DataGridView コントロールでのセルのスタイル
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: dbb75ed6-8804-4232-8382-f9920c2e380c
ms.openlocfilehash: be4c47db5c56685a84153a9ae4a9a2fe14c6adad
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917766"
---
# <a name="cell-styles-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールでのセルのスタイル
<xref:System.Windows.Forms.DataGridView>コントロール内の各セルは、テキスト形式、背景色、前景色、フォントなど、独自のスタイルを持つことができます。 ただし、通常は、複数のセルで特定のスタイル特性を共有します。  
  
 スタイルを共有するセルのグループには、特定の行または列内のすべてのセル、特定の値を含むすべてのセル、またはコントロール内のすべてのセルを含めることができます。 これらのグループが重なっているため、各セルのスタイル情報が複数の場所から取得される場合があります。 たとえば、 <xref:System.Windows.Forms.DataGridView>コントロール内のすべてのセルで同じフォントを使用する必要があり、通貨の列のセルだけが通貨形式を使用するようにし、負の値を持つ通貨セルのみが赤の前景色を使用するようにすることができます。  
  
## <a name="the-datagridviewcellstyle-class"></a>DataGridViewCellStyle クラス  
 <xref:System.Windows.Forms.DataGridViewCellStyle>クラスには、visual スタイルに関連する次のプロパティが含まれています。  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>  
  
 このクラスには、書式設定に関連する次のプロパティも含まれています。  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> および <xref:System.Windows.Forms.DataGridViewCellStyle.DataSourceNullValue%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A>  
  
- <xref:System.Windows.Forms.DataGridViewCellStyle.Padding%2A>  
  
 これらのプロパティおよびその他のセルスタイルのプロパティの詳細につい<xref:System.Windows.Forms.DataGridViewCellStyle>ては、以下の「関連項目」セクションに記載されているリファレンスドキュメントとトピックを参照してください。  
  
## <a name="using-datagridviewcellstyle-objects"></a>DataGridViewCellStyle オブジェクトの使用  
 <xref:System.Windows.Forms.DataGridView>、 <xref:System.Windows.Forms.DataGridViewCellStyle> 、、および<xref:System.Windows.Forms.DataGridViewCell>の各クラスとその派生クラスのさまざまなプロパティからオブジェクトを取得できます。 <xref:System.Windows.Forms.DataGridViewRow> <xref:System.Windows.Forms.DataGridViewColumn> これらのプロパティのいずれかがまだ設定されていない場合は、その<xref:System.Windows.Forms.DataGridViewCellStyle>値を取得すると新しいオブジェクトが作成されます。 独自<xref:System.Windows.Forms.DataGridViewCellStyle>のオブジェクトをインスタンス化して、これらのプロパティに割り当てることもできます。  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> 複数<xref:System.Windows.Forms.DataGridView>の要素間でオブジェクトを共有することによって、スタイル情報の不要な重複を回避できます。 コントロール、列、および行の各レベルで設定されたスタイルによって、各レベルがセルレベルまでフィルター処理されるため、上記のレベルとは異なる各レベルのスタイルプロパティのみを設定することにより、スタイルの重複を回避することもできます。 詳細については、後の「スタイルの継承」セクションを参照してください。  
  
 次の表に、オブジェクトを取得または設定<xref:System.Windows.Forms.DataGridViewCellStyle>する主なプロパティを示します。  
  
|プロパティ|クラス|説明|  
|--------------|-------------|-----------------|  
|`DefaultCellStyle`|<xref:System.Windows.Forms.DataGridView>、 <xref:System.Windows.Forms.DataGridViewColumn>、、およびの各派生クラス<xref:System.Windows.Forms.DataGridViewRow>|コントロール全体 (ヘッダーセルを含む)、列、または行内のすべてのセルで使用される既定のスタイルを取得または設定します。|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|コントロールのすべての行で使用される既定のセルスタイルを取得または設定します。 これには、ヘッダーセルは含まれません。|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|コントロールの交互の行で使用される既定のセルスタイルを取得または設定します。 元帳に似た効果を作成するために使用します。|  
|<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|コントロールの行ヘッダーによって使用される既定のセルスタイルを取得または設定します。 Visual スタイルが有効になっている場合、現在のテーマによってオーバーライドされます。|  
|<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>|<xref:System.Windows.Forms.DataGridView>|コントロールの列ヘッダーによって使用される既定のセルスタイルを取得または設定します。 Visual スタイルが有効になっている場合、現在のテーマによってオーバーライドされます。|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A>|<xref:System.Windows.Forms.DataGridViewCell>および派生クラス|セルレベルで指定されたスタイルを取得または設定します。 これらのスタイルは、上位レベルから継承されたスタイルよりも優先されます。|  
|`InheritedStyle`|<xref:System.Windows.Forms.DataGridViewCell>、 <xref:System.Windows.Forms.DataGridViewRow>、、およびの各派生クラス<xref:System.Windows.Forms.DataGridViewColumn>|上位レベルから継承されたスタイルを含む、セル、行、または列に現在適用されているすべてのスタイルを取得します。|  
  
 前述のように、プロパティが以前に設定されていない<xref:System.Windows.Forms.DataGridViewCellStyle>場合、スタイルプロパティの値を取得すると、新しいオブジェクトが自動的にインスタンス化されます。 これらのオブジェクトを不必要に作成しないように、行クラス<xref:System.Windows.Forms.DataGridViewBand.HasDefaultCellStyle%2A>と列クラスにはプロパティがあり、 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A>プロパティが設定されているかどうかを確認できます。 同様に、セルクラスには<xref:System.Windows.Forms.DataGridViewCell.HasStyle%2A> 、 <xref:System.Windows.Forms.DataGridViewCell.Style%2A>プロパティが設定されているかどうかを示すプロパティがあります。  
  
 各スタイルプロパティには、 <xref:System.Windows.Forms.DataGridView>コントロールに対応する*PropertyName* `Changed`イベントがあります。 行、列、およびセルの各プロパティの場合、イベントの名前は "`Row`"、"`Column`"、または`Cell`"" ( <xref:System.Windows.Forms.DataGridView.RowDefaultCellStyleChanged>など) で始まります。 これらの各イベントは、対応するスタイルプロパティが別<xref:System.Windows.Forms.DataGridViewCellStyle>のオブジェクトに設定されている場合に発生します。 これらのイベントは、スタイルプロパティからオブジェクト<xref:System.Windows.Forms.DataGridViewCellStyle>を取得し、そのプロパティ値を変更したときには発生しません。 セルスタイルオブジェクト自体への変更に応答するには、 <xref:System.Windows.Forms.DataGridView.CellStyleContentChanged>イベントを処理します。  
  
## <a name="style-inheritance"></a>スタイルの継承  
 各<xref:System.Windows.Forms.DataGridViewCell>は、その<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>プロパティから外観を取得します。 この<xref:System.Windows.Forms.DataGridViewCellStyle>プロパティによって返されるオブジェクトは、型<xref:System.Windows.Forms.DataGridViewCellStyle>のプロパティの階層から値を継承します。 これらのプロパティは、ヘッダー以外のセルのが<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>値を取得する順序で下に一覧表示されます。  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(インデックス番号が奇数の行のセルのみ)  
  
4. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
5. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
6. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 行と列のヘッダーセルの場合<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A> 、プロパティは、指定された順序で、次のソースプロパティのリストの値によって設定されます。  
  
1. <xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A?displayProperty=nameWithType> または <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A?displayProperty=nameWithType>  
  
3. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 このプロセスを説明する図を次に示します。  
  
 ![DataGridViewCellStyle 型のプロパティ](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-inheritance-diagram.gif "DataGridViewCells 継承ダイアグラム")  
  
 また、特定の行と列によって継承されたスタイルにアクセスすることもできます。 Column <xref:System.Windows.Forms.DataGridViewColumn.InheritedStyle%2A>プロパティは、次のプロパティからその値を継承します。  
  
1. <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 Row <xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A>プロパティは、次のプロパティからその値を継承します。  
  
1. <xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
2. <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>(インデックス番号が奇数の行のセルのみ)  
  
3. <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
  
4. <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
  
 プロパティ<xref:System.Windows.Forms.DataGridViewCellStyle> <xref:System.Windows.Forms.DataGridViewCellStyle>によって返されるオブジェクトの各プロパティについて、プロパティ値は、対応するプロパティがクラスの既定値以外の値に設定されている、適切なリストの最初のセルスタイルから取得されます。`InheritedStyle`  
  
 次の表は、例<xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>のセルのプロパティ値が、その親列から継承される方法を示しています。  
  
|型のプロパティ`DataGridViewCellStyle`|取得`ForeColor`したオブジェクトの値の例|  
|----------------------------------------------|----------------------------------------------------|  
|<xref:System.Windows.Forms.DataGridViewCell.Style%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewRow.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Empty?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.DarkBlue%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>|<xref:System.Drawing.Color.Black%2A?displayProperty=nameWithType>|  
  
 この場合、 <xref:System.Drawing.Color.Red%2A?displayProperty=nameWithType>セルの行の値は、リストの最初の実際の値になります。 これは、 <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> <xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>セルののプロパティ値になります。  
  
 次の図は、さまざま<xref:System.Windows.Forms.DataGridViewCellStyle>なプロパティが異なる場所から値を継承する方法を示しています。  
  
 ![DataGridView プロパティ&#45;値の継承](./media/cell-styles-in-the-windows-forms-datagridview-control/datagridviewcells-value-inheritance-diagram.gif "DataGridViewCells 値の継承ダイアグラム")  
  
 スタイルの継承を利用することで、複数の場所で同じ情報を指定しなくても、コントロール全体に適したスタイルを提供できます。  
  
 ヘッダーセルは、説明のとおりスタイル継承に参加しますが、 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> <xref:System.Windows.Forms.DataGridView>コントロール<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>のプロパティおよびプロパティによって返されるオブジェクトには、によって返されるオブジェクトのプロパティ値をオーバーライドする初期プロパティ値があります。<xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>プロパティ。 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>プロパティによって返されるオブジェクトに対して設定されたプロパティを行ヘッダーと列ヘッダーに適用する場合は、プロパティ<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>および<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>プロパティによって返されるオブジェクトの対応するプロパティを、指定された既定値に設定する必要があります。<xref:System.Windows.Forms.DataGridViewCellStyle>クラスの。  
  
> [!NOTE]
> 視覚スタイルが有効になっている場合、行ヘッダーと列ヘッダー <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>(を除く) は、現在のテーマによって自動的にスタイルが設定され、これらのプロパティによって指定されたすべてのスタイルがオーバーライドされます。  
  
 型、型<xref:System.Windows.Forms.DataGridViewButtonColumn>、 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>および型も、column <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>プロパティによって返されるオブジェクトの一部の値を初期化します。 <xref:System.Windows.Forms.DataGridViewImageColumn> 詳細については、これらの型のリファレンスドキュメントを参照してください。  
  
## <a name="setting-styles-dynamically"></a>動的なスタイル設定  
 特定の値を持つセルのスタイルをカスタマイズするには、 <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>イベントのハンドラーを実装します。 このイベントのハンドラーは、 <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>型の引数を受け取ります。 このオブジェクトには、書式設定されているセルの値を<xref:System.Windows.Forms.DataGridView>コントロール内のその位置と共に判断するためのプロパティが含まれています。 このオブジェクトには、 <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.CellStyle%2A>書式設定されるセルの<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>プロパティの値に初期化されるプロパティも含まれています。 セルスタイルのプロパティを変更して、セルの値と場所に適したスタイル情報を指定できます。  
  
> [!NOTE]
> イベント<xref:System.Windows.Forms.DataGridView.RowPrePaint>と<xref:System.Windows.Forms.DataGridView.RowPostPaint>イベントは、イベント<xref:System.Windows.Forms.DataGridViewCellStyle>データ内でもオブジェクトを受け取りますが、その場合は読み取り専用の行<xref:System.Windows.Forms.DataGridViewRow.InheritedStyle%2A>プロパティのコピーであるため、変更内容はコントロールに影響しません。  
  
 イベント<xref:System.Windows.Forms.DataGridView.CellMouseEnter?displayProperty=nameWithType> や<xref:System.Windows.Forms.DataGridView.CellMouseLeave>イベントなどのイベントに応じて、個々のセルのスタイルを動的に変更することもできます。 たとえば、 <xref:System.Windows.Forms.DataGridView.CellMouseEnter>イベントのハンドラーで、セルの背景色の現在の値 (セルの<xref:System.Windows.Forms.DataGridViewCell.Style%2A>プロパティを通じて取得される) を格納し、マウスをポイントしたときにセルを強調表示する新しい色に設定することができます。 <xref:System.Windows.Forms.DataGridView.CellMouseLeave>イベントのハンドラーでは、背景色を元の値に戻すことができます。  
  
> [!NOTE]
> 特定のスタイル値が設定され<xref:System.Windows.Forms.DataGridViewCell.Style%2A>ているかどうかに関係なく、セルのプロパティに格納されている値をキャッシュすることが重要です。 スタイル設定を一時的に置き換える場合は、元の "設定なし" の状態に復元することで、そのセルが上位レベルからスタイル設定を継承するようになります。 スタイルが継承されているかどうかに関係なく、セルに対して実際に有効なスタイルを決定<xref:System.Windows.Forms.DataGridViewCell.InheritedStyle%2A>する必要がある場合は、セルのプロパティを使用します。  
  
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
- [方法: Windows フォーム DataGridView コントロールの既定のセルスタイルを設定する](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールでのデータの書式設定](data-formatting-in-the-windows-forms-datagridview-control.md)
