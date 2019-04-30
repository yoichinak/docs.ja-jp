---
title: 既定のキーボードとマウスの Windows フォーム DataGridView コントロールでの処理
ms.date: 02/13/2018
helpviewer_keywords:
- data grids [Windows Forms], mouse handling
- DataGridView control [Windows Forms], navigation keys
- keyboards [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], keyboard handling
- mouse [Windows Forms], default handling in DataGridView control
- DataGridView control [Windows Forms], mouse handling
- navigation keys [Windows Forms], DataGridView control
ms.assetid: 4519b928-bfc8-4e8b-bb9c-b1e76a0ca552
ms.openlocfilehash: 56585bf91a559844f15aede4519706674357a924
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011347"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>既定のキーボードとマウスの Windows フォーム DataGridView コントロールでの処理

次の表では、ユーザーの対話方法について説明します、<xref:System.Windows.Forms.DataGridView>キーボード、マウスを使用してコントロール。  
  
> [!NOTE]
>  キーボードの動作をカスタマイズすることがイベントを処理する標準のキーボードなど<xref:System.Windows.Forms.Control.KeyDown>します。 編集モードで、ただし、ホストされる編集コントロール、キーボード入力を受け取るし、キーボード イベントについては行われません、<xref:System.Windows.Forms.DataGridView>コントロール。 編集コントロールのイベントを処理するために、ハンドラーの編集コントロールをアタッチ、<xref:System.Windows.Forms.DataGridView.EditingControlShowing>イベント ハンドラー。 またはでのキーボード動作をカスタマイズすることができます、<xref:System.Windows.Forms.DataGridView>サブクラスをオーバーライドすることで、<xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A>と<xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A>メソッド。  
  
## <a name="default-keyboard-handling"></a>既定のキーボード処理  
  
### <a name="basic-navigation-and-entry-keys"></a>基本的なナビゲーションとエントリのキー  
  
