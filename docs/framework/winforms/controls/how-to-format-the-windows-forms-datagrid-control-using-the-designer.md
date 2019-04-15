---
title: '方法: デザイナーを使って Windows フォーム DataGrid コントロールの書式を設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- columns [Windows Forms], DataGrid controls
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: 533b9814-6124-49dc-9fda-085f1502609f
ms.openlocfilehash: fbe2aa724274022446498a89618f37787f0fa8bd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59333575"
---
# <a name="how-to-format-the-windows-forms-datagrid-control-using-the-designer"></a>方法: デザイナーを使って Windows フォーム DataGrid コントロールの書式を設定する

> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 さまざまな部分に別の色を適用する、<xref:System.Windows.Forms.DataGrid>コントロールのことで情報を読みやすくするヘルプことができます。 色は、行と列に適用できます。 行と列も非表示にしたりユーザーの判断で示すようにします。  
  
 書式設定の 3 つの基本的な機能がある、<xref:System.Windows.Forms.DataGrid>コントロール。  
  
-   データを表示する既定のスタイルを確立するためにプロパティを設定することができます。  
  
-   そのベースから、実行時に特定のテーブルの表示方法をカスタマイズできます。  
  
-   最後に、色と同様に、データ グリッドで表示する列を変更することができ、その他の書式を示します。  
  
 データ グリッドの書式設定に最初のステップとしてのプロパティを設定することができます、<xref:System.Windows.Forms.DataGrid>自体。 これらの色と書式の選択を加えることができますし、データ テーブルと表示される列によって、ベースを形成します。  
  
 次の手順が必要です、 **Windows アプリケーション**プロジェクトが含まれているフォームを<xref:System.Windows.Forms.DataGrid>コントロール。 このようなプロジェクトの設定の詳細については、次を参照してください。[方法。Windows フォーム アプリケーション プロジェクトを作成](/visualstudio/ide/step-1-create-a-windows-forms-application-project)と[方法。Windows フォームにコントロールを追加](how-to-add-controls-to-windows-forms.md)します。 Visual Studio 2005 で、<xref:System.Windows.Forms.DataGrid>制御されていない、**ツールボックス**既定。 詳細については、「[方法 :項目をツールボックスに追加](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms165355(v=vs.100))します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。 設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。 詳細については、「[Visual Studio IDE のカスタマイズ](/visualstudio/ide/personalizing-the-visual-studio-ide)」を参照してください。  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>DataGrid コントロールの既定のスタイルを確立するには  
  
1. <xref:System.Windows.Forms.DataGrid> コントロールを選択します。  
  
