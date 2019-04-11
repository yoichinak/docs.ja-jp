---
title: '方法: Windows フォーム DataGrid コントロールの書式を設定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], DataGrid control
- colors [Windows Forms], applying to DataGrid controls
- DataGrid control [Windows Forms], formatting
- columns [Windows Forms], formatting in DataGrid control
- DataGrid control [Windows Forms], default styles
- tables [Windows Forms], formatting in DataGrid control
- formatting [Windows Forms]
ms.assetid: a50fcc3b-8abf-47ec-9029-7f268af4ddb1
ms.openlocfilehash: 8e5c41d6f146e6abef8d7670e6191b587ac86c92
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59336123"
---
# <a name="how-to-format-the-windows-forms-datagrid-control"></a>方法: Windows フォーム DataGrid コントロールの書式を設定する
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 さまざまな部分に別の色を適用する、<xref:System.Windows.Forms.DataGrid>コントロールのことで情報を読みやすくするヘルプことができます。 色は、行と列に適用できます。 行と列も非表示にしたりユーザーの判断で示すようにします。  
  
 書式設定の 3 つの基本的な機能がある、<xref:System.Windows.Forms.DataGrid>コントロール。 データを表示する既定のスタイルを確立するためにプロパティを設定することができます。 そのベースから、実行時に特定のテーブルの表示方法をカスタマイズできます。 最後に、色と同様に、データ グリッドで表示する列を変更することができ、その他の書式を示します。  
  
 データ グリッドの書式設定に最初のステップとしてのプロパティを設定することができます、<xref:System.Windows.Forms.DataGrid>自体。 これらの色と書式の選択を加えることができますし、データ テーブルと表示される列によって、ベースを形成します。  
  
### <a name="to-establish-a-default-style-for-the-datagrid-control"></a>DataGrid コントロールの既定のスタイルを確立するには  
  
1. 必要に応じて、次のプロパティを設定します。  
  
    |プロパティ|説明|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>|<xref:System.Windows.Forms.DataGrid.BackColor%2A>プロパティ グリッドの偶数行の色を定義します。 設定すると、<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>プロパティを別の色は、その他のすべての行は、この新しい色に設定が (行 1、3、5、およびなど)。|  
    |<xref:System.Windows.Forms.DataGrid.BackColor%2A>|グリッドの偶数行の背景色 (0、2、4、6、および具合の行数)。|  
    |<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>|一方、<xref:System.Windows.Forms.DataGrid.BackColor%2A>と<xref:System.Windows.Forms.DataGrid.AlternatingBackColor%2A>プロパティ グリッドで行の色を決定する、<xref:System.Windows.Forms.DataGrid.BackgroundColor%2A>プロパティは、一番下のグリッドがスクロールされたとき、または少数の行に含まれるだけの場合にのみ表示 nonrow 領域の色を決定しますグリッドです。|  
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
    |<xref:System.Windows.Forms.DataGrid.HeaderForeColor%2A>|列ヘッダー テキストやプラス/マイナス グリフ (複数の関連テーブルが表示されるときに行を展開する) を含むグリッドの列ヘッダーの前景色。|  
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
    >  コントロールを不適切な色選択 (たとえば、赤と緑) ためにアクセスできないようにすることは、コントロールの色をカスタマイズする場合に、注意します。 使用できる色を使用して、**システム カラー**パレットに、この問題を回避します。  
  
     次の手順は、フォームに、<xref:System.Windows.Forms.DataGrid>コントロールがデータ テーブルにバインドします。 詳細については、次を参照してください。 [Windows フォームの DataGrid コントロールをデータ ソースにバインド](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)します。  
  
### <a name="to-set-the-table-and-column-style-of-a-data-table-programmatically"></a>データ テーブルのテーブルと列のスタイルをプログラムで設定するには  
  
1. 新しいテーブルのスタイルを作成し、そのプロパティを設定します。  
  
2. 列のスタイルを作成し、そのプロパティを設定します。  
  
3. テーブル スタイルの列スタイルのコレクションに列のスタイルを追加します。  
  
