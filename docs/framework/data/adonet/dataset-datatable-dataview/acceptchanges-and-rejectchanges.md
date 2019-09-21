---
title: AcceptChange と RejectChange
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e2d1a6fe-31f9-4b83-9728-06c406a3394e
ms.openlocfilehash: c537fa808fc6ba4c740e71bfd70fe9cd1f3bd31a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785563"
---
# <a name="acceptchanges-and-rejectchanges"></a>AcceptChange と RejectChange
で<xref:System.Data.DataTable> <xref:System.Data.DataRow.AcceptChanges%2A>データに対して行われた変更の精度を確認した後、 <xref:System.Data.DataRow>、 <xref:System.Data.DataTable>、または<xref:System.Data.DataSet>のメソッドを使用して変更を受け入れることができます。これにより、**現在**の**行の値がに設定されます。元**の値は、 **RowState**プロパティを**Unchanged**に設定します。 変更の受け入れまたは拒否を行うと、 **RowError**情報がクリアされ、 **haserrors**プロパティが**false**に設定されます。 変更を受け入れるかまたは拒否した場合、データ ソース内で実行中の更新操作にも影響することがあります。 詳細については、「 [dataadapter を使用したデータソースの更新](../updating-data-sources-with-dataadapters.md)」を参照してください。  
  
 **DataTable**に foreign key 制約が存在する場合、 **AcceptChanges**と**RejectChanges**を使用して許可または拒否された変更は、 **DataRow**の子行に反映されます **。ForeignKeyConstraint AcceptRejectRule**。 詳細については、「 [DataTable の制約](datatable-constraints.md)」を参照してください。  
  
 行にエラーがあるかどうかをチェックし、必要に応じてエラーを解決し、エラーを解決できない場合にはその行を拒否する例を次に示します。 解決されたエラーについては、 **RowError**の値が空の文字列にリセットされ、 **haserrors**プロパティが**false**に設定されていることに注意してください。 エラーのあるすべての行が解決または拒否された場合、**データテーブル**全体のすべての変更を受け入れるために**AcceptChanges**が呼び出されます。  
  
```vb  
If workTable.HasErrors Then  
  Dim errRow As DataRow  
  
  For Each errRow in workTable.GetErrors()  
  
    If errRow.RowError = "Total cannot exceed 1000." Then  
      errRow("Total") = 1000  
      errRow.RowError = ""    ' Clear the error.  
    Else  
      errRow.RejectChanges()  
    End If  
  Next  
End If  
  
workTable.AcceptChanges()  
```  
  
```csharp  
if (workTable.HasErrors)  
{  
  
  foreach (DataRow errRow in workTable.GetErrors())  
  {  
    if (errRow.RowError == "Total cannot exceed 1000.")  
    {  
      errRow["Total"] = 1000;  
      errRow.RowError = "";    // Clear the error.  
    }  
    else  
      errRow.RejectChanges();  
  }  
}  
  
workTable.AcceptChanges();  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataRow>
- <xref:System.Data.DataSet>
- <xref:System.Data.DataTable>
- [DataTable 内のデータの操作](manipulating-data-in-a-datatable.md)
- [ADO.NET の概要](../ado-net-overview.md)