2. **プロパティ**ウィンドウで、適切な次のプロパティを設定します。  
  
    |プロパティ|説明|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|`BackColor`プロパティ グリッドの偶数行の色を定義します。 設定すると、<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>プロパティを別の色は、その他のすべての行は、この新しい色に設定が (行 1、3、5、およびなど)。|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|グリッドの偶数行の背景色 (0、2、4、6、および具合の行数)。|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|一方、<xref:System.Windows.Forms.DataGrid.BackColor%2A>と<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>プロパティは、グリッド内の行の色を決定、<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>プロパティは、一番下のグリッドがスクロールされたとき、または少数の行がの場合のみ表示される行領域の外側の色を決定します。グリッドに含まれています。|  
    |<xref:System.Windows.Forms.DataGrid.BorderStyle%2A>|1 つのグリッドの罫線のスタイル、<xref:System.Windows.Forms.BorderStyle>列挙値。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionBackColor%2A>|グリッドの上にすぐに表示されるグリッドのウィンドウ キャプションの背景色。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionFont%2A>|グリッドの上部のキャプションのフォントです。|  
    |<xref:System.Windows.Forms.DataGrid.CaptionForeColor%2A>|グリッドのウィンドウ キャプションの背景色。|  
    |<xref:System.Windows.Forms.Control.Font%2A>|グリッド内のテキストを表示するために使用するフォントです。|  
    |<xref:System.Windows.Forms.DataGrid.ForeColor%2A>|データ グリッド内の行のデータが表示されるフォントの色。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineColor%2A>|データ グリッドのグリッド線の色。|  
    |<xref:System.Windows.Forms.DataGrid.GridLineStyle%2A>|いずれかと、グリッドのセルを区切る線のスタイル、<xref:System.Windows.Forms.DataGridLineStyle>列挙値。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderBackColor%2A>|行および列ヘッダーの背景色。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderFont%2A>|列ヘッダーに使用するフォントです。|  
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|列ヘッダーのテキストと、プラス記号 (+) とマイナス記号 (-) を展開し、複数の関連するテーブルと行を折りたたむグリフを含むグリッドの列ヘッダーの前景の色が表示されます。|  
    |<xref:System.Windows.Forms.DataGrid.LinkColor%2A>|子テーブル、リレーションシップ名、およびなどへのリンクなど、データ グリッド内のすべてのリンクのテキストの色。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsBackColor%2A>|子テーブルでは、これは、親の行の背景色です。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsForeColor%2A>|子テーブルでは、これは、親の行の前景色。|  
    |<xref:System.Windows.Forms.DataGrid.ParentRowsLabelStyle%2A>|親の行のテーブルと列の名前が表示されるかどうかを決定、<xref:System.Windows.Forms.DataGridParentRowsLabelStyle>列挙体。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredColumnWidth%2A>|グリッドの列の既定の幅 (ピクセル単位)。 リセットする前に、このプロパティを設定、<xref:System.Windows.Forms.DataGrid.DataSource%2A>と<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティ (どちらかとは別に、または、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッド)、またはプロパティには効果はありません。<br /><br /> プロパティは、0 より小さい値に設定できません。|  
    |<xref:System.Windows.Forms.DataGrid.PreferredRowHeight%2A>|グリッド内の行のピクセル単位で行の高さ。 リセットする前に、このプロパティを設定、<xref:System.Windows.Forms.DataGrid.DataSource%2A>と<xref:System.Windows.Forms.DataGrid.DataMember%2A>プロパティ (どちらかとは別に、または、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッド)、またはプロパティには効果はありません。<br /><br /> プロパティは、0 より小さい値に設定できません。|  
    |<xref:System.Windows.Forms.DataGrid.RowHeaderWidth%2A>|グリッドの行ヘッダーの幅。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionBackColor%2A>|行またはセルを選択すると、これは、背景色。|  
    |<xref:System.Windows.Forms.DataGrid.SelectionForeColor%2A>|行またはセルを選択すると、これは、前景色。|  
  
    > [!NOTE]
    >  コントロールの色をカスタマイズする場合は、コントロールのため、不適切な色選択 (たとえば、赤と緑) にアクセスできないようにすることです。 使用できる色を使用して、**システム カラー**パレットに、この問題を回避します。

     次の手順が必要です、<xref:System.Windows.Forms.DataGrid>コントロールがデータ テーブルにバインドします。 詳細については、「[方法 :データ ソースに Windows フォーム DataGrid コントロールをバインド](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)します。

### <a name="to-set-the-table-and-column-style-of-a-data-table-at-design-time"></a>デザイン時にデータ テーブルのテーブルと列のスタイルを設定するには

1. 選択、<xref:System.Windows.Forms.DataGrid>フォーム上のコントロール。

2. **プロパティ**ウィンドウで、<xref:System.Windows.Forms.DataGrid.TableStyles%2A>プロパティをクリックして、**省略記号**(![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")) ボタンをクリックします。

3. **DataGridTableStyle コレクション エディター**ダイアログ ボックスで、をクリックして**追加**テーブル スタイルをコレクションに追加します。

     **DataGridTableStyle コレクション エディター**、追加することができますおよびマッピングが表スタイルの名前テーブル スタイルの削除、表示の設定とレイアウトのプロパティ セット。

4. 設定、<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>プロパティを各テーブルのスタイルのマッピングの名前にします。

     マッピングの名前は、どのテーブルで使用するテーブル スタイルを指定に使用されます。

5. **DataGridTableStyle コレクション エディター**を選択、<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>プロパティの省略記号ボタンをクリックします (![VisualStudioEllipsesButton スクリーン ショット](../media/vbellipsesbutton.png "vbEllipsesButton")).

6. **DataGridColumnStyle コレクション エディター**  ダイアログ ボックスで、列のスタイルを作成したテーブルのスタイルを追加します。

     **DataGridColumnStyle コレクション エディター**列のデータの文字列の書式設定、および追加し、列のスタイルを削除、表示とレイアウトのプロパティを設定およびマッピングの名前を設定します。

    > [!NOTE]
    >  文字列の書式設定に関する詳細については、次を参照してください。[型の書式設定](../../../standard/base-types/formatting-types.md)します。

## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [方法: Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid コントロール](datagrid-control-windows-forms.md)