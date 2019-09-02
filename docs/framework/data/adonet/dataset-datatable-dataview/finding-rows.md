---
title: 行の検索
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 5da300e2-74c0-4d13-9202-fc20ed8212d8
ms.openlocfilehash: 2ff2b6b6d00c854d07f36d37986268a388c7f31b
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203716"
---
# <a name="finding-rows"></a>行の検索
<xref:System.Data.DataView.Find%2A> の <xref:System.Data.DataView.FindRows%2A> メソッドと <xref:System.Data.DataView> メソッドを使用すると、並べ替えキーの値に基づいて行を検索できます。 **Find**メソッドと**FindRows**メソッドの検索値の大文字と小文字の区別は、基になる<xref:System.Data.DataTable>の**CaseSensitive**プロパティによって決定されます。 検索結果を返すには、検索値が既存の並べ替えキーの値と完全に一致している必要があります。  
  
 **Find**メソッドは、検索条件に一致<xref:System.Data.DataRowView>するのインデックスを持つ整数を返します。 複数の行が検索条件に一致する場合は、最初に一致した**DataRowView**のインデックスのみが返されます。 一致するものが見つからない場合は、-1 が返されます。  
  
 複数の行に一致する検索結果を返すには、 **FindRows**メソッドを使用します。 **FindRows**は、**検索**メソッドと同様に機能しますが、 **DataView**内の一致するすべての行を参照する**DataRowView**配列を返す点が異なります。 一致するものが見つからない場合、 **DataRowView**配列は空になります。  
  
 **Find**メソッドまたは**FindRows**メソッドを使用するには、 **applydefaultsort**を**true**に設定するか、 **sort**プロパティを使用して、並べ替え順序を指定する必要があります。 並べ替え順序が指定されないと、例外がスローされます。  
  
 **Find**メソッドと**FindRows**メソッドは、並べ替え順序の列数と長さが一致する値の配列を入力として受け取ります。 1 つの列に基づく並べ替えの場合は、1 つの値を渡します。 複数列に基づく並べ替えの場合は、オブジェクトの配列を渡します。 複数の列の並べ替えでは、オブジェクト配列内の値が**DataView**の**sort**プロパティで指定された列の順序と一致する必要があることに注意してください。  
  
 次のコード例は、単一の列の並べ替え順序を持つ**DataView**に対して呼び出される**Find**メソッドを示しています。  
  
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
  
 **Sort**プロパティで複数の列を指定する場合は、次のコード例のように、 **sort**プロパティで指定された順序で各列の検索値を含むオブジェクト配列を渡す必要があります。  
  
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
- [DataViews](dataviews.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
