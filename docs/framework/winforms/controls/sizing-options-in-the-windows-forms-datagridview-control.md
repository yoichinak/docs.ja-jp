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
ms.openlocfilehash: 1da98dfa58651eca2052f7d180912d1aa2898385
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651971"
---
# <a name="sizing-options-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールのサイズ変更オプション
<xref:System.Windows.Forms.DataGridView> 行、列、およびヘッダーは、多くの異なるオカレンスの結果としてのサイズを変更できます。 次の表では、これらの出現回数を示します。  
  
|見つかった|説明|  
|----------------|-----------------|  
|ユーザーによるサイズ変更|ユーザーは、ドラッグするか、行、列、またはヘッダー区分線をダブルクリックしてサイズ調整を行うことができます。|  
|コントロールのサイズ変更|コントロールの幅が変更されたときの列フィル モードでは、列の幅を変更します。たとえばとユーザーの親フォームにコントロールがドッキングされているときに、フォームがサイズ変更します。|  
|セル値の変更|コンテンツ ベースの自動サイズ変更モードでは、サイズは、新しい表示値に合わせて変更します。|  
|メソッド呼び出し|プログラムによるコンテンツに基づくサイズ変更するには、メソッドの呼び出し時にセルの値に基づく便宜的サイズを調整することができます。|  
|プロパティの設定|特定の高さと幅の値を設定することもできます。|  
  
 既定では、ユーザーによるサイズ変更が有効になっている、自動サイズ設定を無効にすると、およびその列よりも幅がセルの値をクリップします。  
  
 既定の動作を調整するかを特定のサイズ変更オプションを使用して、特定の効果を実現するために使用できるシナリオを次の表に示します。  
  
|シナリオ|実装|  
|--------------|--------------------|  
|表示するため、使用して列フィル モードは、比較的少数の水平スクロール バーを表示せず、コントロールの幅全体を占有する列のデータを同様にサイズ。|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>に設定します。|  
|列フィル モードの使用は、さまざまなサイズの値を表示します。|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>に設定します。 相対的な列の幅を列を設定して初期化<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>プロパティまたはコントロールを呼び出すことによって<xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>データ コントロールのデータを読み込んだ後メソッド。|  
|列フィル モードを使用して、さまざまな重要度の値を使用します。|<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A> プロパティを <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode.Fill>に設定します。 Large 設定<xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>列で常にいくつかのデータの表示や以外のサイズ変更オプションを使用する必要があります塗りつぶしモードの特定の列の値します。|  
|列フィル モードを使用して、コントロールの背景色を表示しないようにします。|設定、<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>する最後の列のプロパティ<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>し、その他の列の他のサイズ変更オプションを使用します。 その他の列が使用の使用可能な領域が多すぎる場合、設定、<xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>最後の列のプロパティ。|  
|アイコンまたは ID 列などの固定長列を表示します。|設定<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>に<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.None>と<xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A>に<xref:System.Windows.Forms.DataGridViewTriState.False>列。 幅を設定して初期化、<xref:System.Windows.Forms.DataGridViewColumn.Width%2A>プロパティまたはコントロールを呼び出すことによって<xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>データ コントロールのデータを読み込んだ後メソッド。|  
|クリッピングを回避するために、領域の使用を最適化するセルの内容が変更されるたびに自動的にサイズを調整します。|コンテンツ ベースのサイズ変更モードを表す値を自動サイズ変更プロパティを設定します。 パフォーマンスの低下を避けるためには、大量のデータを使用する場合、表示されている行のみを計算するサイズ変更モードを使用します。|  
|多くの行を使用する場合は、パフォーマンスの低下を回避するために表示されている行の値に合わせてサイズを調整します。|自動またはプログラムによってサイズ変更に適切なサイズ変更モードの列挙値を使用します。 スクロール中も新しく表示されている行の値に合わせてサイズを調整するサイズ変更メソッドを呼び出して、<xref:System.Windows.Forms.DataGridView.Scroll>イベント ハンドラー。 ユーザーのダブルクリックをカスタマイズするサイズ変更表示されている行の値のみが、新しいサイズを判断できるようにサイズ変更のメソッドを呼び出す、<xref:System.Windows.Forms.DataGridView.RowDividerDoubleClick>または<xref:System.Windows.Forms.DataGridView.ColumnDividerDoubleClick>イベント ハンドラー。|  
|または、パフォーマンスの低下を避けるために、ユーザーによるサイズ変更を有効にする特定の時点でのみセルの内容に合わせてサイズを調整します。|イベント ハンドラーでは、コンテンツ ベースのサイズ変更メソッドを呼び出します。 などを使用して、 <xref:System.Windows.Forms.DataGridView.DataBindingComplete> 、バインドした後にサイズを初期化して処理するイベント、<xref:System.Windows.Forms.DataGridView.CellValidated>または<xref:System.Windows.Forms.DataGridView.CellValueChanged>ユーザー編集または変更を補正するサイズを調整するイベントにバインドされたデータ ソース。|  
|複数行のセルの内容の行の高さを調整します。|列の幅が段落のテキストを表示するために適切であることを確認し、自動またはプログラムによってコンテンツ ベースの行のサイズ変更を使用して、高さを調整します。 使用して複数行のコンテンツを含むセルを表示することも確認、<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>セルのスタイル値<xref:System.Windows.Forms.DataGridViewTriState.True>します。<br /><br /> 通常、列の幅を維持または行の高さを調整する前に特定の値に設定する列の自動サイズ変更モードを使用します。|  
  
