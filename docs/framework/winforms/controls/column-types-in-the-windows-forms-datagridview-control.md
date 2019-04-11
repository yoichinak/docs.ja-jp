---
title: Windows フォーム DataGridView コントロールの列型
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], types
- DataGridView control [Windows Forms], column types
- data grids [Windows Forms], columns
ms.assetid: f0a0a9f1-8757-4bfd-891f-d7d12870dbed
ms.openlocfilehash: a33cf4cd865921c04ef10c7fccf3a67c3d22de73
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115675"
---
# <a name="column-types-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールの列型
<xref:System.Windows.Forms.DataGridView>コントロールがその情報を表示したり変更したり、情報を追加するユーザーを有効にするためにいくつかの列の型を使用します。  
  
 バインドすると、<xref:System.Windows.Forms.DataGridView>を制御し、設定、<xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A>プロパティを`true`列は、バインドされたデータ ソースに含まれるデータ型の適切な既定の列型を使用して自動的に生成されます。  
  
 自分で任意の列のクラスのインスタンスを作成し、によって返されるコレクションに追加することができますも、<xref:System.Windows.Forms.DataGridView.Columns%2A>プロパティ。 非バインド列として使用するため、これらのインスタンスを作成するか、手動でバインドすることができます。 手動でバインドされた列は、別の型の列を含む 1 つの型の自動的に生成された列を置換するときなどに便利です。  
  
 次の表に、さまざまな列クラスで使用できる、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
|クラス|説明|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|テキスト ベースの値と共に使用します。 数値や文字列にバインドするときに自動的に生成されます。|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|併用<xref:System.Boolean>と<xref:System.Windows.Forms.CheckState>値。 これらの型の値にバインドするときに自動的に生成されます。|  
|<xref:System.Windows.Forms.DataGridViewImageColumn>|イメージを表示するために使用します。 バイト配列にバインドするときに自動的に生成された<xref:System.Drawing.Image>オブジェクト、または<xref:System.Drawing.Icon>オブジェクト。|  
|<xref:System.Windows.Forms.DataGridViewButtonColumn>|セルにボタンを表示するために使用します。 バインドするときに自動的に生成されます。 通常、バインドされていない列として使用します。|  
|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|セルのドロップダウン リストを表示するために使用します。 バインドするときに自動的に生成されます。 通常、データ バインド手動でします。|  
|<xref:System.Windows.Forms.DataGridViewLinkColumn>|セル内のリンクを表示するために使用します。 バインドするときに自動的に生成されます。 通常、データ バインド手動でします。|  
|カスタム列の型|列の独自のクラスを作成するには継承することによって、<xref:System.Windows.Forms.DataGridViewColumn>クラスまたはカスタムの外観、動作、またはホストされるコントロールを提供する派生クラスのいずれか。 詳細については、「[方法 :それぞれの動作と外観を拡張することによって、セルと、Windows フォーム DataGridView コントロール内の列をカスタマイズします。](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)|  
  
 これらの列型は、次のセクションで詳しく説明します。  
  
## <a name="datagridviewtextboxcolumn"></a>[Datagridviewtextboxcolumn]  
 <xref:System.Windows.Forms.DataGridViewTextBoxColumn>は数値や文字列などのテキスト ベースの値で使用するための汎用の列の型です。 編集モードで、<xref:System.Windows.Forms.TextBox>セル値を変更するユーザーを有効にすると、アクティブなセルに、コントロールが表示されます。  
  
 セルの値は、表示する文字列を自動的に変換されます。 値を入力またはユーザーによって変更が自動的に適切なデータ型のセル値を作成する解析されます。 これらの変換をカスタマイズするには処理することによって、<xref:System.Windows.Forms.DataGridView.CellFormatting>と<xref:System.Windows.Forms.DataGridView.CellParsing>のイベント、<xref:System.Windows.Forms.DataGridView>コントロール。  
  
 列のセル値のデータ型がで指定された、<xref:System.Windows.Forms.DataGridViewColumn.ValueType%2A>列のプロパティ。  
  
## <a name="datagridviewcheckboxcolumn"></a>DataGridViewCheckBoxColumn  
 <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>併用<xref:System.Boolean>と<xref:System.Windows.Forms.CheckState>値。 <xref:System.Boolean> 値の値に応じて、2 つの状態または 3 つの状態のチェック ボックスとして表示、<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>プロパティ。 列のバインド時<xref:System.Windows.Forms.CheckState>値、<xref:System.Windows.Forms.DataGridViewCheckBoxColumn.ThreeState%2A>プロパティの値が`true`既定では。  
  
 通常などその他のデータ記憶域をまたは一括操作を実行するために、チェック ボックス セルの値が想定しては。 処理することができます チェック ボックス セルをクリックすると、ときにすぐに応答する場合、<xref:System.Windows.Forms.DataGridView.CellClick>セルの値を更新する前に、イベントがこのイベントが発生します。 1 つのオプションが予期される値を計算するにはクリックの時に新しい値が必要な場合、現在の値に基づきます。 別の方法がすぐに、変更をコミットして処理するには、<xref:System.Windows.Forms.DataGridView.CellValueChanged>それに応答するイベントです。 セルがクリックされたときに、変更をコミットするに処理する必要があります、<xref:System.Windows.Forms.DataGridView.CurrentCellDirtyStateChanged>イベント。 ハンドラーで、現在のセルがチェック ボックス セルの場合を呼び出す、<xref:System.Windows.Forms.DataGridView.CommitEdit%2A>メソッドを渡します、<xref:System.Windows.Forms.DataGridViewDataErrorContexts.Commit>値。  
  
