---
title: Windows フォーム DataGridView コントロールでの既定のキーボード操作とマウス処理
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
ms.openlocfilehash: 97b8c8c3e418586bbc0053c358a2924484115a26
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969127"
---
# <a name="default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールでの既定のキーボード操作とマウス処理

次の表では、ユーザーがキーボードと<xref:System.Windows.Forms.DataGridView>マウスを使用してコントロールを操作する方法について説明します。  
  
> [!NOTE]
> キーボードの動作をカスタマイズするには、などの標準<xref:System.Windows.Forms.Control.KeyDown>のキーボードイベントを処理します。 ただし、編集モードでは、ホストされている編集コントロールはキーボード入力を受け取り、キーボードイベントは<xref:System.Windows.Forms.DataGridView>コントロールに対して発生しません。 コントロールイベントの編集を処理するには、ハンドラーを<xref:System.Windows.Forms.DataGridView.EditingControlShowing>イベントハンドラーの編集コントロールにアタッチします。 または、メソッド<xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.DataGridView.ProcessDialogKey%2A>と<xref:System.Windows.Forms.DataGridView.ProcessDataGridViewKey%2A>メソッドをオーバーライドして、サブクラスのキーボード動作をカスタマイズすることもできます。  
  
## <a name="default-keyboard-handling"></a>既定のキーボード処理  
  
### <a name="basic-navigation-and-entry-keys"></a>基本的なナビゲーションキーとエントリキー  
  
|キーまたはキーの組み合わせ|説明|  
|----------------------------|-----------------|  
|↓|フォーカスを現在のセルのすぐ下のセルに移動します。 フォーカスが最後の行にある場合、は何も行いません。|  
|←|フォーカスを行の前のセルに移動します。 フォーカスが行の最初のセルにある場合、は何も行いません。|  
|→|フォーカスを行の次のセルに移動します。 フォーカスが行の最後のセルにある場合、は何も行いません。|  
|↑|フォーカスを現在のセルのすぐ上のセルに移動します。 フォーカスが最初の行にある場合、は何も行いません。|  
|Home|フォーカスを現在の行の最初のセルに移動します。|  
|END|フォーカスを現在の行の最後のセルに移動します。|  
|PageDown|コントロールを、完全に表示されている行の数だけ下にスクロールします。 列を変更せずに、最後に表示された行にフォーカスを移動します。|  
|PageUp|コントロールを、完全に表示されている行の数だけ上にスクロールします。 列を変更せずに、最初に表示された行にフォーカスを移動します。|  
|Tab|プロパティ値が`false`の場合は、現在の行の次のセルにフォーカスを移動します。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> フォーカスが行の最後のセルに既に存在する場合、は、フォーカスを次の行の最初のセルに移動します。 フォーカスがコントロールの最後のセルにある場合、は親コンテナーのタブオーダーで次のコントロールにフォーカスを移動します。<br /><br /> プロパティ値が`true`の場合、親コンテナーのタブオーダーの次のコントロールにフォーカスを移動します。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A>|  
|Shift + Tab|プロパティ値が`false`の場合は、現在の行の前のセルにフォーカスを移動します。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> フォーカスが既に行の最初のセルにある場合、は、前の行の最後のセルにフォーカスを移動します。 フォーカスがコントロールの最初のセルにある場合、は親コンテナーのタブオーダーで前のコントロールにフォーカスを移動します。<br /><br /> プロパティ値が`true`の場合は、親コンテナーのタブオーダーで前のコントロールにフォーカスを移動します。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A>|  
|Ctrl + Tab|プロパティ値が`false`の場合、親コンテナーのタブオーダーの次のコントロールにフォーカスを移動します。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A><br /><br /> プロパティ値が`true`の場合は、現在の行の次のセルにフォーカスを移動します。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> フォーカスが行の最後のセルに既に存在する場合、は、フォーカスを次の行の最初のセルに移動します。 フォーカスがコントロールの最後のセルにある場合、は親コンテナーのタブオーダーで次のコントロールにフォーカスを移動します。|  
|Ctrl + Shift + Tab|プロパティ値が`false`の場合は、親コンテナーのタブオーダーで前のコントロールにフォーカスを移動します。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A><br /><br /> プロパティ値が`true`の場合は、現在の行の前のセルにフォーカスを移動します。 <xref:System.Windows.Forms.DataGridView.StandardTab%2A> フォーカスが既に行の最初のセルにある場合、は、前の行の最後のセルにフォーカスを移動します。 フォーカスがコントロールの最初のセルにある場合、は親コンテナーのタブオーダーで前のコントロールにフォーカスを移動します。|  
|CTRL + 方向キー|矢印の方向にある最も遠いセルにフォーカスを移動します。|  
|Ctrl + Home|フォーカスをコントロールの最初のセルに移動します。|  
|Ctrl + End|フォーカスをコントロール内の最後のセルに移動します。|  
|CTRL + PAGEDOWN/UP|PAGEUP または pageup と同じです。|  
|F2|<xref:System.Windows.Forms.DataGridView.EditMode%2A>プロパティ値が<xref:System.Windows.Forms.DataGridViewEditMode.EditOnF2>または<xref:System.Windows.Forms.DataGridViewEditMode.EditOnKeystrokeOrF2>の場合、現在のセルをセル編集モードにします。|
|F3|<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>プロパティ値が<xref:System.Windows.Forms.DataGridViewColumnSortMode.Automatic>の場合、現在の列を並べ替えます。 これは、現在の列ヘッダーをクリックした場合と同じです。 .NET Framework 4.7.2 以降で使用できます。 この機能を有効にするには、アプリケーションで .NET Framework 4.7.2 以降のバージョンを対象にするか、AppContext スイッチを使用してユーザー補助機能の強化を明示的に選択する必要があります。|  
|F4|現在のセルがの<xref:System.Windows.Forms.DataGridViewComboBoxCell>場合は、セルを編集モードにし、ドロップダウンリストを表示します。|  
|ALT + ↑/↓|現在のセルがの<xref:System.Windows.Forms.DataGridViewComboBoxCell>場合は、セルを編集モードにし、ドロップダウンリストを表示します。|  
|Space|現在のセルが<xref:System.Windows.Forms.DataGridViewButtonCell>、 <xref:System.Windows.Forms.DataGridViewLinkCell>、または<xref:System.Windows.Forms.DataGridViewCheckBoxCell>の場合は、 <xref:System.Windows.Forms.DataGridView.CellClick>イベント<xref:System.Windows.Forms.DataGridView.CellContentClick>とイベントを発生させます。 現在のセルがの<xref:System.Windows.Forms.DataGridViewButtonCell>場合は、もボタンを押します。 現在のセルがの<xref:System.Windows.Forms.DataGridViewCheckBoxCell>場合は、もチェックの状態を変更します。|  
|Enter|現在のセルと行に対するすべての変更をコミットし、現在のセルのすぐ下にあるセルにフォーカスを移動します。 フォーカスが最後の行にある場合、はフォーカスを移動せずにすべての変更をコミットします。|  
|Esc|コントロールが編集モードの場合は、編集をキャンセルします。 コントロールが編集モードでない場合、は、編集をサポートするデータソースにコントロールがバインドされているか、行レベルのコミットスコープで仮想モードが実装されている場合に、現在の行に加えられたすべての変更を元に戻します。|  
|行頭|セルを編集するときに、挿入位置の前の文字を削除します。|  
|Del|セルを編集するときに、挿入位置の後の文字を削除します。|  
|Ctrl + Enter|フォーカスを移動せずに、現在のセルに対するすべての変更をコミットします。 また、は、編集をサポートするデータソースにコントロールがバインドされている場合、または行レベルのコミットスコープで仮想モードが実装されている場合に、現在の行に対するすべての変更をコミットします。|  
|Ctrl + 0|セルを<xref:System.DBNull.Value?displayProperty=nameWithType>編集できる場合は、現在のセルに値を入力します。 既定では、 <xref:System.DBNull>セル値の表示値は、 <xref:System.Windows.Forms.DataGridViewCellStyle>現在のセルに<xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A>対して有効になっているのプロパティの値です。|  
  
