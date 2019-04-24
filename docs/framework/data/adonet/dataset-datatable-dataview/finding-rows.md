---
title: 行の検索
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: 72af4b049153ce647cc1ceb2d40c3b17cc7ed988
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59206552"
---
# <a name="finding-rows"></a>行の検索
<xref:System.Data.DataView.Find%2A> の <xref:System.Data.DataView.FindRows%2A> メソッドと <xref:System.Data.DataView> メソッドを使用すると、並べ替えキーの値に基づいて行を検索できます。 値の検索の大文字小文字の区別、**検索**と**FindRows**メソッドはによって決定されます、 **CaseSensitive** 、基になるプロパティ<xref:System.Data.DataTable>します。 検索結果を返すには、検索値が既存の並べ替えキーの値と完全に一致している必要があります。  
  
 **検索**メソッドのインデックスを持つ整数を返します、<xref:System.Data.DataRowView>検索条件に一致します。 1 つ以上の行が一致した最初のインデックスのみである検索条件と一致する場合**DataRowView**が返されます。 一致が見つからない場合**検索**-1 を返します。  
  
 使用して、複数の行に一致する検索結果を返す、 **FindRows**メソッド。 **FindRows**同様の機能、**検索**メソッドを返す点を除いて、 **DataRowView**一致するすべての行を参照する配列、 **DataView**します。 一致が見つからない場合、 **DataRowView**配列は空になります。  
  
 使用する、**検索**または**FindRows**並べ替え順を指定する必要がありますメソッド順序を設定して**ApplyDefaultSort**に**true**またはを使用して、**並べ替え**プロパティ。 並べ替え順序が指定されないと、例外がスローされます。  
  
 **検索**と**FindRows**メソッドは、長さが、並べ替え順序の列の数と一致する入力として値の配列を取得します。 1 つの列に基づく並べ替えの場合は、1 つの値を渡します。 複数列に基づく並べ替えの場合は、オブジェクトの配列を渡します。 複数の列で並べ替えには、オブジェクトの配列内の値と一致するがで指定された列の順序に注意してください、**並べ替え**のプロパティ、 **DataView**します。  
  
 次のコード例は、**検索**に対して呼び出されるメソッドを**DataView**で 1 つの列の並べ替え順序。  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName", DataViewRowState.CurrentRows)  
  
Dim rowIndex As Integer = custView.Find("The Cracker Box")  
  
If rowIndex = -1 Then  
  Console.WriteLine("No match found.")  
Else  
  Console.WriteLine("{0}, {1}", _  
    custView(rowIndex)("CustomerID").ToString(), _  
    custView(rowIndex)("CompanyName").ToString())  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",   
  "CompanyName", DataViewRowState.CurrentRows);  
  
int rowIndex = custView.Find("The Cracker Box");  
  
if (rowIndex == -1)  
  Console.WriteLine("No match found.");  
else  
  Console.WriteLine("{0}, {1}",  
    custView[rowIndex]["CustomerID"].ToString(),  
    custView[rowIndex]["CompanyName"].ToString());  
```  
  
 場合、**並べ替え**プロパティが複数の列を指定しますで指定された順序で各列の検索値でオブジェクトの配列を渡す必要があります、**並べ替え**プロパティは、次のコード例に示すようにします。  
  
```vb  
Dim custView As DataView = _  
  New DataView(custDS.Tables("Customers"), "", _  
  "CompanyName, ContactName", _  
  DataViewRowState.CurrentRows)  
  
Dim foundRows() As DataRowView = _  
  custView.FindRows(New object() {"The Cracker Box", "Liu Wong"})  
  
If foundRows.Length = 0 Then  
  Console.WriteLine("No match found.")  
Else  
  Dim myDRV As DataRowView  
  For Each myDRV In foundRows  
    Console.WriteLine("{0}, {1}", _  
      myDRV("CompanyName").ToString(), myDRV("ContactName").ToString())  
  Next  
End If  
```  
  
```csharp  
DataView custView = new DataView(custDS.Tables["Customers"], "",  
  "CompanyName, ContactName",  
  DataViewRowState.CurrentRows);  
  
DataRowView[] foundRows =   
  custView.FindRows(new object[] {"The Cracker Box", "Liu Wong"});  
  
if (foundRows.Length == 0)  
  Console.WriteLine("No match found.");  
else  
  foreach (DataRowView myDRV in foundRows)  
    Console.WriteLine("{0}, {1}", myDRV["CompanyName"].ToString(),   
      myDRV["ContactName"].ToString());  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
