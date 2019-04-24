---
title: DataGrid コントロールのサイズ変更方法
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid control [WPF], sizing
- size [WPF], DataGrid
- automatically size DataGrid [WPF]
ms.assetid: 96a0e47e-b010-4302-98ef-2daac446d8db
ms.openlocfilehash: 6d100fb17b1ee3e652985a637d333d9f65e20d36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59769802"
---
# <a name="sizing-options-in-the-datagrid-control"></a>DataGrid コントロールのサイズ変更方法
さまざまなオプションは、コントロールを使用する方法、<xref:System.Windows.Controls.DataGrid>自体のサイズします。 <xref:System.Windows.Controls.DataGrid>、および個々 の行と列で、 <xref:System.Windows.Controls.DataGrid>、その内容を自動的にサイズに設定することができます、または特定の値に設定することができます。 既定で、<xref:System.Windows.Controls.DataGrid>拡大およびその内容のサイズに合わせて縮小されます。  
  
## <a name="sizing-the-datagrid"></a>データ グリッドのサイズ変更  
  
### <a name="cautions-when-using-automatic-sizing"></a>自動サイズ設定を使用する場合の注意事項  
 既定では、<xref:System.Windows.FrameworkElement.Height%2A>と<xref:System.Windows.FrameworkElement.Width%2A>のプロパティ、<xref:System.Windows.Controls.DataGrid>に設定されている<xref:System.Double.NaN?displayProperty=nameWithType>("`Auto`"XAML で)、および<xref:System.Windows.Controls.DataGrid>その内容のサイズに調整されます。  
  
 など、その子のサイズを制限しませんが、コンテナー内に配置されたときに、<xref:System.Windows.Controls.Canvas>または<xref:System.Windows.Controls.StackPanel>、<xref:System.Windows.Controls.DataGrid>コンテナーの表示範囲を超えた拡大して、スクロール バーは表示されません。 この条件は、使いやすさとパフォーマンスの両方の影響を与えます。  
  
 場合、データ セットにバインドするとき、<xref:System.Windows.FrameworkElement.Height%2A>の<xref:System.Windows.Controls.DataGrid>は制限されません、バインドされたデータ セットの各データ項目の行を追加する続行されます。 これが発生することができます、<xref:System.Windows.Controls.DataGrid>行が追加されると、アプリケーションの表示の境界の外側に拡張します。 <xref:System.Windows.Controls.DataGrid>は表示されませんスクロールバー例ではこのため、その<xref:System.Windows.FrameworkElement.Height%2A>は新しい行に対応するために増加し続けます。  
  
 内の行ごとのオブジェクトが作成された、<xref:System.Windows.Controls.DataGrid>します。 大規模なデータ セットを使用して、許可するかどうか、<xref:System.Windows.Controls.DataGrid>それ自体のサイズに自動的に、多数のオブジェクトの作成、アプリケーションのパフォーマンスに影響する可能性があります。  
  
 これらの問題を避けるためには、大規模なデータ セットを使用する場合、お勧め具体的には設定されて、<xref:System.Windows.FrameworkElement.Height%2A>の<xref:System.Windows.Controls.DataGrid>を制限するコンテナーに配置することもその<xref:System.Windows.FrameworkElement.Height%2A>など、<xref:System.Windows.Controls.Grid>します。 ときに、<xref:System.Windows.FrameworkElement.Height%2A>が制限された、<xref:System.Windows.Controls.DataGrid>はその指定内に収まる行のみが作成<xref:System.Windows.FrameworkElement.Height%2A>、し、新しいデータを表示するために必要なようにこれらの行をリサイクルします。  
  
### <a name="setting-the-datagrid-size"></a>データ グリッド サイズの設定  
 <xref:System.Windows.Controls.DataGrid>指定した境界内で自動的にサイズを設定することができます、または<xref:System.Windows.Controls.DataGrid>特定のサイズに設定することができます。 次の表に、コントロールに設定できるプロパティ、<xref:System.Windows.Controls.DataGrid>サイズ。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.Windows.FrameworkElement.Height%2A>|特定の高さを設定、<xref:System.Windows.Controls.DataGrid>します。|  
