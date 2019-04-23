---
title: DataGrid コントロールの既定のキーボード動作とマウス動作
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid [WPF], keyboard behavior
- DataGrid [WPF], mouse behavior
- keyboard behavior [WPF], DataGrid
- mouse behavior [WPF], DataGrid
ms.assetid: 563b8854-ca39-4d97-8235-17eaa0f93c8d
ms.openlocfilehash: 6be464ce85bd3ba91dd6e6cc810ec7d04edc0c3d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59083323"
---
# <a name="default-keyboard-and-mouse-behavior-in-the-datagrid-control"></a>DataGrid コントロールの既定のキーボード動作とマウス動作
このトピックでは、ユーザーの対話方法について説明します、<xref:System.Windows.Controls.DataGrid>キーボードとマウスを使用して制御します。  
  
 一般的な対話、<xref:System.Windows.Controls.DataGrid>ナビゲーション、選択した場合、および編集します。 選択の動作を受ける、<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>と<xref:System.Windows.Controls.DataGrid.SelectionUnit%2A>プロパティ。 このトピックで説明する動作が発生する既定値は<xref:System.Windows.Controls.DataGridSelectionMode.Extended?displayProperty=nameWithType>と<xref:System.Windows.Controls.DataGridSelectionUnit.FullRow?displayProperty=nameWithType>します。 これらの値を変更すると、説明されているとは異なる動作が発生する可能性があります。 標準のキーボード動作の場合、セルが編集モードでは、編集コントロール方が優先されます、<xref:System.Windows.Controls.DataGrid>します。  
  
## <a name="default-keyboard-behavior"></a>既定のキーボード動作  
 次の表に、既定のキーボード動作、<xref:System.Windows.Controls.DataGrid>します。  
  
|キーまたはキーの組み合わせ|説明|  
|----------------------------|-----------------|  
|↓|現在のセルの直下のセルにフォーカスを移動します。 最後の行にフォーカスがある場合は、下方向キーを押すと何も行われません。|  
|↑|現在のセルのすぐ上のセルにフォーカスを移動します。 最初の行にフォーカスがある場合は、上方向キーを押して何も行われません。|  
|←|行の前のセルにフォーカスを移動します。 行の最初のセルにフォーカスがある場合は、左方向キーを押すと何も行われません。|  
|→|次の行のセルにフォーカスを移動します。 行の最後のセルにフォーカスがある場合は、右矢印を押すと何もしません。|  
|ホーム|現在の行の最初のセルにフォーカスを移動します。|  
|End|現在の行の最後のセルにフォーカスを移動します。|  
|PAGE DOWN|行はグループ化されていない場合は、完全に表示されている行の数によって、コントロールを下にスクロールします。 最後に完全に表示されている行に列を変更することがなく、フォーカスを移動します。<br /><br /> 行はグループ化する場合は、最後の行にフォーカスを移動、<xref:System.Windows.Controls.DataGrid>列を変更することがなく。|  
|PAGE UP|行はグループ化されていない場合、完全に表示されている行の数でコントロールを上へスクロールします。 列を変更することがなく表示される最初の行にフォーカスを移動します。<br /><br /> 行はグループ化する場合は、最初の行にフォーカスを移動、<xref:System.Windows.Controls.DataGrid>列を変更することがなく。|  
|Tab|現在の行に次のセルにフォーカスを移動します。 行の最後のセルにフォーカスがある場合は、次の行の最初のセルにフォーカスを移動します。 コントロール内の最後のセルにフォーカスがある場合は、親コンテナーのタブ オーダー内で次のコントロールにフォーカスを移動します。<br /><br /> 現在のセルが編集モードと現在の行から移動する原因フォーカスをタブ キーを押して、行に加えられた変更がコミットされますフォーカスが変更される前にいます。 場合、|  
|Shift + Tab|現在の行の前のセルにフォーカスを移動します。 行の最初のセルにフォーカスがある場合は、前の行の最後のセルにフォーカスを移動します。 コントロール内の最初のセルにフォーカスがある場合は、親コンテナーのタブ オーダー内で前のコントロールにフォーカスを移動します。<br /><br /> 現在のセルが編集モードと現在の行から移動する原因フォーカスをタブ キーを押して、行に加えられた変更がコミットされますフォーカスが変更される前にいます。 場合、|  
|Ctrl +↓|現在の列の最後のセルにフォーカスを移動します。|  
|Ctrl + ↑|現在の列の最初のセルにフォーカスを移動します。|  
|Ctrl + →|現在の行の最後のセルにフォーカスを移動します。|  
|Ctrl + ←|現在の行の最初のセルにフォーカスを移動します。|  
|Ctrl + Home|コントロールの最初のセルにフォーカスを移動します。|  
|Ctrl + End|コントロールの最後のセルにフォーカスを移動します。|  
|Ctrl + PageDown|PAGEDOWN と同じです。|  
|Ctrl + PageUp|ページの上と同じです。|  
|F2|場合、<xref:System.Windows.Controls.DataGrid.IsReadOnly%2A?displayProperty=nameWithType>プロパティは`false`と<xref:System.Windows.Controls.DataGridColumn.IsReadOnly%2A?displayProperty=nameWithType>プロパティは`false`現在の列のセルの編集モードに現在のセルを格納します。|  
|Enter|現在のセルと行に変更をコミットし、現在のセルの直下のセルにフォーカスを移動します。 最後の行にフォーカスがある場合は、フォーカスを移動せず、変更をコミットします。|  
|Esc|コントロールが編集モードにある場合は、編集をキャンセルし、コントロールに加えられた変更を元に戻します。 基になるデータ ソースの実装場合<xref:System.ComponentModel.IEditableObject>、行全体の編集モードをキャンセルを 2 回目に esc キーを押します。|  
|BACKSPACE キー|セルを編集するときに、カーソルの前に文字を削除します。|  
|Del|セルを編集するときに、カーソルより後の文字を削除します。|  
|Ctrl + Enter|現在のセルにフォーカスを移動せず、変更をコミットします。|  
|Ctrl + A|場合<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>に設定されている<xref:System.Windows.Controls.DataGridSelectionMode.Extended>、すべての行を選択、<xref:System.Windows.Controls.DataGrid>します。|  
  