|キーまたはキーの組み合わせ|説明|  
|----------------------------|-----------------|  
|↓|現在のセルの直下のセルにフォーカスを移動します。 最後の行にフォーカスがある場合は、何も行われません。|  
|←|行の前のセルにフォーカスを移動します。 行の最初のセルにフォーカスがある場合は、何も行われません。|  
|→|次の行のセルにフォーカスを移動します。 行の最後のセルにフォーカスがある場合は、何も行われません。|  
|↑|現在のセルのすぐ上のセルにフォーカスを移動します。 最初の行にフォーカスがある場合は、何も行われません。|  
|ホーム|現在の行の最初のセルにフォーカスを移動します。|  
|End|現在の行の最後のセルにフォーカスを移動します。|  
|PAGE DOWN|完全に表示されている行の数によって、コントロールを下をスクロールします。 最後に完全に表示されている行に列を変更することがなく、フォーカスを移動します。|  
|PAGE UP|コントロールを完全に表示される行の数、スクロールします。 列を変更することがなく表示される最初の行にフォーカスを移動します。|  
|Tab|場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`false`、現在の行の次のセルにフォーカスを移動します。 行の最後のセルにフォーカスがある場合は、次の行の最初のセルにフォーカスを移動します。 コントロール内の最後のセルにフォーカスがある場合は、親コンテナーのタブ オーダー内で次のコントロールにフォーカスを移動します。<br /><br /> 場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`true`、親コンテナーのタブ オーダーの次のコントロールにフォーカスを移動します。|  
|Shift + Tab|場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`false`、現在の行の前のセルにフォーカスを移動します。 行の最初のセルにフォーカスがある場合は、前の行の最後のセルにフォーカスを移動します。 コントロール内の最初のセルにフォーカスがある場合は、親コンテナーのタブ オーダー内で前のコントロールにフォーカスを移動します。<br /><br /> 場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`true`、親コンテナーのタブ オーダー内で前のコントロールにフォーカスを移動します。|  
|Ctrl + Tab|場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`false`、親コンテナーのタブ オーダーの次のコントロールにフォーカスを移動します。<br /><br /> 場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`true`、現在の行の次のセルにフォーカスを移動します。 行の最後のセルにフォーカスがある場合は、次の行の最初のセルにフォーカスを移動します。 コントロール内の最後のセルにフォーカスがある場合は、親コンテナーのタブ オーダー内で次のコントロールにフォーカスを移動します。|  
|Ctrl + Shift + Tab|場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`false`、親コンテナーのタブ オーダー内で前のコントロールにフォーカスを移動します。<br /><br /> 場合、<xref:System.Windows.Forms.DataGridView.StandardTab%2A>プロパティの値が`true`、現在の行の前のセルにフォーカスを移動します。 行の最初のセルにフォーカスがある場合は、前の行の最後のセルにフォーカスを移動します。 コントロール内の最初のセルにフォーカスがある場合は、親コンテナーのタブ オーダー内で前のコントロールにフォーカスを移動します。|  
|CTRL + 方向キー|矢印の方向の一番下のセルにフォーカスを移動します。|  
|Ctrl + Home|コントロールの最初のセルにフォーカスを移動します。|  
|Ctrl + End|コントロールの最後のセルにフォーカスを移動します。|  
|CTRL + ページ/アップ ダウン|ページの下またはページの上と同じです。|  
|F2|現在のセルを編集モードのセルには場合、<xref:System.Windows.Forms.DataGridView.EditMode%2A>プロパティの値が<xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2>または<xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>します。|
|F3|現在の列を並べ替える場合、<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>プロパティの値が<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>します。 現在の列ヘッダーをクリックすると同じです。 .NET Framework 4.7.2 以降で使用可能です。 この機能を有効にするのには、アプリケーションは .NET Framework 4.7.2 以降のバージョンを対象または AppContext スイッチを使用してアクセシビリティ機能改善を明示的に選択する必要があります。|  
|F4|現在のセルがある場合、<xref:System.Windows.Forms.DataGridViewComboBoxCell>をセルを編集モードに配置し、ドロップダウン リストを表示します。|  
|ALT + ↑ または ↓|現在のセルがある場合、<xref:System.Windows.Forms.DataGridViewComboBoxCell>をセルを編集モードに配置し、ドロップダウン リストを表示します。|  
|Space|現在のセルがある場合、 <xref:System.Windows.Forms.DataGridViewButtonCell>、 <xref:System.Windows.Forms.DataGridViewLinkCell>、または<xref:System.Windows.Forms.DataGridViewCheckBoxCell>、発生させる、<xref:System.Windows.Forms.DataGridView.CellClick>と<xref:System.Windows.Forms.DataGridView.CellContentClick>イベント。 現在のセルがある場合、 <xref:System.Windows.Forms.DataGridViewButtonCell>、また、ボタンを押します。 現在のセルがある場合、<xref:System.Windows.Forms.DataGridViewCheckBoxCell>もチェックの状態を変更します。|  
|Enter|現在のセルと行に変更をコミットし、現在のセルの直下のセルにフォーカスを移動します。 最後の行にフォーカスがある場合は、フォーカスを移動せず、変更をコミットします。|  
|Esc|コントロールが編集モードにある場合は、編集をキャンセルします。 編集モードでコントロールがない場合は、コントロールが編集をサポートするデータ ソースにバインドされている場合に、現在の行に加えられた変更を元に戻します。 または行レベルのコミットのスコープを持つ仮想モードが実装されています。|  
|BACKSPACE キー|セルを編集するときに、挿入ポイントの前に文字を削除します。|  
|Del|セルを編集するときに、カーソル位置の後の文字を削除します。|  
|Ctrl + Enter|現在のセルにフォーカスを移動せず、変更をコミットします。 コミットで、コントロールが編集または仮想モードをサポートするデータ ソースにバインドされている場合は、現在の行への変更が実装されて行レベルのコミットのスコープ。|  
|Ctrl + 0|入力、<xref:System.DBNull.Value?displayProperty=nameWithType>を現在のセルに値の場合は、セルを編集することができます。 既定では、値の表示、<xref:System.DBNull>セルの値は、の値、<xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellStyle>現在のセルに対して有効な。|  
  
### <a name="selection-keys"></a>キーの選択

 場合、<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>プロパティに設定されて`false`と<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>プロパティに設定されて<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>、新しいセルに、選択を変更するナビゲーション キーを使用して現在のセルを変更します。 SHIFT、ctrl キー、および alt の各キーは、この動作は影響しません。  
  
 場合、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>に設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>、同じ動作が発生しますが、次の項目を追加します。  
  