## <a name="datagridviewimagecolumn"></a>DataGridViewImageColumn  
 <xref:System.Windows.Forms.DataGridViewImageColumn>イメージを表示するために使用します。 イメージの列がデータ ソースから自動的に設定、バインドされていない列は、手動で設定されますまたはのハンドラーで動的に読み込まれる、<xref:System.Windows.Forms.DataGridView.CellFormatting>イベント。  
  
 さまざまなイメージ形式でサポートされるすべての形式でバイト配列を image 列のデータ ソースからの自動作成の動作、<xref:System.Drawing.Image>クラスと Microsoft® アクセスと、Northwind サンプル データベースで使用される OLE 画像形式。  
  
 機能を提供する場合に便利ですが image 列を手動で設定を<xref:System.Windows.Forms.DataGridViewButtonColumn>、カスタマイズされた外観を持つが、します。 処理することができます、<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>画像セル内で数回のクリックに応答するイベントです。  
  
 ハンドラーで image 列のセルを設定、<xref:System.Windows.Forms.DataGridView.CellFormatting>イベントは、イメージ以外の形式で計算される値または値のイメージを提供したい場合に便利です。 たとえば、文字列値を持つ「リスク」の列をなどにある可能性があります`"high"`、 `"middle"`、および`"low"`アイコンとして表示します。 または、画像のバイナリ コンテンツではなく読み込む必要があるイメージの位置を含む「イメージ」列がある可能性があります。  
  
## <a name="datagridviewbuttoncolumn"></a>DataGridViewButtonColumn  
 <xref:System.Windows.Forms.DataGridViewButtonColumn>ボタンが含まれているセルの列を表示することができます。 これは、ユーザーが注文や別のウィンドウに子レコードを表示するなど、特定のレコードに対してアクションを実行するための簡単な方法を提供したい場合に便利です。  
  
 データ バインディング時にボタンの列は自動的に生成されません、<xref:System.Windows.Forms.DataGridView>コントロール。 ボタン列を使用するには、手動で作成し、によって返されるコレクションに追加する必要があります、<xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>プロパティ。  
  
 処理することによりボタン セル内のユーザーのクリックに応答できる、<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>イベント。  
  
## <a name="datagridviewcomboboxcolumn"></a>DataGridViewComboBoxColumn  
 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>、ドロップダウン リスト ボックスが含まれているセルの列を表示することができます。 これは、Northwind サンプル データベースの Products テーブルのカテゴリ列などの特定の値を含めることができますのみフィールドでのデータ入力に役立ちます。  
  
 すべてのセルの設定と同じ方法で使用するドロップダウン リストを設定することができます、<xref:System.Windows.Forms.ComboBox>によって返されるコレクションを手動でいずれか、ドロップダウン リスト、<xref:System.Windows.Forms.DataGridViewComboBoxColumn.Items%2A>プロパティ、またはデータ ソースにバインドして、 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A>、 <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DisplayMember%2A>、および<xref:System.Windows.Forms.DataGridViewComboBoxColumn.ValueMember%2A>プロパティ。 詳細については、次を参照してください。 [ComboBox コントロール](combobox-control-windows-forms.md)します。  
  
 によって使用されるデータ ソースに実際のセル値をバインドすることができます、<xref:System.Windows.Forms.DataGridView>コントロールを設定して、<xref:System.Windows.Forms.DataGridViewColumn.DataPropertyName%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewComboBoxColumn?displayProperty=nameWithType>します。  
  
 データ バインディング、コンボ ボックスの列が自動的に生成されませんが、<xref:System.Windows.Forms.DataGridView>コントロール。 コンボ ボックスの列を使用するには、手動で作成およびによって返されるコレクションに追加する必要があります、<xref:System.Windows.Forms.DataGridView.Columns%2A>プロパティ。  
  
## <a name="datagridviewlinkcolumn"></a>DataGridViewLinkColumn  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>ハイパーリンクを含むセルの列を表示することができます。 これは URL の値で、データ ソースまたは子レコードを含むウィンドウを開くなどの特殊な動作のボタン列の代替として役立ちます。  
  
 データ バインディング時に列のリンクは自動的に生成されません、<xref:System.Windows.Forms.DataGridView>コントロール。 リンク列を使用するには、手動で作成し、によって返されるコレクションに追加する必要があります、<xref:System.Windows.Forms.DataGridView.Columns%2A>プロパティ。  
  
 処理することによってリンク上のユーザーのクリックに応答できる、<xref:System.Windows.Forms.DataGridView.CellContentClick>イベント。 このイベントは、異なる、<xref:System.Windows.Forms.DataGridView.CellClick>と<xref:System.Windows.Forms.DataGridView.CellMouseClick>イベントで、ユーザーがセルの任意の場所をクリックしたときに発生します。  
  
 <xref:System.Windows.Forms.DataGridViewLinkColumn>クラスでは、いくつかのプロパティを提供する前に、中、および後へのリンクの外観を変更するためをクリックします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn>
- <xref:System.Windows.Forms.DataGridViewButtonColumn>
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>
- <xref:System.Windows.Forms.DataGridViewImageColumn>
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>
- <xref:System.Windows.Forms.DataGridViewLinkColumn>
- [DataGridView コントロール](datagridview-control-windows-forms.md)
- [方法: Windows フォーム DataGridView コントロールのセルにイメージを表示する](how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)
- [方法: Windows フォーム DataGridView コントロールのイメージ列を操作する](how-to-work-with-image-columns-in-the-windows-forms-datagridview-control.md)
- [Windows フォーム DataGridView コントロールのカスタマイズ](customizing-the-windows-forms-datagridview-control.md)