4. データ グリッドのテーブル スタイルのコレクションには、テーブルのスタイルを追加します。  
  
5. 次の例での新しいインスタンスを作成<xref:System.Windows.Forms.DataGridTableStyle>設定とその<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>プロパティ。  
  
6. 新しいインスタンスを作成、 **GridColumnStyle**設定とその**MappingName** (およびその他のいくつかのレイアウトと表示プロパティ)。  
  
7. 各列のスタイルを作成するには、手順 2. ~ 6. を繰り返します。  
  
     次の例を示して 方法、<xref:System.Windows.Forms.DataGridTextBoxColumn>名前が列に表示されるため、作成されます。 さらに、列のスタイルを追加、<xref:System.Windows.Forms.GridColumnStylesCollection>のテーブルのスタイルをテーブルのスタイルを追加して、<xref:System.Windows.Forms.GridTableStylesCollection>データ グリッドの。  
  
    ```vb  
    Private Sub CreateAuthorFirstNameColumn()  
       ' Add a GridTableStyle and set the MappingName   
       ' to the name of the DataTable.  
       Dim TSAuthors As New DataGridTableStyle()  
       TSAuthors.MappingName = "Authors"  
  
       ' Add a GridColumnStyle and set the MappingName   
       ' to the name of a DataColumn in the DataTable.   
       ' Set the HeaderText and Width properties.   
       Dim TCFirstName As New DataGridTextBoxColumn()  
       TCFirstName.MappingName = "AV_FName"  
       TCFirstName.HeaderText = "First Name"  
       TCFirstName.Width = 75  
       TSAuthors.GridColumnStyles.Add(TCFirstName)  
  
       ' Add the DataGridTableStyle instance to   
       ' the GridTableStylesCollection.   
       myDataGrid.TableStyles.Add(TSAuthors)  
    End Sub  
    ```  
  
    ```csharp  
    private void addCustomDataTableStyle()  
    {  
       // Add a GridTableStyle and set the MappingName   
       // to the name of the DataTable.  
       DataGridTableStyle TSAuthors = new DataGridTableStyle();  
       TSAuthors.MappingName = "Authors";  
  
       // Add a GridColumnStyle and set the MappingName   
       // to the name of a DataColumn in the DataTable.   
       // Set the HeaderText and Width properties.   
       DataGridColumnStyle TCFirstName = new DataGridTextBoxColumn();  
       TCFirstName.MappingName = " AV_FName";  
       TCFirstName.HeaderText = "First Name";  
       TCFirstName.Width = 75;  
       TSAuthors.GridColumnStyles.Add(TCFirstName);  
  
       // Add the DataGridTableStyle instance to   
       // the GridTableStylesCollection.   
       dataGrid1.TableStyles.Add(TSAuthors);  
    }  
    ```  
  
    ```cpp  
    private:  
       void addCustomDataTableStyle()  
       {  
          // Add a GridTableStyle and set the MappingName   
          // to the name of the DataTable.  
          DataGridTableStyle^ TSAuthors = new DataGridTableStyle();  
          TSAuthors->MappingName = "Authors";  
  
          // Add a GridColumnStyle and set the MappingName   
          // to the name of a DataColumn in the DataTable.   
          // Set the HeaderText and Width properties.   
          DataGridColumnStyle^ TCFirstName = gcnew DataGridTextBoxColumn();  
          TCFirstName->MappingName = "AV_FName";  
          TCFirstName->HeaderText = "First Name";  
          TCFirstName->Width = 75;  
          TSAuthors->GridColumnStyles->Add(TCFirstName);  
  
          // Add the DataGridTableStyle instance to   
          // the GridTableStylesCollection.   
          dataGrid1->TableStyles->Add(TSAuthors);  
       }  
    ```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Windows.Forms.GridTableStylesCollection>
- <xref:System.Windows.Forms.GridColumnStylesCollection>
- <xref:System.Windows.Forms.DataGrid>
- [方法: Windows フォーム DataGrid コントロールの列を削除するまたは非表示にする](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [DataGrid コントロール](datagrid-control-windows-forms.md)
