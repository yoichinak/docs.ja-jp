---
title: DataView の変更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 3e811410ea9fdd4be0cbd84b895483f69f58b0d0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786046"
---
# <a name="modifying-dataviews"></a>DataView の変更
<xref:System.Data.DataView> を使用して、データ行を基になるテーブルに追加、削除、または変更できます。 **Dataview**を使用して基になるテーブルのデータを変更する機能は、 **dataview**の3つのブール型プロパティのいずれかを設定することによって制御されます。 この 3 つのプロパティとは、<xref:System.Data.DataView.AllowNew%2A>、<xref:System.Data.DataView.AllowEdit%2A> および <xref:System.Data.DataView.AllowDelete%2A> です。 既定では、これらは**true**に設定されています。  
  
 **AllowNew**が**true**の場合、 **DataView**のメソッド<xref:System.Data.DataView.AddNew%2A>を使用して新しい<xref:System.Data.DataRowView>を作成できます。 <xref:System.Data.DataTable> **DataRowView**の<xref:System.Data.DataRowView.EndEdit%2A>メソッドが呼び出されるまで、新しい行が基になるに実際に追加されるわけではないことに注意してください。 <xref:System.Data.DataRowView.CancelEdit%2A> **DataRowView**のメソッドが呼び出されると、新しい行は破棄されます。 同時に編集できる**DataRowView**は1つだけであることにも注意してください。 保留中の行が存在するときに**DataRowView**の**AddNew**メソッドまたは**BeginEdit**メソッドを呼び出すと、保留中の行に対して**EndEdit**が暗黙的に呼び出されます。 **EndEdit**を呼び出すと、変更は基になる**datatable**に適用され、後で**datatable**、DataSet、または**データセット**の**AcceptChanges**メソッドまたは **RejectChanges メソッドを使用してコミットまたは拒否できます。DataRow**オブジェクト。 **AllowNew**が**false**の場合、 **DataRowView**の**AddNew**メソッドを呼び出すと例外がスローされます。  
  
 **AllowEdit**が**true**の場合、 **DataRowView**を使用して**DataRow**の内容を変更できます。 **DataRowView**を使用して基になる行に対する変更を確認するか、 **DataRowView**を使用して変更を拒否することができます。 一度に編集できるのは 1 行だけです。 保留中の行が存在するときに**DataRowView**の**AddNew**メソッドまたは**BeginEdit**メソッドを呼び出すと、保留中の行に対して**EndEdit**が暗黙的に呼び出されます。 **EndEdit**が呼び出されると、指定された変更は基になる**DataRow**の**現在**の行バージョンに配置され、後でコミット**または**拒否することができます。そのため**には、** **DataTable**、 **DataSet**、または**DataRow**オブジェクト。 **AllowEdit**が**false**の場合、 **DataView**の値を変更しようとすると例外がスローされます。  
  
 既存の**DataRowView**が編集されている場合でも、基になる**DataTable**のイベントは、提案された変更で発生します。 基になる**DataRow**で**EndEdit**また**は CancelEdit**を呼び出すと、 **DataRowView**で**EndEdit**または**CancelEdit**が呼び出されているかどうかにかかわらず、保留中の変更が適用または取り消されます。  
  
 **Allowdelete**が**true**の場合、 **dataview**または**DataRowView**オブジェクトの**delete**メソッドを使用して**Dataview**から行を削除すると、基になる**DataTable**から行が削除されます。 後で、 **AcceptChanges**または**RejectChanges**を使用して、削除をコミットまたは拒否することができます。 **Allowdelete**が**false**の場合、 **DataView**または**DataRowView**の**Delete**メソッドを呼び出すと例外がスローされます。  
  
 次のコード例では、 **dataview**を使用して行を削除し、 **dataview**を使用して基になるテーブルに新しい行を追加します。  
  
```vb  
Dim custTable As DataTable = custDS.Tables("Customers")  
Dim custView As DataView = custTable.DefaultView  
custView.Sort = "CompanyName"  
  
custView.AllowDelete = False  
  
Dim newDRV As DataRowView = custView.AddNew()  
newDRV("CustomerID") = "ABCDE"  
newDRV("CompanyName") = "ABC Products"  
newDRV.EndEdit()  
```  
  
```csharp  
DataTable custTable = custDS.Tables["Customers"];  
DataView custView = custTable.DefaultView;  
custView.Sort = "CompanyName";  
  
custView.AllowDelete = false;  
  
DataRowView newDRV = custView.AddNew();  
newDRV["CustomerID"] = "ABCDE";  
newDRV["CompanyName"] = "ABC Products";  
newDRV.EndEdit();  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataTable>
- <xref:System.Data.DataView>
- <xref:System.Data.DataRowView>
- [DataViews](dataviews.md)
- [ADO.NET の概要](../ado-net-overview.md)
