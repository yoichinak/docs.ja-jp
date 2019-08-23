---
title: Windows フォーム DataGridView コントロールのサイズ変更オプション
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], row sizing
- data grids [Windows Forms], column sizing
- DataGridView control [Windows Forms], column sizing
- DataGridView control [Windows Forms], sizing options
- data grids [Windows Forms], row sizing
- data grids [Windows Forms], sizing options
ms.assetid: a5620a9c-0d06-41e3-8934-c25ddb16c9e6
ms.openlocfilehash: a8e2e05877746dfb043b7e8ac2a6c2b7017883c3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960417"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールのサイズ変更オプション
<xref:System.Windows.Forms.DataGridView>行、列、およびヘッダーは、さまざまな発生の結果としてサイズを変更できます。 次の表は、これらの出現を示しています。  
  
|見つかる|説明|  
|----------------|-----------------|  
|ユーザーのサイズ変更|ユーザーは、行、列、またはヘッダーの区切り線をドラッグまたはダブルクリックしてサイズ調整を行うことができます。|  
|コントロールのサイズ変更|列の塗りつぶしモードでは、コントロールの幅が変化したときに列幅が変化します。たとえば、コントロールが親フォームにドッキングされ、ユーザーがフォームのサイズを変更した場合などです。|  
|セル値の変更|コンテンツベースの自動サイズ調整モードでは、新しい表示値に合わせてサイズが変更されます。|  
|メソッド呼び出し|プログラムによるコンテンツベースのサイズ変更では、メソッド呼び出し時のセル値に基づいて、便宜的なサイズ調整を行うことができます。|  
|プロパティの設定|また、特定の高さと幅の値を設定することもできます。|  
  
 既定では、ユーザーのサイズ変更が有効になり、自動サイズ調整が無効になり、列よりも幅の広いセル値がクリップされます。  
  
 次の表は、既定の動作を調整したり、特定のサイズ変更オプションを使用して特定の効果を実現するために使用できるシナリオを示しています。  
  
|シナリオ|実装|  
|--------------|--------------------|  
|列の塗りつぶしモードは、水平スクロールバーを表示せずに、コントロールの幅全体を占める、比較的少数の列に同じサイズのデータを表示する場合に使用します。|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>に設定します。|  
|さまざまなサイズの表示値を使用して、列フィルモードを使用します。|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>に設定します。 列<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>のプロパティを設定するか、コントロールにデータを格納し<xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>た後でコントロールメソッドを呼び出すことによって、列の相対幅を初期化します。|  
|列フィルモードは、さまざまな重要度の値と共に使用してください。|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>に設定します。 データの<xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>一部を常に表示するか、特定の列に対して fill モード以外のサイズ変更オプションを使用する必要がある列に大きな値を設定します。|  
|コントロールの背景が表示されないようにするには、列フィルモードを使用します。|最後の列の<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill> プロパティをに設定し、他の列に対して他のサイズ変更オプションを使用します。<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> 他の列で使用可能な領域が多すぎる場合は、 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>最後の列のプロパティを設定します。|  
|固定幅の列 (アイコンや ID 列など) を表示します。|列のをに<xref:System.Windows.Forms.DataGridViewTriState.False>設定<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A>し、をに設定します。 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None> プロパティを設定する<xref:System.Windows.Forms.DataGridViewColumn.Width%2A>か、コントロールにデータを入力した後でコントロール<xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>メソッドを呼び出すことによって、幅を初期化します。|  
|クリッピングを回避し、領域の使用を最適化するためにセルの内容が変更されるたびに、サイズを自動的に調整します。|自動サイズ変更プロパティを、コンテンツベースのサイズ変更モードを表す値に設定します。 大量のデータを処理するときにパフォーマンスが低下しないようにするには、表示されている行のみを計算するサイズ変更モードを使用します。|  
|多数の行を処理するときにパフォーマンスが低下しないように、表示される行の値に合わせてサイズを調整します。|自動またはプログラムによるサイズ変更で、適切なサイズ変更モードの列挙値を使用します。 スクロール中に新しく表示された行の値に合わせてサイズを調整するに<xref:System.Windows.Forms.DataGridView.Scroll>は、イベントハンドラーでサイズ変更メソッドを呼び出します。 ユーザーがダブルクリックしたサイズ変更をカスタマイズして、表示される行の値だけが新しいサイズを決定<xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick>できる<xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick>ようにするには、イベントハンドラーまたはイベントハンドラーでサイズ変更メソッドを呼び出します。|  
|パフォーマンスの低下を避けるため、またはユーザーのサイズ変更を可能にするために、特定の時点でのみセルの内容に合わせてサイズを調整します。|イベントハンドラーでコンテンツベースのサイズ変更メソッドを呼び出します。 たとえば、 <xref:System.Windows.Forms.DataGridView.DataBindingComplete>イベントを使用して、バインド後のサイズを初期化し、 <xref:System.Windows.Forms.DataGridView.CellValueChanged>イベント<xref:System.Windows.Forms.DataGridView.CellValidated>またはイベントを処理して、バインドされたデータソースのユーザーの編集や変更に合わせてサイズを調整します。|  
|複数行のセルの内容の行の高さを調整します。|列の幅がテキストの段落を表示するのに適していることを確認し、自動またはプログラムによるコンテンツベースの行のサイズ設定を使用して高さを調整します。 また、セルスタイルの値を使用して、 <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>複数行の<xref:System.Windows.Forms.DataGridViewTriState.True>コンテンツを含むセルが表示されることを確認します。<br /><br /> 通常、列の幅を維持するには自動列サイズ変更モードを使用し、行の高さを調整する前に特定の幅に設定します。|  
  