|<xref:System.Windows.FrameworkElement.MaxHeight%2A>|高さの上限の境界を設定、<xref:System.Windows.Controls.DataGrid>します。 <xref:System.Windows.Controls.DataGrid>この高さに達するまで垂直方向に拡張されます。|  
|<xref:System.Windows.FrameworkElement.MinHeight%2A>|高さの下限の境界を設定、<xref:System.Windows.Controls.DataGrid>します。 <xref:System.Windows.Controls.DataGrid>この高さに達するまで垂直方向に縮小されます。|  
|<xref:System.Windows.FrameworkElement.Width%2A>|特定の幅を設定、<xref:System.Windows.Controls.DataGrid>します。|  
|<xref:System.Windows.FrameworkElement.MaxWidth%2A>|幅の上限の境界を設定、<xref:System.Windows.Controls.DataGrid>します。 <xref:System.Windows.Controls.DataGrid>この幅に到達するまで水平方向に拡張されます。|  
|<xref:System.Windows.FrameworkElement.MinWidth%2A>|幅の下限の境界を設定、<xref:System.Windows.Controls.DataGrid>します。 <xref:System.Windows.Controls.DataGrid>この幅に到達するまで水平方向に縮小されます。|  
  
## <a name="sizing-rows-and-row-headers"></a>行と行ヘッダーのサイズ変更  
  
### <a name="datagrid-rows"></a>データ グリッドの行  
 既定を<xref:System.Windows.Controls.DataGrid>行の<xref:System.Windows.FrameworkElement.Height%2A>プロパティに設定されて<xref:System.Double.NaN?displayProperty=nameWithType>("`Auto`"XAML で)、行の高さがその内容のサイズを展開します。 すべての行の高さ、<xref:System.Windows.Controls.DataGrid>を設定して指定することができます、<xref:System.Windows.Controls.DataGrid.RowHeight%2A?displayProperty=nameWithType>プロパティ。 ユーザーは、行ヘッダー区分線をドラッグして行の高さを変更できます。  
  
### <a name="datagrid-row-headers"></a>DataGrid の行ヘッダー  
 行のヘッダーを表示する、<xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A>にプロパティを設定する必要があります<xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType>または<xref:System.Windows.Controls.DataGridHeadersVisibility.All?displayProperty=nameWithType>します。 既定では、行ヘッダーを表示およびそのコンテンツに合わせてサイズが自動的に調整します。 行ヘッダーは、設定して特定の幅を与えることができます、<xref:System.Windows.Controls.DataGrid.RowHeaderWidth%2A?displayProperty=nameWithType>プロパティ。  
  
## <a name="sizing-columns-and-column-headers"></a>列および列ヘッダーのサイズ変更  
  
### <a name="datagrid-columns"></a>DataGrid の列  
 <xref:System.Windows.Controls.DataGrid>の値を使用して、 <xref:System.Windows.Controls.DataGridLength> 、<xref:System.Windows.Controls.DataGridLengthUnitType>絶対または自動サイズ変更モードを指定する構造体。  
  
 次の表で指定された値、<xref:System.Windows.Controls.DataGridLengthUnitType>構造体。  
  
