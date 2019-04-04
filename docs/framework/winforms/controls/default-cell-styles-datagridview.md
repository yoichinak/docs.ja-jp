---
title: '方法: デザイナーを使用して Windows フォーム DataGridView コントロールの既定のセル スタイルとデータ形式を設定します。'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], setting styles
- data formats
- data [Windows Forms], setting formats
ms.assetid: fc6da49f-8942-41da-b49f-b2afc38cc656
ms.openlocfilehash: 44180c1d8e7f6fd29778ef6b9f5bd5e333c3ece2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702348"
---
# <a name="how-to-set-default-cell-styles-and-data-formats-for-the-windows-forms-datagridview-control-using-the-designer"></a>方法: デザイナーを使用して Windows フォーム DataGridView コントロールの既定のセル スタイルとデータ形式を設定します。
<xref:System.Windows.Forms.DataGridView>コントロールを使用する既定のセル スタイルを指定し、コントロール全体の特定の列、行および列のヘッダーおおよび台帳効果を作成する行を交互のデータ形式します。 既定のスタイルのコントロール全体の設定は、既定の列と交互の行のスタイル設定によって上書きされます。 さらに、個々 の行とセルのコードに設定するスタイルは、既定のスタイルをオーバーライドします。  
  
 セルのスタイルの詳細については、[Windows フォームの DataGridView コントロールのセル スタイル](cell-styles-in-the-windows-forms-datagridview-control.md)を参照してください。 交互の行のスタイルを設定するを参照してください。[方法。Windows フォーム DataGridView コントロールのデザイナーを使用しての交互の行のスタイル設定](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)します。  
  
 使用してスタイルを設定することも、<xref:System.Windows.Forms.DataGridView.RowTemplate%2A>プロパティをコントロールに追加されるすべての行に影響します。 行のテンプレートの詳細については、次を参照してください。[方法。行テンプレートを使用して Windows フォームの DataGridView コントロール内の行をカスタマイズする](use-the-row-template-to-customize-rows-in-the-datagrid.md)します。  
  
 次の手順が必要です、 **Windows アプリケーション**プロジェクトが含まれているフォームを<xref:System.Windows.Forms.DataGridView>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[方法。Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)と[方法。Windows フォームにコントロールを追加](how-to-add-controls-to-windows-forms.md)します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-set-default-styles-for-all-cells-in-the-control"></a>コントロール内のすべてのセルの既定のスタイルを設定するには  
  
1.  選択、<xref:System.Windows.Forms.DataGridView>デザイナーでコントロールできます。  
  
2.  **プロパティ**ウィンドウで、省略記号ボタンをクリックします (![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")) 横に、 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>、 <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>、または<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>プロパティ。 **[CellStyle ビルダー** ] ダイアログ ボックスが表示されます。  
  
3.  使用して、プロパティを設定してスタイルを定義、**プレビュー**ウィンドウで選択内容を確認します。  
  
> [!NOTE]
>  Visual スタイルが有効な場合行および列ヘッダー (を除き、 <xref:System.Windows.Forms.DataGridView.TopLeftHeaderCell%2A>) は、現在のテーマによって自動的にスタイルが設定をオーバーライドする、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>と<xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle%2A>プロパティの値。  
>   
>  選択された複数のセル スタイルを設定する<xref:System.Windows.Forms.DataGridView>セル スタイル プロパティを変更するのと同じ値がある場合にのみ、デザイナーの使用を制御します。 そのプロパティの任意のセルのスタイルが異なる場合、**プロパティ**の windows、 **[CellStyle ビルダー** ] ダイアログ ボックスは空白になります。  
  
### <a name="to-set-default-styles-for-cells-in-individual-columns"></a>個々 の列のセルの既定のスタイルを設定するには  
  
1.  右クリックし、<xref:System.Windows.Forms.DataGridView>デザイナーで制御および選択**列の編集**します。  
  
2.  列を選択、**選択した列**一覧。  
  
3.  **列プロパティ**グリッドで、省略記号ボタンをクリックします (![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")) 横に、<xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A>プロパティ。 **[CellStyle ビルダー** ] ダイアログ ボックスが表示されます。  
  
4.  使用して、プロパティを設定してスタイルを定義、**プレビュー**ウィンドウで選択内容を確認します。  
  
### <a name="to-format-data-in-cells"></a>データ セルを書式設定するには  
  
1.  表示する前の手順のいずれかを使用して、 **[CellStyle ビルダー** ] ダイアログ ボックスに関連する既定のセル スタイル プロパティ。  
  
2.  **[CellStyle ビルダー** ] ダイアログ ボックスで、省略記号ボタンをクリックします (![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")) 横に、 <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>プロパティ。 **書式指定文字列** ダイアログ ボックスが表示されます。  
  
3.  形式の種類を選択し、表示する小数点以下桁数の数) などの型の詳細の変更を使用して、**サンプル**ボックス選択内容を確認します。  
  
4.  バインドしている場合、 <xref:System.Windows.Forms.DataGridView> null 値を含む、入力する可能性があるデータ ソースにコントロール、 **Null 値**テキスト ボックス。 セルの値が null 参照に等しい場合に、この値が表示されます (`Nothing` Visual basic) または<xref:System.DBNull.Value?displayProperty=nameWithType>します。  
  
## <a name="see-also"></a>関連項目
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A?displayProperty=nameWithType>
- [Windows フォーム DataGridView コントロールでのセルのスタイル](cell-styles-in-the-windows-forms-datagridview-control.md)
- [方法: デザイナーを使用して Windows フォーム DataGridView コントロールの交互の行のスタイル設定します。](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)
- [方法: Windows フォーム アプリケーション プロジェクトの作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [方法: Windows フォームにコントロールを追加します。](how-to-add-controls-to-windows-forms.md)