### <a name="selection-keys"></a>選択キー

 プロパティがに`false`設定されてい<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>て、プロパティが<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>に設定されている場合、ナビゲーションキーを使用して現在のセルを変更すると、選択内容が新しいセルに変わります。 <xref:System.Windows.Forms.DataGridView.MultiSelect%2A> SHIFT、CTRL、ALT の各キーは、この動作に影響しません。  
  
 がまた<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> は<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>に設定されている場合、同じ動作が発生しますが、次の追加機能があります。 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>  
  
|キーまたはキーの組み合わせ|説明|  
|----------------------------|-----------------|  
|SHIFT + SPACE|行または列の全体を選択します (行または列のヘッダーをクリックした場合と同じです)。|  
|ナビゲーションキー (矢印キー、pageup/DOWN、HOME、END)|行または列がすべて選択されている場合、現在のセルを新しい行または列に変更すると、選択範囲が新しい行または列に移動します (選択モードによって異なります)。|  
  
 が<xref:System.Windows.Forms.DataGridView.MultiSelect%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>に設定`false`され、がまたはに設定されている場合、キーボードを使用して現在のセルを新しい行または列に変更すると、選択範囲が完全な新しい行または列に<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>移動します。 SHIFT、CTRL、ALT の各キーは、この動作に影響しません。  
  
 が<xref:System.Windows.Forms.DataGridView.MultiSelect%2A> に`true`設定されている場合、ナビゲーション動作は変更されませんが、shift キーを押しながら (CTRL + SHIFT を含む) キーボードで移動すると、複数セルの選択が変更されます。 ナビゲーションが開始される前に、コントロールは現在のセルをアンカーセルとしてマークします。 SHIFT キーを押しながら移動すると、アンカーセルと現在のセルの間にあるすべてのセルが選択範囲に含まれます。 コントロール内の他のセルは、既に選択されている場合は選択されたままになりますが、キーボードナビゲーションによってアンカーセルと現在のセルの間に一時的に配置されると、選択が解除されることがあります。  
  
 が<xref:System.Windows.Forms.DataGridView.MultiSelect%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect>に設定`true`され、がまたはに設定されている場合、アンカーセルと現在のセルの動作は同じですが、完全な行または列のみが選択または選択解除<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>されます。  
  
