---
title: DataTable の編集
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f08008a9-042e-4de9-94f3-4f0e502b1eb5
ms.openlocfilehash: 9e8c4204b51121b147fc7614066d9b849a687574
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151261"
---
# <a name="datatable-edits"></a>DataTable の編集
<xref:System.Data.DataRow> 内の列値を変更すると、その変更はすぐに行の現在の状態に反映されます。 <xref:System.Data.DataRowState>は Modified**に設定**され、変更は**DataRow**の<xref:System.Data.DataRow.AcceptChanges%2A>or<xref:System.Data.DataRow.RejectChanges%2A>メソッドを使用して受け入れられるか拒否されます。 **DataRow**には、編集中に行の状態を中断するために使用できる 3 つのメソッドも用意されています。 これらのメソッドとは、<xref:System.Data.DataRow.BeginEdit%2A>、<xref:System.Data.DataRow.EndEdit%2A> および <xref:System.Data.DataRow.CancelEdit%2A> です。  
  
 **DataRow**の列の値を直接変更すると **、DataRow**は **、現在**のバージョン、**既定**の行、**および元**の行のバージョンを使用して列の値を管理します。 これらの行バージョンに加えて、 **BeginEdit**、 **EndEdit**、および**CancelEdit**メソッドは 4 行目のバージョンを使用します:**提案済み**。 行バージョンの詳細については、「[行の状態」および「行バージョン](row-states-and-row-versions.md)」を参照してください。  
  
 **提案された**行のバージョンは **、BeginEdit**を呼び出すことによって開始し **、EndEdit**または**CancelEdit**を使用するか、**または AcceptChanges**または**RejectChanges**を呼び出すことによって終了する編集操作中に存在します。  
  
 編集操作中に **、DataTable**の**ColumnChanged**イベントで**提案値**を評価することで、個々の列に検証ロジックを適用できます。 **イベント**は、変更されている列への参照と**提案された値**への参照を保持する**DataColumnChangeEventArgs**を保持します。 提示された値を評価した後で、値を変更するか、または編集をキャンセルできます。 編集が終了すると、行は**提案済み**状態から外れます。  
  
 編集内容を確認するには **、EndEdit**を呼び出すか **、CancelEdit**を呼び出してキャンセルすることができます。 **EndEdit**は編集内容を確認**しますが、****データセットは、AcceptChanges**が呼び出されるまで、実際には変更を受け入れません。 また **、EndEdit**または**CancelEdit**で編集を終了する前に**AcceptChanges**を呼び出すと、編集は終了し、**提案された**行の値は**現在**の行と**元**の行のバージョンの両方で受け入れられます。 同様に **、RejectChanges を**呼び出すと、編集が終了し、**現在**の行と**提案された**行のバージョンが破棄されます。 **AcceptChanges**または**RejectChanges**を呼び出した後に**EndEdit**または**CancelEdit**を呼び出しても、編集は既に終了しているため、何の効果もありません。  
  
 次の例は **、EndEdit**と**CancelEdit**で**BeginEdit**を使用する方法を示しています。 この例では **、ColumnChanged**イベントの**提案値**もチェックし、編集をキャンセルするかどうかを決定します。  
  
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
- [ADO.NET の概要](../ado-net-overview.md)