## <a name="selection-keys"></a>キーの選択  
 場合、<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>プロパティに設定されて<xref:System.Windows.Controls.DataGridSelectionMode.Extended>ナビゲーションの動作は変わりませんが、複数の行の選択が変更されます (CTRL + SHIFT を含む) shift キーを押しながらキーボードでナビゲートします。 ナビゲーションが開始する前に、コントロールは、アンカーの行として、現在の行をマークします。 Shift キーを押しながら移動するときに、選択範囲には、アンカーの行と、現在の行の間のすべての行が含まれています。  
  
 次の選択キーは、複数行の選択を変更します。  
  
-   Shift + ↓  
  
-   Shift + ↑  
  
-   Shift + PageDown  
  
-   Shift + PageUp  
  
-   Ctrl + Shift + ↓  
  
-   Ctrl + Shift + ↑  
  
-   Ctrl</localizedText> + <localizedText>Shift</localizedText> + <localizedText>Home  
  
-   Ctrl</localizedText> + <localizedText>Shift</localizedText> + <localizedText>End  
  
## <a name="default-mouse-behavior"></a>既定のマウス動作  
 次の表に、マウスの既定の動作、<xref:System.Windows.Controls.DataGrid>します。  
  
|マウス操作|説明|  
|------------------|-----------------|  
|選択されていない行をクリックします|クリックされた行では、現在の行と現在のセルにセルがクリックされました。|  
|現在のセルをクリックします。|現在のセルを編集モードに配置します。|  
|列ヘッダー セルをドラッグします。|場合、<xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A?displayProperty=nameWithType>プロパティは`true`と<xref:System.Windows.Controls.DataGridColumn.CanUserReorder%2A?displayProperty=nameWithType>プロパティは`true`の現在の列を新しい位置に削除されるように列を移動します。|  
|列ヘッダーの区切り線をドラッグします。|場合、<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType>プロパティは`true`と<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType>プロパティは`true`現在の列の列のサイズを変更します。|  
|列ヘッダーの区切り線をダブルクリックします。|場合、<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A?displayProperty=nameWithType>プロパティは`true`と<xref:System.Windows.Controls.DataGridColumn.CanUserResize%2A?displayProperty=nameWithType>プロパティは`true`サイズが自動的に、現在の列の列を使用して、<xref:System.Windows.Controls.DataGridLength.Auto%2A>サイズ変更モード。|  
|列ヘッダー セルをクリックします。|場合、<xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A?displayProperty=nameWithType>プロパティは`true`と<xref:System.Windows.Controls.DataGridColumn.CanUserSort%2A?displayProperty=nameWithType>プロパティは`true`現在の列の列を並べ替えます。<br /><br /> まだ並べ替えられている列の見出しをクリックすると、その列の並べ替えの方向は逆です。<br /><br /> SHIFT キーを押しながら複数の列見出しをクリックした順番で複数の列で並べ替えられます。|  
|Ctrl キーを押しながら、行をクリックします。|場合<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>に設定されている<xref:System.Windows.Controls.DataGridSelectionMode.Extended>、連続しない複数の行の選択を変更します。<br /><br /> 行が既に選択されている場合は、行を選択解除します。|  
|Shift キー、行をクリックします。|場合<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>に設定されている<xref:System.Windows.Controls.DataGridSelectionMode.Extended>、複数行の連続する範囲を変更します。|  
|行グループ ヘッダーをクリックします。|展開またはグループを折りたたみます。|  
|左上隅にある [すべて選択] ボタンをクリックします <xref:System.Windows.Controls.DataGrid>|場合<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>に設定されている<xref:System.Windows.Controls.DataGridSelectionMode.Extended>、すべての行を選択、<xref:System.Windows.Controls.DataGrid>します。|  
  
## <a name="mouse-selection"></a>マウスの選択  
 場合、<xref:System.Windows.Controls.DataGrid.SelectionMode%2A>プロパティに設定されて<xref:System.Windows.Controls.DataGridSelectionMode.Extended>、複数行の選択範囲の変更は ctrl キーまたは shift キーを押しながら行をクリックします。  
  
 CTRL キーを押しながら、行をクリックすると、行は、その他のすべての行が現在の選択状態を保持の選択状態を変更します。 連続していない行を選択します。  
  
 Shift キーを押しながら、行をクリックすると、選択範囲には、現在の行と、アンカーの行をクリックする前に、現在の行の位置にあるすべての行が含まれています。 Shift キーを押しながら後続数回のクリックでは、現在の行がアンカー行ではなくを変更します。 隣接する行の範囲を選択します。  
  
 隣接する行の連続していない範囲を選択するには、CTRL + SHIFT を組み合わせることできます。 これを行うには、shift キーを使用して、最初の範囲を選択 + 前述のようにクリックします。 行の最初の範囲を選択した後、ctrl キーを使用 + をクリックして [次へ] の範囲の最初の行を選択し、CTRL + SHIFT を押しながら次の範囲の最後の行をクリックします。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Controls.DataGrid>
- <xref:System.Windows.Controls.DataGrid.SelectionMode%2A>
