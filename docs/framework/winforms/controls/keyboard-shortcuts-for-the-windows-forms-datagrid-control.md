---
title: Windows フォームの DataGrid コントロール内の移動に使用できるキーボード ショートカット
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard shortcuts [Windows Forms], DataGrid control
- DataGrid control [Windows Forms], navigation keys
ms.assetid: a01780f9-20d5-4f5f-808f-c790c9a007a5
ms.openlocfilehash: 58e65ee9d95329c3583515b99db47b87b3749c8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973785"
---
# <a name="keyboard-shortcuts-for-the-windows-forms-datagrid-control"></a>Windows フォームの DataGrid コントロール内の移動に使用できるキーボード ショートカット
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 次の表に、Windows フォーム内のナビゲーションに使用できるキーボード ショートカット<xref:System.Windows.Forms.DataGrid>コントロール。  
  
|アクション|ショートカット|  
|------------|--------------|  
|セルの入力を完了し、次のセルに下に移動します。<br /><br /> 子テーブルのリンクにフォーカスがある場合は、そのテーブルに移動します。|Enter|  
|セルの編集モードの場合は、セルの編集をキャンセルします。<br /><br /> マーキーの選択の場合は、行の編集をキャンセルします。|Esc|  
|セルを編集するときに、挿入ポイントの前に文字を削除します。|BACKSPACE キー|  
|セルを編集するときに、カーソル位置の後の文字を削除します。|Del|  
|現在の行の最初のセルに移動します。|ホーム|  
|最後の現在の行のセルに移動します。|End|  
|現在のセル内の文字を強調表示し、行の末尾にカーソルを置きます。 セルをダブルクリックした場合と同じ動作です。|F2|  
|セルにフォーカスがある場合は、次の行のセルに移動します。<br /><br /> 行の最後のセルにフォーカスがある場合は、行の最初の子テーブルのリンクに移動し、それを展開します。<br /><br /> 子のリンクにフォーカスがある場合は、[次へ] の子のリンクに移動します。<br /><br /> 最後の子のリンクにフォーカスがある場合は、次の行の最初のセルに移動します。|Tab|  
|セルにフォーカスがある場合は、行の前のセルに移動します。<br /><br /> 行の最初のセルにフォーカスがある場合は、前の行の最後の展開された子テーブルのリンクに移動または最後の前の行のセルに移動します。<br /><br /> 子のリンクにフォーカスがある場合は、以前の子へのリンクに移動します。<br /><br /> 最初の子のリンクにフォーカスがある場合は移動前の行のセルでは、最後にします。|Shift + Tab|  
|タブ オーダー内で次のコントロールに移動します。|Ctrl + Tab|  
|タブ オーダー内で前のコントロールに移動します。|Ctrl + Shift + Tab|  
|子テーブルの場合に、親テーブルに移動します。 [戻る] ボタンをクリックすると同じ動作です。|Alt + ←|  
|子テーブルへのリンクを展開します。 Alt キーを押しながら下方向は、選択したものだけでなく、すべてのリンクを展開します。|Alt キーを押しながら下方向キーまたは CTRL + プラス記号|  
|子テーブルへのリンクを折りたたみます。 ALT + 上方向キーでは、選択したものだけでなく、すべてのリンクを折りたたみます。|ALT + 上方向キーまたは CTRL + マイナス記号|  
|矢印の方向の右端の空白のセルに移動します。|CTRL + 方向キー|  
|(子テーブルへのリンクを除く) の矢印の方向に選択範囲の 1 つの行を拡張します。|SHIFT + ↑ または ↓|  
|(子テーブルへのリンクを除く) の矢印の向きの右端の空白行に選択範囲を拡大します。|CTRL + SHIFT + 上向き/下向きの矢印|  
|左上隅のセルに移動します。|Ctrl + Home|  
|右下のセルに移動します。|Ctrl + End|  
|一番上の行を選択範囲を拡大します。|Ctrl</localizedText> + <localizedText>Shift</localizedText> + <localizedText>Home|  
|一番下の行を選択範囲を拡大します。|Ctrl</localizedText> + <localizedText>Shift</localizedText> + <localizedText>End|  
|(子テーブルへのリンクを除く) 現在の行を選択します。|SHIFT キーを押しながら SPACE キー|  
|グリッド全体 (子テーブルへのリンクを除く) を選択します。|Ctrl + A|  
|子テーブルにある場合、親の行を表示します。|Ctrl + PageDown|  
|子テーブルにある場合、親の行を非表示にします。|Ctrl + PageUp|  
|1 つの画面 (子テーブルへのリンクを除く) を選択範囲を拡大します。|Shift + PageDown|  
|1 つの画面 (子テーブルへのリンクを除く) を選択範囲を拡大します。|Shift + PageUp|  
|呼び出す、<xref:System.Windows.Forms.DataGrid.EndEdit%2A>メソッドが現在の行。|Ctrl + Enter|  
|入力、<xref:System.DBNull.Value?displayProperty=nameWithType>編集モードでのセルに値。|Ctrl + 0|  
  
## <a name="see-also"></a>関連項目

- [DataGrid コントロールの概要](datagrid-control-overview-windows-forms.md)
- [DataGrid コントロール](datagrid-control-windows-forms.md)
