---
title: '方法: Windows フォーム DataGrid コントロールでマスター/詳細リストを作成します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- master-details lists
- DataGrid control [Windows Forms], master-details lists
- related tables [Windows Forms], displaying in DataGrid control
ms.assetid: 20388c6a-94f9-4d96-be18-8c200491247f
ms.openlocfilehash: 8f247fb3e61abe46b3bb9c74a3b984310d2b99b3
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57715465"
---
# <a name="how-to-create-masterdetail-lists-with-the-windows-forms-datagrid-control"></a>方法: Windows フォーム DataGrid コントロールを使用してマスター/詳細リストを作成します。
> [!NOTE]
>  
  <xref:System.Windows.Forms.DataGridView> コントロールは、<xref:System.Windows.Forms.DataGrid> コントロールに代わると共に追加の機能を提供します。ただし、<xref:System.Windows.Forms.DataGrid> コントロールは、下位互換性を保つ目的および将来使用する目的で保持されます。 詳細については、「[Windows フォームの DataGridView コントロールと DataGrid コントロールの違いについて](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)」を参照してください。  
  
 場合、<xref:System.Data.DataSet>は一連の関連テーブルの 2 つ使用できます<xref:System.Windows.Forms.DataGrid>マスター/詳細形式でデータを表示するコントロール。 1 つ<xref:System.Windows.Forms.DataGrid>マスター グリッドに指定し、2 つ目は詳細グリッドに指定します。 マスター リストのエントリを選択すると、すべての関連する子エントリ、詳細の一覧に表示されます。 たとえば場合、 <xref:System.Data.DataSet> Customers テーブルと関連する Orders テーブルを含むマスター グリッドに Customers テーブルと Orders テーブル詳細グリッドに指定します。 マスター グリッドから顧客を選択すると、すべての Orders テーブルでは、その顧客に関連付けられている注文の詳細グリッドで表示されます。  
  
### <a name="to-set-a-masterdetail-relationship-programmatically"></a>プログラムでマスター/詳細リレーションシップを設定するには  
  
1.  新しい 2 つ作成<xref:System.Windows.Forms.DataGrid>を制御し、そのプロパティを設定します。  
  
2.  データセットにテーブルを追加します。  
  
3.  型の変数を宣言<xref:System.Data.DataRelation>を作成するリレーションシップを表します。  
  
4.  リレーションシップの名前を指定して、テーブル、列、および 2 つのテーブルに関連付けられるアイテムを指定することによって、リレーションシップをインスタンス化します。  
  
5.  リレーションシップを追加、<xref:System.Data.DataSet>オブジェクトの<xref:System.Data.DataSet.Relations%2A>コレクション。  
  
6.  使用して、<xref:System.Windows.Forms.DataGrid.SetDataBinding%2A>のメソッド、<xref:System.Windows.Forms.DataGrid>のグリッドの各バインドに、<xref:System.Data.DataSet>します。  
  
     次の例は、以前に生成されたで顧客と注文テーブル間のマスター/詳細リレーションシップを設定する方法を示します<xref:System.Data.DataSet>(`ds`)。  
  
    ```vb  
    Dim myDataRelation As DataRelation  
    myDataRelation = New DataRelation _  
       ("CustOrd", ds.Tables("Customers").Columns("CustomerID"), _  
       ds.Tables("Orders").Columns("CustomerID"))  
    ' Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation)  
    GridOrders.SetDataBinding(ds, "Customers")  
    GridDetails.SetDataBinding(ds, "Customers.CustOrd")  
    ```  
  
    ```csharp  
    DataRelation myDataRelation;  
    myDataRelation = new DataRelation("CustOrd", ds.Tables["Customers"].Columns["CustomerID"], ds.Tables["Orders"].Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds.Relations.Add(myDataRelation);  
    GridOrders.SetDataBinding(ds,"Customers");  
    GridDetails.SetDataBinding(ds,"Customers.CustOrd");  
    ```  
  
    ```cpp  
    DataRelation^ myDataRelation;  
    myDataRelation = gcnew DataRelation("CustOrd",  
       ds->Tables["Customers"]->Columns["CustomerID"],  
       ds->Tables["Orders"]->Columns["CustomerID"]);  
    // Add the relation to the DataSet.  
    ds->Relations->Add(myDataRelation);  
    GridOrders->SetDataBinding(ds, "Customers");  
    GridDetails->SetDataBinding(ds, "Customers.CustOrd");  
    ```  
  
## <a name="see-also"></a>関連項目
- [DataGrid コントロール](datagrid-control-windows-forms.md)
- [DataGrid コントロールの概要](datagrid-control-overview-windows-forms.md)
- [方法: Windows フォームの DataGrid コントロールをデータ ソースにバインドします。](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)