## <a name="resizing-with-the-mouse"></a>マウスを使用してサイズ変更  
 既定では、ユーザーは行、列、およびセルの値に基づいて、自動サイズ変更モードを使用してヘッダーをサイズ変更できます。 ユーザーが列フィル モードなど、他のモードでのサイズを変更することを防ぐために、次の 1 つ以上を設定<xref:System.Windows.Forms.DataGridView>プロパティ。  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
 個々 の行または列をサイズ変更を設定してからユーザーを防ぐことができますもその<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>プロパティ。 既定では、<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>プロパティの値がに基づいて、<xref:System.Windows.Forms.DataGridView.AllowUserToResizeColumns%2A>列のプロパティの値と<xref:System.Windows.Forms.DataGridView.AllowUserToResizeRows%2A>行のプロパティの値。 明示的に設定する場合<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>に<xref:System.Windows.Forms.DataGridViewTriState.True>または<xref:System.Windows.Forms.DataGridViewTriState.False>、ただし、コントロールの値がその行または列が、指定した値で上書きされます。 設定<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>に<xref:System.Windows.Forms.DataGridViewTriState.NotSet>継承を復元します。  
  
 <xref:System.Windows.Forms.DataGridViewTriState.NotSet>値の継承を復元、<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>プロパティを返すことは、<xref:System.Windows.Forms.DataGridViewTriState.NotSet>値の行または列に追加されていない場合を除き、<xref:System.Windows.Forms.DataGridView>コントロール。 確認する必要がある場合かどうか、<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>行または列のプロパティの値の継承、確認、<xref:System.Windows.Forms.DataGridViewElement.State%2A>プロパティ。 場合、<xref:System.Windows.Forms.DataGridViewElement.State%2A>値が含まれています、<xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>フラグ、<xref:System.Windows.Forms.DataGridViewBand.Resizable%2A>プロパティの値は継承されません。  
  