## <a name="resizing-with-the-mouse"></a>マウスによるサイズ変更  
 既定では、ユーザーは、セル値に基づいて自動サイズ変更モードを使用しない行、列、およびヘッダーのサイズを変更できます。 列の塗りつぶしモードなど、他のモードでユーザーのサイズを変更できないようにするに<xref:System.Windows.Forms.DataGridView>は、次のプロパティの1つまたは複数を設定します。  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 また、ユーザーが個々の行や列のサイズを変更でき<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>ないようにするには、プロパティを設定します。 既定<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>では、プロパティ値は、列の<xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>プロパティ<xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>値と行のプロパティ値に基づいています。 ただし、を明示<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>的<xref:System.Windows.Forms.DataGridViewTriState.True>に<xref:System.Windows.Forms.DataGridViewTriState.False>またはに設定した場合、指定された値はその行または列のコントロール値よりも優先されます。 継承<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>を<xref:System.Windows.Forms.DataGridViewTriState.NotSet>復元するには、に設定します。  
  
 は値の継承を復元する<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>ため<xref:System.Windows.Forms.DataGridViewTriState.NotSet> 、行または<xref:System.Windows.Forms.DataGridViewTriState.NotSet>列がコントロールに追加されていない場合、プロパティは値を返しません。<xref:System.Windows.Forms.DataGridView> 行または列のプロパティ値<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>が継承されているかどうかを判断する<xref:System.Windows.Forms.DataGridViewElement.State%2A>必要がある場合は、そのプロパティを調べます。 値に<xref:System.Windows.Forms.DataGridViewElement.State%2A> <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>フラグが含まれている<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>場合、プロパティ値は継承されません。  
  