|キーまたはキーの組み合わせ|説明|  
|----------------------------|-----------------|  
|SHIFT キーを押しながら SPACE キー|完全な行または列 (行または列ヘッダーをクリックすると同じ) を選択します。|  
|ナビゲーション キー (矢印、ページの上下 HOME、END)|完全な行または列が選択されている場合、新しい行または列に現在のセルを変更するを完全に新しい行または列 (選択モード) に応じて選択範囲に移動します。|  
  
 場合<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>に設定されている`false`と<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>に設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>、選択範囲を完全に新しい行または列に移動、キーボードを使用して新しい行または列に現在のセルを変更します。 SHIFT、ctrl キー、および alt の各キーは、この動作は影響しません。  
  
 場合<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>に設定されている`true`ナビゲーションの動作は変わりませんが、複数のセルの選択が変更されます (CTRL + SHIFT を含む) shift キーを押しながらキーボードでナビゲートします。 ナビゲーションが開始する前に、コントロールは、現在のセルをアンカー セルとしてマークします。 Shift キーを押しながら移動すると、選択範囲にはアンカー セルに、現在のセル間のすべてのセルが含まれます。 コントロールの他のセルは、既に選択されている、キーボード ナビゲーションが一時的にアンカー セルと現在のセルの場合は、選択されていない、なる可能性がある場合、選択した保持されます。  
  
 場合<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>に設定されている`true`と<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>に設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>アンカー セルと現在のセルの動作は同じが完全な行や列だけになる選択または選択解除します。  
  
## <a name="default-mouse-handling"></a>既定のマウス処理
  
### <a name="basic-mouse-handling"></a>基本的なマウス処理
  
> [!NOTE]
>  マウスの左ボタンでセルをクリックすると、常に現在のセルを変更します。 セルをマウスの右ボタンでクリックすると、いずれかが使用可能な場合、ショートカット メニューが開きます。  
  
|マウス操作|説明|  
|------------------|-----------------|  
|マウスの左ボタンを押す|セルがクリックされた現在のセルは、させ、<xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType>イベント。|  
|マウスの左ボタン|<xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> イベントを発生させます。|  
|マウスの左ボタンをクリックします|発生させる、<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>と<xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType>イベント|  
|マウスの左ボタンを押す、および列ヘッダー セルにドラッグ|場合、<xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>プロパティは`true`、新しい位置に削除するように、列を移動します。|  
  
### <a name="mouse-selection"></a>マウスの選択

 選択の動作は、マウスの中央ボタンまたはマウス ホイール関連付けではありません。  
  
 場合、<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>プロパティに設定されて`false`と<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>プロパティに設定されて<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>、次の動作が発生します。  
  
|マウス操作|説明|  
|------------------|-----------------|  
|マウスの左ボタンをクリックします。|ユーザーがセルをクリックした場合は、現在のセルのみを選択します。 動作はありません選択場合は、ユーザーが行または列ヘッダーをクリックします。|  
|マウスの右ボタンをクリックします。|1 つが使用可能な場合は、ショートカット メニューを表示します。|  
  
 同じ動作が発生したときに、<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>に設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>選択モードに応じて行または列見出しをクリックしては完全な行または列を選択し、行または列の最初のセルに現在のセルを設定点を除き、します。  
  
 場合<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>に設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>、行または列の任意のセルをクリックすると行全体または列を選択します。  
  
 場合<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>に設定されている`true`、ctrl キーまたは shift キーを押しながらセルをクリックすると、複数のセルの選択が変更されます。  
  
 CTRL キーを押しながらセルをクリックすると、セルは、その他のすべてのセルが現在の選択状態を保持の選択状態を変更します。  
  
 Shift キーを押しながらセルまたは一連のセルをクリックすると、選択範囲には、現在のセルとセルの最初のクリックする前に現在のセルの位置にあるアンカー セル間のすべてのセルが含まれています。 クリックして、複数のセルにポインターをドラッグして、ときにアンカー セルに、ドラッグ操作の開始時にクリックしてセルです。 Shift キーを押しながら後続数回のクリックは、現在のセルがないのアンカー セルに変更します。 コントロールの他のセルは、既に選択されているが、マウスのナビゲーションは一時的にアンカー セルと現在のセルの場合は、選択されていない、なる可能性がある場合、選択した保持されます。  
  
 場合<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>に設定されている`true`と<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>に設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>、このような場合、完全な行または列の既存の選択を変更は shift キーを押しながら (選択モード) に応じて、行または列ヘッダーをクリックすると、選択範囲が存在します。 それ以外の場合、選択を解除され、完全な行または列の新しい選択範囲の開始。 CTRL キーを押しながら行または列ヘッダーをクリックすると、ただしを追加またはそれ以外の場合、現在の選択を変更することがなく、現在の選択項目から、クリックされた行または列を削除します。  
  
 場合<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>に設定されている`true`と<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>に設定されている<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>または<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>列が影響を受ける、shift キーまたは CTRL を押しながらセルをクリックするとその完全のみの行を除く同様に動作します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView コントロール](datagridview-control-windows-forms.md)
