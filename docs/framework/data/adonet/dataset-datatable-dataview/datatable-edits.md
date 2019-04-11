---
title: DataTable の編集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 0300ceab16d9a94bd04468f7acd105e69d13e643
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150944"
---
# <a name="datatable-edits"></a>DataTable の編集
<xref:System.Data.DataRow> 内の列値を変更すると、その変更はすぐに行の現在の状態に反映されます。 <xref:System.Data.DataRowState>に設定されている、 **Modified**、され、変更が受け入れられますまたは拒否を使用して、<xref:System.Data.DataRow.AcceptChanges%2A>または<xref:System.Data.DataRow.RejectChanges%2A>のメソッド、 **DataRow**します。 **DataRow**を編集しているときに、行の状態を中断するのに使用できる 3 つのメソッドも提供されます。 これらのメソッドとは、<xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> および <xref:System.Data.DataRow.CancelEdit%2A> です。  
  
 列の値を変更する場合、 **DataRow**を直接、 **DataRow**を使用して列の値を管理、**現在**、**既定**と**元**行のバージョン。 これらの行のバージョンだけでなく、 **BeginEdit**、 **EndEdit**、および**CancelEdit**メソッドを使用して、4 番目の行のバージョン。**提案された**します。 行のバージョンの詳細については、次を参照してください。[行の状態と行バージョン](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-states-and-row-versions.md)します。  
  
 **提案済み**呼び出しによって開始編集操作中に行バージョンが存在する**BeginEdit**を使用するか終了して**EndEdit**または**CancelEdit**または呼び出すことによって**AcceptChanges**または**RejectChanges**します。  
  
 編集操作中に適用できます検証ロジックの個々 の列を評価することによって、 **ProposedValue**で、 **ColumnChanged**のイベント、 **DataTable**します。 **ColumnChanged**イベントを保持**DataColumnChangeEventArgs**変更されている列をする参照を保持する、 **ProposedValue**します。 提示された値を評価した後で、値を変更するか、または編集をキャンセルできます。 うち、行が移動、編集が終了したとき、**提案済み**状態。  
  
 編集内容を確認するには呼び出すことによって**EndEdit**、呼び出すことによって、それらをキャンセルできます**CancelEdit**します。 注意してください**EndEdit**が編集内容を確認して、**データセット**まで変更を実際には受け入れません**AcceptChanges**が呼び出されます。 なおを呼び出す場合**AcceptChanges**で編集を終了する前に**EndEdit**または**CancelEdit**、編集を終了し、 **提案済み**両方の行の値を受け入れる、**現在**と**元**行のバージョン。 同様に、呼び出す**RejectChanges**編集を終了し、破棄、**現在**と**提案済み**行のバージョン。 呼び出す**EndEdit**または**CancelEdit**呼び出した後**AcceptChanges**または**RejectChanges**編集が既にあるため、影響を与えません終了しました。  
  
 次の例を使用する方法を示します**BeginEdit**で**EndEdit**と**CancelEdit**します。 例もチェック、 **ProposedValue**で、 **ColumnChanged**イベントされ、編集をキャンセルするかどうかを決定します。  
  
```vb  
Dim workTable As DataTable = New DataTable  
workTable.Columns.Add("LastName", Type.GetType("System.String"))  
  
AddHandler workTable.ColumnChanged, _  
  New DataColumnChangeEventHandler(AddressOf OnColumnChanged)  
  
Dim workRow As DataRow = workTable.NewRow()  
workRow(0) = "Smith"  
workTable.Rows.Add(workRow)  
  
workRow.BeginEdit()  
' Causes the ColumnChanged event to write a message and cancel the edit.  
workRow(0) = ""       
workRow.EndEdit()  
  
' Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow(0), workRow.RowState)  
  
Private Shared Sub OnColumnChanged( _  
  sender As Object, args As DataColumnChangeEventArgs)  
  If args.Column.ColumnName = "LastName" Then  
    If args.ProposedValue.ToString() = "" Then  
      Console.WriteLine("Last Name cannot be blank.  Edit canceled.")  
      args.Row.CancelEdit()  
    End If  
  End If  
End Sub  
```  
  
```csharp  
DataTable workTable  = new DataTable();  
workTable.Columns.Add("LastName", typeof(String));  
  
workTable.ColumnChanged +=   
  new DataColumnChangeEventHandler(OnColumnChanged);  
  
DataRow workRow = workTable.NewRow();  
workRow[0] = "Smith";  
workTable.Rows.Add(workRow);  
  
workRow.BeginEdit();  
// Causes the ColumnChanged event to write a message and cancel the edit.  
workRow[0] = "";       
workRow.EndEdit();  
  
// Displays "Smith, New".  
Console.WriteLine("{0}, {1}", workRow[0], workRow.RowState);    
  
protected static void OnColumnChanged(  
  Object sender, DataColumnChangeEventArgs args)  
{  
  if (args.Column.ColumnName == "LastName")  
    if (args.ProposedValue.ToString() == "")  
    {  
      Console.WriteLine("Last Name cannot be blank. Edit canceled.");  
      args.Row.CancelEdit();  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataRow>
- <xref:System.Data.DataTable>
- <xref:System.Data.DataRowVersion>
- [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [DataTable イベントの処理](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/handling-datatable-events.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