## <a name="default-mouse-handling"></a>既定のマウス処理
  
### <a name="basic-mouse-handling"></a>基本的なマウス処理
  
> [!NOTE]
> マウスの左ボタンを使用してセルをクリックすると、常に現在のセルが変更されます。 マウスの右ボタンを使用してセルをクリックすると、ショートカットメニューが表示されます (使用可能な場合)。  
  
|マウス操作|説明|  
|------------------|-----------------|  
|マウスの左ボタンを押す|クリックされたセルを現在のセルにし<xref:System.Windows.Forms.DataGridView.CellMouseDown?displayProperty=nameWithType> 、イベントを発生させます。|  
|マウスの左ボタンを上へ移動|<xref:System.Windows.Forms.DataGridView.CellMouseUp?displayProperty=nameWithType> イベントを発生させます。|  
|マウスの左ボタンのクリック|イベントと<xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> <xref:System.Windows.Forms.DataGridView.CellMouseClick?displayProperty=nameWithType>イベントを発生させます。|  
|マウスボタンを押したままにして、列ヘッダーセルにドラッグします|<xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>プロパティが`true`の場合は、新しい位置にドロップできるように列を移動します。|  
  
### <a name="mouse-selection"></a>マウスの選択

 マウスの中央ボタンまたはマウスホイールには、選択動作が関連付けられていません。  
  
 プロパティがに`false` 設定され、<xref:System.Windows.Forms.DataGridViewSelectionMode.CellSelect>プロパティがに設定されている場合、次の動作が発生します。 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> <xref:System.Windows.Forms.DataGridView.MultiSelect%2A>  
  
|マウス操作|説明|  
|------------------|-----------------|  
|マウスの左ボタンをクリック|ユーザーがセルをクリックした場合に、現在のセルのみを選択します。 ユーザーが行ヘッダーまたは列ヘッダーをクリックした場合、選択の動作はありません。|  
|マウスの右ボタンをクリック|使用できる場合は、ショートカットメニューを表示します。|  
  
 この動作は、 <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>がまたは<xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>に<xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect>設定されている場合にも発生します。ただし、選択モードによっては、行または列のヘッダーをクリックすると、行または列のすべての行または列が選択され、現在のセルが行または列の最初のセルに設定されます。  
  
 が<xref:System.Windows.Forms.DataGridView.SelectionMode%2A>または<xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> に<xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>設定されている場合、行または列の任意のセルをクリックすると、行または列全体が選択されます。  
  
 が<xref:System.Windows.Forms.DataGridView.MultiSelect%2A> に`true`設定されている場合、CTRL キーまたは SHIFT キーを押しながらセルをクリックすると、複数セルの選択が変更されます。  
  
 CTRL キーを押しながらセルをクリックすると、セルの選択状態が変化し、他のすべてのセルは現在の選択状態を保持します。  
  
 SHIFT キーを押しながらセルまたは一連のセルをクリックすると、選択範囲には、現在のセルと、最初のクリックの前の現在のセルの位置にあるアンカーセルの間のすべてのセルが含まれます。 ポインターをクリックして複数のセルにドラッグすると、アンカーセルはドラッグ操作の開始時にクリックされたセルになります。 SHIFT キーを押しながらクリックすると、現在のセルは変更されますが、アンカーセルは変更されません。 コントロール内のその他のセルは、既に選択されている場合は選択されたままになりますが、マウスのナビゲーションによってアンカーセルと現在のセルの間に一時的に配置されると、選択が解除されることがあります。  
  
 が<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>に<xref:System.Windows.Forms.DataGridView.SelectionMode%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect>設定されていて、がまたはに設定されている場合、SHIFT キーを押すと、行または列のヘッダー (選択モードによって異なります) をクリックすると、行または列の既存の選択が変更されます。 `true`選択範囲が存在します。 それ以外の場合は、選択をクリアし、完全な行または列の新しい選択を開始します。 ただし、CTRL キーを押しながら行または列のヘッダーをクリックすると、現在の選択範囲を変更せずに、選択した行または列が現在の選択から追加または削除されます。  
  
 が<xref:System.Windows.Forms.DataGridView.MultiSelect%2A>に<xref:System.Windows.Forms.DataGridView.SelectionMode%2A> <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect>設定されていて、がまたはに設定されている場合、SHIFT キーまたは CTRL キーを押しながらセルをクリックした場合と同じように動作します。ただし、完全な行と列のみが影響を受けます。 `true`  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- [DataGridView コントロール](datagridview-control-windows-forms.md)