## <a name="automatic-sizing"></a>自動サイズ変更  
 自動サイズ変更の 2 種類があります、<xref:System.Windows.Forms.DataGridView>コントロール: 列フィル モードとコンテンツ ベースの自動サイズ変更します。  
  
 列フィル モードでは、コントロールの表示領域の幅に合わせてコントロールで、表示する列が発生します。 このモードの詳細については、次を参照してください。 [Windows フォーム DataGridView コントロールで列の塗りつぶしモード](column-fill-mode-in-the-windows-forms-datagridview-control.md)します。  
  
 行、列、およびヘッダーのサイズに合わせてセルの内容を自動的に調整を構成することもできます。 この場合、サイズ調整は、セルの内容が変更されるたびに発生します。  
  
> [!NOTE]
>  自動サイズ変更には、ユーザーがセルの値を編集しますが、外のキャッシュされた値を変更する場合は発生しないときに発生します仮想モードを使用してカスタム データ キャッシュ内のセル値を保持している場合、<xref:System.Windows.Forms.DataGridView.CellValuePushed>イベント ハンドラー。 この場合、呼び出し、<xref:System.Windows.Forms.DataGridView.UpdateCellValue%2A>セルの表示を更新して、現在の自動サイズ変更モードを適用するコントロールを強制する方法。  
  
 コンテンツ ベースの自動サイズ変更が 1 つのディメンションにのみ有効になっている場合などは、行がない列は、列やがない行を — と<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>も有効になっている、サイズの調整は、その他のディメンションが変更されるたびにも発生します。 たとえば、次の行がない列が自動サイズ変更用に構成されたと<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>が有効にすると、ユーザーが列の幅を変更する列の区分線をドラッグでき、行の高さは、セルの内容が完全に表示されるよう自動的に調整します。  
  
 行と列のコンテンツ ベースの自動サイズ設定の両方を構成する場合と<xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A>が有効になって、<xref:System.Windows.Forms.DataGridView>セルの内容が変更され、新しいサイズを計算するときに、理想的なセルの高さと幅の比率を使用するたびに、コントロールのサイズは調整します。  
  
 次の 1 つ以上設定とコントロールの値をオーバーライドしない列のヘッダーと行のサイズ変更モードを構成するには、<xref:System.Windows.Forms.DataGridView>プロパティ。  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeightSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidthSizeMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoSizeRowsMode%2A>  
  
 個々 の列のコントロールの列のサイズ変更モードを無効にする次のように設定します。 その<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>プロパティ以外の値を<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>します。 列のサイズ変更モードが実際に続くその<xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>プロパティ。 このプロパティの値が列のに基づいて<xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>プロパティ値の値がない限り<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.NotSet>その場合、コントロールの<xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>値が継承されます。  
  
 コンテンツに基づく自動サイズ変更には注意大量のデータを使用する場合に使用します。 パフォーマンスの低下を回避するには、コントロール内のすべての行を分析するのではなく、表示されている行のみに基づくサイズを計算する自動サイズ変更モードを使用します。 最高のパフォーマンスを使用してプログラムによるサイズ変更代わりにするため、サイズを変更する特定の時点でなど直後に新しいデータが読み込まれます。  
  
 コンテンツ ベースの自動サイズ変更モードには影響しません、行、列、またはヘッダー行または列を設定して非表示にした<xref:System.Windows.Forms.DataGridViewBand.Visible%2A>プロパティまたはコントロール<xref:System.Windows.Forms.DataGridView.RowHeadersVisible%2A>または<xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A>プロパティ`false`します。 たとえば、大規模なセル値に合わせてサイズが自動的にその後、列を非表示の場合非表示の列は変更されませんのサイズの大きなセル値を含む行が削除された場合。 可視性が変更されたときに、自動サイズ変更は発生しませんので、列を変更する<xref:System.Windows.Forms.DataGridViewColumn.Visible%2A>プロパティ`true`現在の内容に基づいてサイズを再計算することを強制しません。  
  
 行、列、およびヘッダーの可視性に関係なく、プログラムによるコンテンツに基づくサイズ変更に影響します。  
  
## <a name="programmatic-resizing"></a>プログラムによるサイズ変更  
 自動サイズ設定を無効にすると、実際の幅または行、列、または、次のプロパティでヘッダーの高さをプログラムで設定できます。  
  
