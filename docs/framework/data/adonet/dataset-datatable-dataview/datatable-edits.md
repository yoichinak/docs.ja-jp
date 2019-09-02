---
title: DataTable の編集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: a970ebda76f5bb6bdea704dabef2ee305436c613
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205017"
---
# <a name="datatable-edits"></a>DataTable の編集
<xref:System.Data.DataRow> 内の列値を変更すると、その変更はすぐに行の現在の状態に反映されます。 次<xref:System.Data.DataRowState>に、が**Modified**に設定され、 <xref:System.Data.DataRow.AcceptChanges%2A> **DataRow**のメソッドまたは<xref:System.Data.DataRow.RejectChanges%2A>メソッドを使用して変更が受け入れられるか拒否されます。 **DataRow**には、編集中に行の状態を中断するために使用できる3つのメソッドも用意されています。 これらのメソッドとは、<xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> および <xref:System.Data.DataRow.CancelEdit%2A> です。  
  
 **Datarow**内の列の値を直接変更すると、 **Datarow**は、**現在**、**既定**、および**元**の行バージョンを使用して列の値を管理します。 これらの行バージョンに加えて、 **BeginEdit**、 **EndEdit**、および**CancelEdit**メソッドでは、4番目の行バージョンが使用されます。**提案済み**。 行バージョンの詳細については、「[行の状態と行のバージョン](row-states-and-row-versions.md)」を参照してください。  
  
 **提案**された行バージョンは、編集操作中に存在します。これは、 **EndEdit**または**CancelEdit**を使用するか、または**AcceptChanges**または**RejectChanges**を呼び出して、 **BeginEdit**を呼び出して開始します。  
  
 編集操作中に、 **DataTable**の**Columnchanged**イベントの**ProposedValue**を評価することによって、個々の列に検証ロジックを適用できます。 **Columnchanged**イベントは、変更されている列と**ProposedValue**に参照を保持する**DataColumnChangeEventArgs**を保持します。 提示された値を評価した後で、値を変更するか、または編集をキャンセルできます。 編集が終了すると、行は**提案**された状態から移動します。  
  
 **EndEdit**を呼び出すことで編集を確認できます。または、 **CancelEdit**を呼び出して、編集を取り消すこともできます。 **EndEdit**が編集内容を確認しても、 **AcceptChanges**が呼び出されるまで、**データセット**は実際には変更を受け入れないことに注意してください。 また、 **EndEdit**または**CancelEdit**で編集を終了する前に**AcceptChanges**を呼び出すと、編集が終了し、**現在**の行バージョンと**元**の行バージョンの両方に対して、**提案**された行の値が受け入れられます。 同様に、 **RejectChanges**を呼び出すと、編集が終了し、**現在**の行バージョンと**提案**された行バージョンが破棄されます。 **AcceptChanges**または**RejectChanges**を呼び出した後に**EndEdit**または**CancelEdit**を呼び出すと、編集が既に終了しているため、効果はありません。  
  
 次の例は、 **EndEdit**と**CancelEdit**での**BeginEdit**の使用方法を示しています。 また、この例では、 **Columnchanged**イベントの**ProposedValue**を確認し、編集を取り消すかどうかを決定します。  
  
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
- [DataTable 内のデータの操作](manipulating-data-in-a-datatable.md)
- [DataTable イベントの処理](handling-datatable-events.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
