---
title: '方法: デザイナーを使用して Windows フォーム DataGridView コントロールの既定のセル スタイルとデータ形式を設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 6d7d867b7c9e83b68589e046565bfb0199692f5f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658512"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>方法: デザイナーを使用して Windows フォーム DataGridView コントロールの既定のセル スタイルとデータ形式を設定する

<xref:System.Windows.Forms.DataGridView>コントロールを使用すると、コントロール全体、特定の列、行ヘッダー、列ヘッダー、および行と列のヘッダーに対して既定のセルスタイルとセルデータ形式を指定できます。また、行を交互に使用して、元帳効果を作成することもできます。 コントロール全体に対して設定されている既定のスタイルは、列および交互の行に対して設定された既定のスタイルによって上書きされます。 また、個々の行およびセルのコードで設定したスタイルは、既定のスタイルを上書きします。

セルスタイルの詳細については、「 [Windows フォーム DataGridView コントロールのセルのスタイル](cell-styles-in-the-windows-forms-datagridview-control.md)」を参照してください。 交互の行のスタイルを設定する[には、「方法:デザイナー](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)を使用して、Windows フォーム DataGridView コントロールに交互の行のスタイルを設定します。

また、 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>プロパティを使用してスタイルを設定し、コントロールに追加されるすべての行に影響を与えることもできます。 行テンプレートの詳細については、 [「方法:行テンプレートを使用して、Windows フォーム DataGridView コントロール](use-the-row-template-to-customize-rows-in-the-datagrid.md)で行をカスタマイズします。

次の手順では、 <xref:System.Windows.Forms.DataGridView>コントロールを含むフォームを含む**Windows アプリケーション**プロジェクトが必要です。 このようなプロジェクトの設定の詳細につい[ては、「方法:Windows フォームアプリケーションプロジェクト](/visualstudio/ide/step-1-create-a-windows-forms-application-project)を作成し[、次の操作を行います。Windows フォーム](how-to-add-controls-to-windows-forms.md)にコントロールを追加します。

### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>コントロール内のすべてのセルに既定のスタイルを設定するには

1. デザイナーで<xref:System.Windows.Forms.DataGridView>コントロールを選択します。

2. **[プロパティ]** ![ウィンドウで、 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>、](./media/visual-studio-ellipsis-button.png) <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>、または<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>の各プロパティの横にある省略記号ボタン ([...] プロパティウィンドウ) をクリックします。 **[CellStyle ビルダー]** ダイアログボックスが表示されます。

3. **プレビュー**ウィンドウを使用して選択内容を確認し、プロパティを設定してスタイルを定義します。

> [!NOTE]
> 視覚スタイルが有効になっている場合、行ヘッダーと列ヘッダー <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>(を除く) は、現在のテーマによっ<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>て<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>自動的にスタイルが設定され、プロパティ値とプロパティ値はオーバーライドされます。
>
> デザイナーを使用して、複数の<xref:System.Windows.Forms.DataGridView>選択したコントロールのセルスタイルを設定できますが、変更するセルスタイルプロパティの値が同じである場合に限られます。 そのプロパティのセルスタイルが異なる場合、 **[CellStyle ビルダー]** ダイアログボックスの **[プロパティ]** ウィンドウは空白になります。

### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>個々の列のセルに既定のスタイルを設定するには

1. デザイナーで<xref:System.Windows.Forms.DataGridView>コントロールを右クリックし、 **[列の編集]** を選択します。

2. **[選択された列]** ボックスの一覧から列を選択します。

3. **[列のプロパティ]** グリッドで、プロパティ![の<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>横にある省略記号ボタン (Visual Studio](./media/visual-studio-ellipsis-button.png)のプロパティウィンドウの省略記号ボタン (...)) をクリックします。 **[CellStyle ビルダー]** ダイアログボックスが表示されます。

4. **プレビュー**ウィンドウを使用して選択内容を確認し、プロパティを設定してスタイルを定義します。

### <a name="to-format-data-in-cells"></a>セルのデータの書式を設定するには

1. 前の手順のいずれかを使用して、既定のセルスタイルプロパティに関連する **[CellStyle ビルダー]** ダイアログボックスを表示します。

2. **[CellStyle ビルダー]** ダイアログボックスで、プロパティの![ <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>横にある省略記号ボタン (Visual Studio](./media/visual-studio-ellipsis-button.png)のプロパティウィンドウの省略記号ボタン ([...]) をクリックします。 **[書式文字列]** ダイアログボックスが表示されます。

3. 書式の種類を選択してから、 **[サンプル]** ボックスを使用して選択内容を確認し、種類の詳細 (表示する小数点以下の桁数など) を変更します。

4. Null 値が含まれる<xref:System.Windows.Forms.DataGridView>可能性のあるデータソースにコントロールをバインドする場合は、 **[null 値]** ボックスに入力します。 この値は、セルの値が null 参照 (`Nothing` Visual Basic) または<xref:System.DBNull.Value?displayProperty=nameWithType>である場合に表示されます。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Windows フォーム DataGridView コントロールでのセルのスタイル](cell-styles-in-the-windows-forms-datagridview-control.md)
- [方法: デザイナーを使用して Windows フォーム DataGridView コントロールに交互の行のスタイルを設定する](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [方法: Windows フォーム アプリケーション プロジェクトの作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [方法: コントロールを Windows フォームに追加する](how-to-add-controls-to-windows-forms.md)
