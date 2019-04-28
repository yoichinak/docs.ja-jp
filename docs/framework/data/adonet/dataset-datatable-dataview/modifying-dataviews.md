---
title: DataView の変更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 697a3991-b660-4a5a-8a54-1a2304ff158e
ms.openlocfilehash: 6e340b9b72735598650d2eefa6e19ab40fffc2e4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607415"
---
# <a name="modifying-dataviews"></a>DataView の変更
<xref:System.Data.DataView> を使用して、データ行を基になるテーブルに追加、削除、または変更できます。 使用する機能、 **DataView**基になるテーブル内のデータを変更するのには 3 つのブール型プロパティのいずれかの設定によって制御されます、 **DataView**します。 この 3 つのプロパティとは、<xref:System.Data.DataView.AllowNew%2A>、<xref:System.Data.DataView.AllowEdit%2A> および <xref:System.Data.DataView.AllowDelete%2A> です。 設定されている**true**既定。  
  
 場合**AllowNew**は**true**、使用することができます、<xref:System.Data.DataView.AddNew%2A>のメソッド、 **DataView**新たに作成する<xref:System.Data.DataRowView>します。 新しい行がないので注意が実際には、基になる追加<xref:System.Data.DataTable>まで、<xref:System.Data.DataRowView.EndEdit%2A>のメソッド、 **DataRowView**が呼び出されます。 場合、<xref:System.Data.DataRowView.CancelEdit%2A>のメソッド、 **DataRowView**が呼び出されると、新しい行が破棄されます。 1 つだけを編集できることにも注意してください**DataRowView**一度にします。 呼び出す場合、 **AddNew**または**BeginEdit**のメソッド、 **DataRowView**保留中の行が存在する場合、 **EndEdit**で暗黙的に呼び出されますが、保留中の行。 ときに**EndEdit**が呼び出されると、変更は、基になるに適用されます**DataTable**し、後でコミットまたは拒否を使用して、 **AcceptChanges**または**RejectChanges**のメソッド、 **DataTable**、**データセット**、または**DataRow**オブジェクト。 場合**AllowNew**は**false**、呼び出した場合、例外がスローされます、 **AddNew**のメソッド、 **DataRowView**します。  
  
 場合**AllowEdit**は**true**の内容を変更することができます、 **DataRow**を使用して、 **DataRowView**します。 使用して基になる行への変更を確認する**DataRowView.EndEdit**を使用して変更を拒否または**DataRowView.CancelEdit**します。 一度に編集できるのは 1 行だけです。 呼び出す場合、 **AddNew**または**BeginEdit**のメソッド、 **DataRowView**保留中の行が存在する場合、 **EndEdit**で暗黙的に呼び出されます保留中の行。 ときに**EndEdit**を呼び出すに提案された変更が配置されます、**現在**行バージョンの基になる**DataRow**し、後では、コミットされたか、を使用して拒否されました。**AcceptChanges**または**RejectChanges**のメソッド、 **DataTable**、**データセット**、または**DataRow**オブジェクト。 場合**AllowEdit**は**false**、値を変更しようとした場合に例外がスローされます、 **DataView**します。  
  
 既存**DataRowView**編集されている、基になるイベント**DataTable**に変更の提案も生成されます。 呼び出す場合**EndEdit**または**CancelEdit**基になる**DataRow**、保留中の変更を適用またはかどうかに関係なくキャンセルは**EndEdit**または**CancelEdit**で呼び出される、 **DataRowView**します。  
  
 場合**AllowDelete**は**true**から行を削除することができます、 **DataView**を使用して、**削除**のメソッド、 **DataView**または**DataRowView**オブジェクト、および行が削除されている場合、基になるから**DataTable**します。 後でコミットまたはを使用して削除を拒否する**AcceptChanges**または**RejectChanges**それぞれします。 場合**AllowDelete**は**false**、呼び出した場合、例外がスローされます、**削除**のメソッド、 **DataView**または**DataRowView**します。  
  
 次のコード例を使用して無効になります、 **DataView**に削除の行やを使用して基になるテーブルに新しい行を追加、 **DataView**します。  
  
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
- [DataViews](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/dataviews.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