- <xref:System.Windows.Forms.DataGridView.RowHeadersWidth%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersHeight%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewRow.Height%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=nameWithType>  
  
 行、列、および、次のメソッドを使用してその内容に合わせてヘッダー サイズを変更することができますもプログラムで。  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumn%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeColumnHeadersHeight%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRow%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>  
  
- <xref:System.Windows.Forms.DataGridView.AutoResizeRowHeadersWidth%2A>  
  
 これらのメソッドは、行、列、またはヘッダーを 1 回ではなく継続的なサイズ変更するための構成にサイズ変更されます。 クリッピングなしすべてのセルの内容を表示する新しいサイズが自動的に計算します。 ときにプログラムでサイズを変更する列を持つ<xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>プロパティの値を<xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode.Fill>、ただし、計算のコンテンツ ベースの幅を使用すると、列を比例的に調整<xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>プロパティ値、および幅は、実際には列すべての列は、コントロールの使用可能な表示領域を入力できるようにこれらの新しい比率に従って計算されます。  
  
 プログラムによるサイズ変更は、継続的なサイズの変更によるパフォーマンス低下を回避するために便利です。 初期サイズを使用して、ユーザーのサイズ変更可能な行、列、およびヘッダーと列フィル モードに便利です。  
  
 通常は特定の時点でプログラムによるサイズ変更メソッドを呼び出します。 たとえば、データの読み込み後すぐにすべての列をプログラムでサイズ可能性があります。 または特定のセル値が変更された後にプログラムで特定の行サイズ可能性があります。  
  
## <a name="customizing-content-based-sizing-behavior"></a>コンテンツ ベースのサイズ変更動作をカスタマイズします。  
 派生を使用する場合は、サイズ変更動作をカスタマイズすることができます<xref:System.Windows.Forms.DataGridView>セル、行、および列の種類をオーバーライドすることで、 <xref:System.Windows.Forms.DataGridViewCell.GetPreferredSize%2A?displayProperty=nameWithType>、 <xref:System.Windows.Forms.DataGridViewRow.GetPreferredHeight%2A?displayProperty=nameWithType>、または<xref:System.Windows.Forms.DataGridViewColumn.GetPreferredWidth%2A?displayProperty=nameWithType>メソッドを呼び出して、派生でサイズ変更メソッドのオーバー ロードを保護または<xref:System.Windows.Forms.DataGridView>コントロール。 保護対象のサイズ変更メソッドのオーバー ロードは、理想的なセルの高さと幅を過度に幅または高さのセルの回避の比率を実現するためにペアで作業する設計されています。 呼び出す場合など、`AutoResizeRows(DataGridViewAutoSizeRowsMode,Boolean)`のオーバー ロード、<xref:System.Windows.Forms.DataGridView.AutoResizeRows%2A>メソッドとの値を渡します`false`の<xref:System.Boolean>パラメーター オーバー ロードは、最適な高さと、行内のセルの幅を計算するが、行の高さが調整されますのみです。 呼び出す必要がありますし、<xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>計算理想に列の幅を調整する方法。  
  
## <a name="content-based-sizing-options"></a>コンテンツ ベースのサイズ変更オプション  
 サイズ変更プロパティおよびメソッドで使用される列挙体では、コンテンツ ベースのサイズ変更と同様の値があります。 これらの値では、適切なサイズの計算に使用するセルを制限できます。 すべてのサイズ変更の列挙、表示されているセルを参照する名前を持つ値は表示されている行のセルに、計算を制限します。 行の除外は、大量の行を使用する場合、パフォーマンスの低下を回避するために便利です。 計算またはヘッダー以外のセルのセルの値を制限することもできます。  
  
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
- [方法: Windows フォーム DataGridView コントロールのサイズ変更モードを設定します。](how-to-set-the-sizing-modes-of-the-windows-forms-datagridview-control.md)
