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
ms.openlocfilehash: 60ba1e9304320346d505f3f73e1ba93ff6edab63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61961656"
---
# <a name="how-to-change-displayed-data-at-run-time-in-the-windows-forms-datagrid-control"></a>方法: Windows フォーム DataGrid コントロールに表示されるデータを実行時に変更する
> [!NOTE]
>  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 Windows フォームを作成した後<xref:System.Windows.Forms.DataGrid>デザイン時機能を使用することも考えの要素を動的に変更する、<xref:System.Data.DataSet>実行時にグリッドのオブジェクト。 これは、テーブルのいずれかの個別の値の変更を含めることができますかにバインドされているデータ ソースを変更する、<xref:System.Windows.Forms.DataGrid>コントロール。 個々 の値への変更が完了したら、<xref:System.Data.DataSet>オブジェクトは、<xref:System.Windows.Forms.DataGrid>コントロール。  
  
### <a name="to-change-data-programmatically"></a>プログラムでデータを変更するには  
  
1. 目的のテーブルの指定、<xref:System.Data.DataSet>オブジェクトおよび必要な行しテーブルのフィールドし、セルを新しい値に設定します。  
  
    > [!NOTE]
    >  最初のテーブルを指定する、<xref:System.Data.DataSet>か、テーブルの最初の行は 0 を使用します。  
  
     次の例をクリックして、データセットの最初のテーブルの最初の行の 2 番目のエントリを変更する方法を示しています。`Button1`します。 <xref:System.Data.DataSet> (`ds`) とテーブル (`0`と`1`) 以前に作成されました。  
  
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
  
     (Visual c#、 [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)])、イベント ハンドラーを登録するフォームのコンス トラクターで、次のコードを配置します。  
  
    ```csharp  
    this.button1.Click += new System.EventHandler(this.button1_Click);  
    ```  
  
    ```cpp  
    this->button1->Click +=  
       gcnew System::EventHandler(this, &Form1::button1_Click);  
    ```  
  
     実行時に使用することができます、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>にバインドするメソッド、<xref:System.Windows.Forms.DataGrid>別のデータ ソースを制御します。 たとえば、いくつかする必要があります[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]データ コントロールでは、それぞれ別のデータベースに接続します。  
  
### <a name="to-change-the-datasource-programmatically"></a>データ ソースをプログラムで変更するには  
  
1. 設定、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッドをデータ ソースにバインドするテーブルの名前。  
  
     次の例は、日付を使用してソースを変更する方法を示します、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>メソッドを[!INCLUDE[vstecado](../../../../includes/vstecado-md.md)]Pubs データベースの Authors テーブルに接続されているデータ コントロール (adoPubsAuthors)。  
  
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
- [方法: 削除、または Windows フォームの DataGrid コントロール内の列を非表示にします。](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)
- [方法: Windows フォームの DataGrid コントロールにテーブルと列を追加します。](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)
- [方法: Windows フォームの DataGrid コントロールをデータ ソースにバインドします。](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
