---
title: '方法: 削除、または Windows フォームの DataGrid コントロール内の列を非表示にします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], deleting columns
- DataGrid control [Windows Forms], deleting columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
- columns [Windows Forms], deleting in data grids
- DataGrid control [Windows Forms], hiding columns
ms.assetid: bcd0dd96-6687-4c48-b0e1-d5287b93ac91
ms.openlocfilehash: 42a697992d4c6c75fe5958a7a17d6df8a7b4f6e4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724517"
---
# <a name="how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control"></a>方法: 削除、または Windows フォームの DataGrid コントロール内の列を非表示にします。
> [!NOTE]
>  
  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 プログラムで削除するか、Windows フォーム内の列を非表示に<xref:System.Windows.Forms.DataGrid>コントロールのメソッドとプロパティを使用して、<xref:System.Windows.Forms.GridColumnStylesCollection>と<xref:System.Windows.Forms.DataGridColumnStyle>オブジェクト (のメンバーである、<xref:System.Windows.Forms.DataGridTableStyle>クラス)。  
  
 削除または非表示の列は、グリッドにバインドされていて、プログラムでアクセスできるデータ ソースにまだ存在します。 なくなるだけデータ グリッドに表示されます。  
  
> [!NOTE]
>  アプリケーションが特定の列のデータにアクセスしないデータ グリッドに表示しない場合は、し、おそらく必要はありません、最初に、データ ソースに含める。  
  
### <a name="to-delete-a-column-from-the-datagrid-programmatically"></a>データ グリッドから列をプログラムで削除するには  
  
1.  フォームの宣言領域内の新しいインスタンスを宣言、<xref:System.Windows.Forms.DataGridTableStyle>クラス。  
  
2.  設定、<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A?displayProperty=nameWithType>プロパティ、スタイルを適用するデータ ソース内のテーブルにします。 次の例では、<xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>プロパティで、既に設定されていることを前提としています。  
  
3.  新しい追加<xref:System.Windows.Forms.DataGridTableStyle>へ datagrid のテーブルのスタイルのコレクション オブジェクト。  
  
4.  呼び出す、<xref:System.Windows.Forms.GridColumnStylesCollection.RemoveAt%2A>のメソッド、<xref:System.Windows.Forms.DataGrid>の<xref:System.Windows.Forms.DataGridTableStyle.GridColumnStyles%2A>コレクションを削除する列の列インデックスを指定します。  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub DeleteColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Delete the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles.RemoveAt(0)  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void deleteColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Delete the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles.RemoveAt(0);  
    }  
    ```  
  
### <a name="to-hide-a-column-in-the-datagrid-programmatically"></a>DataGrid の列をプログラムで非表示にするには  
  
1.  フォームの宣言領域内の新しいインスタンスを宣言、<xref:System.Windows.Forms.DataGridTableStyle>クラス。  
  
2.  設定、<xref:System.Windows.Forms.DataGridTableStyle.MappingName%2A>のプロパティ、<xref:System.Windows.Forms.DataGridTableStyle>スタイルを適用するデータ ソース内のテーブルにします。 次のコード例では、<xref:System.Windows.Forms.DataGrid.DataMember%2A?displayProperty=nameWithType>プロパティで、既に設定されていることを前提としています。  
  
3.  新しい追加<xref:System.Windows.Forms.DataGridTableStyle>へ datagrid のテーブルのスタイルのコレクション オブジェクト。  
  
4.  設定して、列を非表示にその`Width`プロパティを非表示にする列の列インデックスを指定する 0 にします。  
  
    ```vb  
    ' Declare a new DataGridTableStyle in the  
    ' declarations area of your form.  
    Dim ts As DataGridTableStyle = New DataGridTableStyle()  
  
    Sub HideColumn()  
       ' Set the DataGridTableStyle.MappingName property  
       ' to the table in the data source to map to.  
       ts.MappingName = DataGrid1.DataMember  
  
       ' Add it to the datagrid's TableStyles collection  
       DataGrid1.TableStyles.Add(ts)  
  
       ' Hide the first column (index 0)  
       DataGrid1.TableStyles(0).GridColumnStyles(0).Width = 0  
    End Sub  
    ```  
  
    ```csharp  
    // Declare a new DataGridTableStyle in the  
    // declarations area of your form.  
    DataGridTableStyle ts = new DataGridTableStyle();  
  
    private void hideColumn()  
    {  
       // Set the DataGridTableStyle.MappingName property  
       // to the table in the data source to map to.  
       ts.MappingName = dataGrid1.DataMember;  
  
       // Add it to the datagrid's TableStyles collection  
       dataGrid1.TableStyles.Add(ts);  
  
       // Hide the first column (index 0)  
       dataGrid1.TableStyles[0].GridColumnStyles[0].Width = 0;  
    }  
    ```  
  
## <a name="see-also"></a>関連項目
- [方法: Windows フォーム DataGrid コントロールでの実行時に表示されるデータの変更](change-displayed-data-at-run-time-wf-datagrid-control.md)
- [方法: Windows フォームの DataGrid コントロールにテーブルと列を追加します。](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
