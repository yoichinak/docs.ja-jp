---
title: '方法: Windows フォーム DataGrid コントロールに表示されるデータを実行時に変更する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- DataGrid control [Windows Forms], dynamically changing at run time
- DataGrid control [Windows Forms], data binding
- cells [Windows Forms], changing DataGrid cell values
ms.assetid: 0c7a6d00-30de-416e-8223-0a81ddb4c1f8
ms.openlocfilehash: c7bf70a67729744f4cf96318f6b270a5ea81b812
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917725"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>方法: Windows フォーム DataGrid コントロールに表示されるデータを実行時に変更する
> [!NOTE]
> <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 デザイン時の機能を使用<xref:System.Windows.Forms.DataGrid>して Windows フォームを作成した後、実行時にグリッドの<xref:System.Data.DataSet>オブジェクトの要素を動的に変更することもできます。 これには、テーブルの個々の値への変更や、コントロールにバインドされて<xref:System.Windows.Forms.DataGrid>いるデータソースの変更が含まれる場合があります。 個々の値に対する変更は、 <xref:System.Data.DataSet> <xref:System.Windows.Forms.DataGrid>コントロールではなく、オブジェクトを介して行われます。  
  
### <a name="to-change-data-programmatically"></a>プログラムによってデータを変更するには  
  
1. <xref:System.Data.DataSet>オブジェクトから目的のテーブルを指定し、目的の行とフィールドをテーブルから指定して、セルを新しい値に設定します。  
  
    > [!NOTE]
    > テーブルの最初の行<xref:System.Data.DataSet>または最初の行を指定するには、0を使用します。  
  
     次の例では、をクリック`Button1`して、データセットの最初のテーブルの最初の行の2番目のエントリを変更する方法を示します。 ( <xref:System.Data.DataSet> `0` ) とテーブル (および`1`) は、以前に作成されています。`ds`  
  
    ```vb  
    Protected Sub Button1_Click(ByVal sender As System.Object, ByVal e As System.EventArgs) Handles Button1.Click  
       ds.tables(0).rows(0)(1) = "NewEntry"  
    End Sub  
    ```  
  
    ```csharp  
    private void button1_Click(object sender, System.EventArgs e)  
    {  
       ds.Tables[0].Rows[0][1]="NewEntry";  
    }  
    ```  
  
    ```cpp  
    private:   
       void button1_Click(System::Object^ sender, System::EventArgs^ e)  
       {  
          dataSet1->Tables[0]->Rows[0][1] = "NewEntry";  
       }  
    ```  
  
     (ビジュアルC#、ビジュアルC++)フォームのコンストラクターに次のコードを配置して、イベントハンドラーを登録します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     実行時に、 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッドを使用して、 <xref:System.Windows.Forms.DataGrid>コントロールを別のデータソースにバインドできます。 たとえば、複数の ADO.NET データコントロールがあり、それぞれが別のデータベースに接続されている場合があります。  
  
### <a name="to-change-the-datasource-programmatically"></a>プログラムによってデータソースを変更するには  
  
1. <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッドに、バインド先のデータソースおよびテーブルの名前を設定します。  
  
     次の例では、 <xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッドを使用して日付ソースを変更し、Pubs データベースの Authors テーブルに接続されている ADO.NET data control (adoPubsAuthors) に変換する方法を示します。  
  
    ```vb  
    Private Sub ResetSource()  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors")  
    End Sub  
    ```  
  
    ```csharp  
    private void ResetSource()  
    {  
       DataGrid1.SetDataBinding(adoPubsAuthors, "Authors");  
    }  
    ```  
  
    ```cpp  
    private:  
       void ResetSource()  
       {  
          dataGrid1->SetDataBinding(adoPubsAuthors, "Authors");  
       }  
    ```  
  
## <a name="see-also"></a>関連項目

- [ADO.NET データセット](../../data/adonet/ado-net-datasets.md)
- [方法: Windows フォーム DataGrid コントロールの列を削除または非表示にする](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [方法: Windows フォーム DataGrid コントロールにテーブルと列を追加する](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [方法: データソースへの Windows フォーム DataGrid コントロールのバインド](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