|名前|説明|  
|----------|-----------------|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Auto>|既定の自動サイズ変更をモード サイズ<xref:System.Windows.Controls.DataGrid>セルと列ヘッダーの内容に基づく列。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToCells>|セル ベースの自動モードのサイズをサイズ変更<xref:System.Windows.Controls.DataGrid>列ヘッダーを含まない、列のセルの内容に基づく列。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.SizeToHeader>|ヘッダー ベースの自動モードのサイズをサイズ変更<xref:System.Windows.Controls.DataGrid>のみの列ヘッダーの内容に基づく列。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Pixel>|ピクセル ベース モードのサイズをサイズ変更<xref:System.Windows.Controls.DataGrid>指定された数値に基づく列。|  
|<xref:System.Windows.Controls.DataGridLengthUnitType.Star>|星のサイズ変更モードは、使用可能なスペースを分配する加重比率で使用されます。<br /><br /> XAML では、星型の値は n * n が数値を表しますとして表現されます。 1\*と等価\*します。 たとえば、2 つ内の列を<xref:System.Windows.Controls.DataGrid>の幅が\*と 2 つ\*、最初の列が使用可能な領域の 1 つの部分を受信し、2 番目の列が使用可能な領域の 2 つの部分を受信します。|  
  
 <xref:System.Windows.Controls.DataGridLengthConverter>数値または文字列値間のデータを変換するクラスを使用できると<xref:System.Windows.Controls.DataGridLength>値。  
  
 既定で、<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>プロパティに設定されて<xref:System.Windows.Controls.DataGridLength.SizeToHeader%2A>、および<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>プロパティに設定されて<xref:System.Windows.Controls.DataGridLength.Auto%2A>します。 サイズ変更モードを設定すると<xref:System.Windows.Controls.DataGridLength.Auto%2A>または<xref:System.Windows.Controls.DataGridLength.SizeToCells%2A>列が表示される多くのコンテンツの幅に増加します。 スクロールすると、これらのサイズ変更モードによりコンテンツを展開する列、現在の列のサイズをスクロールして表示よりも大きい。 コンテンツのスクロールされて見えない後は、列は圧縮されません。  
  
 内の列、 <xref:System.Windows.Controls.DataGrid> 、指定した境界内でのみ自動的にサイズを設定することも、または列は、特定のサイズに設定することができます。 次の表では、列のサイズを制御する設定できるプロパティを示します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|<xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType>|すべての列に上限を設定、<xref:System.Windows.Controls.DataGrid>します。|  
|<xref:System.Windows.Controls.DataGridColumn.MaxWidth%2A?displayProperty=nameWithType>|個々 の列の上限の境界を設定します。 <xref:System.Windows.Controls.DataGrid.MaxColumnWidth%2A?displayProperty=nameWithType> をオーバーライドします。|  
|<xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType>|すべての列の下限の境界を設定、<xref:System.Windows.Controls.DataGrid>します。|  
|<xref:System.Windows.Controls.DataGridColumn.MinWidth%2A?displayProperty=nameWithType>|個々 の列の下限の境界を設定します。 <xref:System.Windows.Controls.DataGrid.MinColumnWidth%2A?displayProperty=nameWithType> をオーバーライドします。|  
|<xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType>|すべての列に特定の幅を設定、<xref:System.Windows.Controls.DataGrid>します。|  
|<xref:System.Windows.Controls.DataGridColumn.Width%2A?displayProperty=nameWithType>|個々 の列を特定の幅を設定します。 <xref:System.Windows.Controls.DataGrid.ColumnWidth%2A?displayProperty=nameWithType> をオーバーライドします。|  
  
### <a name="datagrid-column-headers"></a>DataGrid の列ヘッダー  
 既定では、<xref:System.Windows.Controls.DataGrid>列ヘッダーを表示します。 列ヘッダーを非表示にする、<xref:System.Windows.Controls.DataGrid.HeadersVisibility%2A>にプロパティを設定する必要があります<xref:System.Windows.Controls.DataGridHeadersVisibility.Row?displayProperty=nameWithType>または<xref:System.Windows.Controls.DataGridHeadersVisibility.None?displayProperty=nameWithType>します。 既定では、列ヘッダーが表示される場合、そのサイズは、コンテンツに合わせて自動的にされます。 列ヘッダーは、設定して特定の高さを与えることができます、<xref:System.Windows.Controls.DataGrid.ColumnHeaderHeight%2A?displayProperty=nameWithType>プロパティ。  
  
### <a name="resizing-with-the-mouse"></a>マウスを使用してサイズ変更  
 サイズを変更できるユーザー<xref:System.Windows.Controls.DataGrid>行と列、行または列ヘッダー区分線をドラッグします。 <xref:System.Windows.Controls.DataGrid>行または列のヘッダー区分線をダブルクリックして行および列の自動サイズ変更もサポートします。 ユーザーが特定の列のサイズを変更しないように、設定、<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType>プロパティを`false`の個々 の列。 ユーザーがすべての列のサイズを変更できないようにする設定、<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType>プロパティを`false`します。 ユーザーがすべての行のサイズを変更できないようにする設定、<xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A?displayProperty=nameWithType>プロパティを`false`します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGridColumn>
- <xref:System.Windows.Controls.DataGridLength>
- <xref:System.Windows.Controls.DataGridLengthConverter>
