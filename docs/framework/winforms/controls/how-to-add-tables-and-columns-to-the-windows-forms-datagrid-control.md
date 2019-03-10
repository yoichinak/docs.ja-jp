---
title: '方法: Windows フォームの DataGrid コントロールにテーブルと列を追加します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- columns [Windows Forms], adding to DataGrid control
- tables [Windows Forms], adding to DataGrid control
- DataGrid control [Windows Forms], adding tables and columns
ms.assetid: 2fe661b9-aa06-49b9-a314-a0d3cbfdcb4d
ms.openlocfilehash: e222227d6283555fa4ec25fe1e5d8e661296034f
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709160"
---
# <a name="how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control"></a>方法: Windows フォームの DataGrid コントロールにテーブルと列を追加します。
> [!NOTE]
>  
  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 データを表示するには、Windows フォームで<xref:System.Windows.Forms.DataGrid>テーブルと列を作成してコントロール**DataGridTableStyle**オブジェクトと追加すること、 **GridTableStylesCollection**となるオブジェクト使用してアクセス、<xref:System.Windows.Forms.DataGrid>コントロールの**TableStyles**プロパティ。 各テーブルのスタイルがで指定されたは、どのようなデータ テーブルの内容を表示、 **DataGridTableStyle**オブジェクトの**MappingName**プロパティ。 既定では、テーブルのスタイルが指定されていない列スタイルを使用するデータ テーブル内のすべての列が表示されます。 追加することで表示するテーブルから列を制限する**DataGridColumnStyle**オブジェクトを**GridColumnStylesCollection**オブジェクトを通じてアクセスされる、 **GridColumnStyles**の各プロパティ**DataGridTableStyle**オブジェクト。  
  
### <a name="to-add-a-table-and-column-to-a-datagrid-programmatically"></a>データ グリッドにテーブルと列をプログラムで追加するには  
  
1.  テーブルにデータを表示するにはまず、<xref:System.Windows.Forms.DataGrid>データセットへのコントロール。 詳細については、「[方法 :データ ソースに Windows フォーム DataGrid コントロールをバインド](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)します。  
  
    > [!CAUTION]
    >  列のスタイルをプログラムで指定するには、ときに常に作成**DataGridColumnStyle**オブジェクトに追加して、 **GridColumnStylesCollection**オブジェクトを追加する前に**DataGridTableStyle**オブジェクトを**GridTableStylesCollection**オブジェクト。 空の追加と**DataGridTableStyle**オブジェクトをコレクションに**DataGridColumnStyle**オブジェクトが自動的に生成します。 新規追加しようとする場合に例外がスローされます、 **DataGridColumnStyle**重複オブジェクト**MappingName**値を**GridColumnStylesCollection**オブジェクト。  
  
2.  新しいテーブルのスタイルを宣言し、そのマッピングの名前を設定します。  
  
    ```vb  
    Dim ts1 As New DataGridTableStyle()  
    ts1.MappingName = "Customers"  
    ```  
  
    ```csharp  
    DataGridTableStyle ts1 = new DataGridTableStyle();  
    ts1.MappingName = "Customers";  
    ```  
  
    ```cpp  
    DataGridTableStyle* ts1 = new DataGridTableStyle();  
    ts1->MappingName = S"Customers";  
    ```  
  
3.  新しい列のスタイルを宣言し、そのマッピングの名前とその他のプロパティを設定します。  
  
    ```vb  
    Dim myDataCol As New DataGridBoolColumn()  
    myDataCol.HeaderText = "My New Column"  
    myDataCol.MappingName = "Current"  
    ```  
  
    ```csharp  
    DataGridBoolColumn myDataCol = new DataGridBoolColumn();  
    myDataCol.HeaderText = "My New Column";  
    myDataCol.MappingName = "Current";  
    ```  
  
    ```cpp  
    DataGridBoolColumn^ myDataCol = gcnew DataGridBoolColumn();  
    myDataCol->HeaderText = "My New Column";  
    myDataCol->MappingName = "Current";  
    ```  
  
4.  呼び出す、**追加**のメソッド、 **GridColumnStylesCollection**テーブルのスタイルに列を追加するオブジェクト  
  
    ```vb  
    ts1.GridColumnStyles.Add(myDataCol)  
    ```  
  
    ```csharp  
    ts1.GridColumnStyles.Add(myDataCol);  
    ```  
  
    ```cpp  
    ts1->GridColumnStyles->Add(myDataCol);  
    ```  
  
5.  呼び出す、**追加**のメソッド、 **GridTableStylesCollection**データ グリッドにテーブルのスタイルを追加するオブジェクト。  
  
    ```vb  
    DataGrid1.TableStyles.Add(ts1)  
    ```  
  
    ```csharp  
    dataGrid1.TableStyles.Add(ts1);  
    ```  
  
    ```cpp  
    dataGrid1->TableStyles->Add(ts1);  
    ```  
  
## <a name="see-also"></a>関連項目
- [DataGrid コントロール](datagrid-control-windows-forms.md)
- [方法: 削除、または Windows フォームの DataGrid コントロール内の列を非表示にします。](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