## <a name="automatic-sizing"></a>自動サイズ調整  
 <xref:System.Windows.Forms.DataGridView>コントロールには、列の塗りつぶしモードとコンテンツベースの自動サイズ調整という2種類の自動サイズ変更があります。  
  
 [列フィルモード] を指定すると、コントロールの表示列がコントロールの表示領域の幅に合わせて表示されます。 このモードの詳細については、「 [Windows フォーム DataGridView コントロールでの列の塗りつぶしモード](column-fill-mode-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
 また、行、列、ヘッダーを構成して、セルの内容に合わせてサイズを自動的に調整することもできます。 この場合、セルの内容が変更されるたびにサイズの調整が発生します。  
  
> [!NOTE]
> 仮想モードを使用してカスタムデータキャッシュのセル値を維持すると、ユーザーがセル値を編集したときに自動サイズ変更が発生しますが、 <xref:System.Windows.Forms.DataGridView.CellValuePushed>イベントハンドラーの外部でキャッシュされた値を変更しても、自動サイズ調整は行われません。 この場合は、 <xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A>メソッドを呼び出して、コントロールにセルの表示を強制的に更新し、現在の自動サイズ変更モードを適用します。  
  
 コンテンツベースの自動サイズ変更が1つのディメンションに対してのみ有効になっている場合 (つまり、行ではなく、列<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>でも、列でも有効になっていない場合) は、他のディメンションが変更されるたびにサイズの調整も行われます。 たとえば、列ではなく行を自動サイズ<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>変更するように構成されていて、有効になっている場合、ユーザーは列の区切り線をドラッグして列の幅を変更することができ、行の高さはセルの内容が完全に表示されるように自動的に調整されます。  
  
 コンテンツベースの自動サイズ変更用に行と列の両方を<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>構成し、有効<xref:System.Windows.Forms.DataGridView>にした場合、コントロールはセルの内容が変更されるたびにサイズを調整し、新しいサイズを計算するときに最適なセルの高さと幅の比率を使用します。  
  
 ヘッダーと行のサイズ変更モードと、コントロールの値をオーバーライドしない列のサイズ変更モードを構成するには、 <xref:System.Windows.Forms.DataGridView>次のプロパティの1つまたは複数を設定します。  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 個々の列のコントロールの列のサイズ変更モードをオーバーライドするに<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>は、そのプロパティを以外<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>の値に設定します。 列のサイズ変更モードは、実際には<xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>プロパティによって決定されます。 このプロパティの値は、その値が<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>である場合を除いて、列のプロパティ値に基づいてい<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>ます。この場合、コントロールの値は継承されます。  
  
 大量のデータを扱うときは、コンテンツベースの自動サイズ変更を慎重に使用してください。 パフォーマンスの低下を回避するには、コントロールのすべての行を分析するのではなく、表示された行のみに基づいてサイズを計算する自動サイズ調整モードを使用します。 パフォーマンスを最大にするには、代わりにプログラムによるサイズ変更を使用します。これにより、新しいデータが読み込まれた直後など、特定の時間にサイズを変更できます。  
  
 コンテンツベースの自動サイズ変更モード<xref:System.Windows.Forms.DataGridViewBand.Visible%2A>では、行<xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A> <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> 、列、またはプロパティをに設定する`false`ことによって、非表示になっている行、列、またはヘッダーには影響しません。 たとえば、大きなセル値に合わせて自動的にサイズが変更された後に列が非表示になっている場合、大きなセル値を含む行が削除されると、非表示の列のサイズは変更されません。 自動サイズ変更は、可視性が変更されたとき<xref:System.Windows.Forms.DataGridViewColumn.Visible%2A>には発生`true`しません。そのため、列プロパティをに変更すると、現在のコンテンツに基づいて列のサイズが再計算されません。  
  
 プログラムによるコンテンツベースのサイズ変更は、表示に関係なく、行、列、およびヘッダーに影響します。  
  
## <a name="programmatic-resizing"></a>プログラムによるサイズ変更  
 自動サイズ変更が無効になっている場合は、次のプロパティを使用して、行、列、またはヘッダーの正確な幅または高さをプログラムで設定できます。  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 次の方法を使用して、行、列、ヘッダーのサイズをプログラムによって内容に合わせて変更することもできます。  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 これらのメソッドでは、行、列、またはヘッダーのサイズを、連続したサイズ変更用に構成するのではなく、1回だけ変更します。 新しいサイズは、すべてのセルの内容をクリッピングせずに表示するために自動的に計算されます。 ただし、のプロパティ値を持つ<xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>列の<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>サイズをプログラムで変更する場合、列<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>のプロパティ値を比例して調整するために、計算されたコンテンツベースの幅が使用されます。実際の列の幅は、その後、これらの新しい比率に従って計算され、すべての列がコントロールの使用可能な表示領域に収まるようになります。  
  
 プログラムによるサイズ変更は、継続的なサイズ変更によるパフォーマンスの低下を回避するために役立ちます。 また、ユーザーがサイズ変更可能な行、列、ヘッダー、および列の塗りつぶしモードの初期サイズを指定する場合にも役立ちます。  
  
 通常は、特定のタイミングでプログラムによるサイズ変更メソッドを呼び出します。 たとえば、データを読み込んだ直後にすべての列のサイズをプログラムで変更することも、特定のセルの値が変更された後に特定の行のサイズをプログラムで変更することもできます。  
  
## <a name="customizing-content-based-sizing-behavior"></a>コンテンツベースのサイズ変更動作のカスタマイズ  
 派生<xref:System.Windows.Forms.DataGridView>したセル、行、および列の型を操作するときに、、、 <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>また<xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType>はの各メソッドをオーバーライドするか、派生クラス<xref:System.Windows.Forms.DataGridView>で保護されたサイズ変更メソッドのオーバーロードを呼び出すことによって、サイズ変更動作をカスタマイズできます。制御. 保護されたサイズ変更メソッドのオーバーロードは、ペアで動作するように設計されています。これにより、セルの高さが非常に広くなるのを防ぐことができます。 `AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)`たとえば、 <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>メソッドのオーバーロードを呼び出し、 <xref:System.Boolean>パラメーターにの`false`値を渡すと、オーバーロードによって、行内のセルの理想的な高さと幅が計算されますが、行の高さが調整されます。専用. 次に、 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>メソッドを呼び出して、列の幅を最適な計算結果に調整する必要があります。  
  
## <a name="content-based-sizing-options"></a>コンテンツベースのサイズ変更オプション  
 サイズ変更プロパティとメソッドによって使用される列挙体の値は、コンテンツベースのサイズ変更に似ています。 これらの値を使用すると、どのセルを使用して適切なサイズを計算するかを制限できます。 すべてのサイズ指定の列挙体では、表示されているセルを参照する名前を持つ値は、表示される行のセルに対する計算を制限します。 行を除外すると、大量の行を処理するときにパフォーマンスが低下しないようにするのに役立ちます。 また、ヘッダーまたは nonheader セルのセル値に対して計算を制限することもできます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.Resizable%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeRowsMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>
- <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>
- <xref:System.Windows.Forms.DataGridViewColumnHeadersHeightSizeMode>
- <xref:System.Windows.Forms.DataGridViewRowHeadersWidthSizeMode>
- [Windows フォーム DataGridView コントロール内の列と行のサイズ変更](resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールの列フィル モード](column-fill-mode-in-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム DataGridView コントロールのサイズ変更モードを設定する](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
