---
title: DataRow の削除
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 46109ee1781b8b509df87b4203c51a55b9f596ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205108"
---
# <a name="datarow-deletion"></a>DataRow の削除
<xref:System.Data.DataRow>オブジェクト<xref:System.Data.DataRowCollection> <xref:System.Data.DataRow.Delete%2A>からオブジェクトを削除するには、オブジェクトの Remove メソッドと DataRow オブジェクトのメソッドの2つのメソッドを使用できます。 <xref:System.Data.DataTable> メソッドは**DataRowCollection**から DataRow を削除しますが、 <xref:System.Data.DataRow.Delete%2A>メソッドは行を削除対象としてマークするだけです。 <xref:System.Data.DataRowCollection.Remove%2A> 実際の削除は、アプリケーションが**AcceptChanges**メソッドを呼び出したときに発生します。 <xref:System.Data.DataRow.Delete%2A> を使用すると、行を実際に削除する前に、削除対象としてどの行がマークされているかをプログラムによってチェックできます。 削除対象としてマークされている行の <xref:System.Data.DataRow.RowState%2A> プロパティは、<xref:System.Data.DataRow.Delete%2A> に設定されています。  
  
 <xref:System.Data.DataRow.Delete%2A> オブジェクトを反復処理している間は、foreach ループで <xref:System.Data.DataRowCollection.Remove%2A> も <xref:System.Data.DataRowCollection> も呼び出すことはできません。 <xref:System.Data.DataRow.Delete%2A> または <xref:System.Data.DataRowCollection.Remove%2A> はコレクションの状態を変更します。  
  
 DataAdapter およびリレーショナル<xref:System.Data.DataSet>データソースと共にまたは**DataTable**を使用する場合は、 **DataRow**の**Delete**メソッドを使用して行を削除します。 **Delete**メソッドは、行を**DataSet**または**DataTable**で**削除済み**としてマークしますが、削除はしません。 代わりに、 **DataAdapter**が**削除済み**としてマークされた行を検出すると、 **DeleteCommand**メソッドを実行してデータソースの行を削除します。 この行は、 **AcceptChanges**メソッドを使用して完全に削除できます。 **Remove**を使用して行を削除すると、その行はテーブルから完全に削除されますが、 **DataAdapter**はデータソースの行を削除しません。  
  
 **DataRowCollection**の**Remove**メソッドは、次の例に示すように、 **DataRow**を引数として受け取り、コレクションから削除します。  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 これに対して、次の例では、 **DataRow**の**Delete**メソッドを呼び出して、その**RowState**を**Deleted**に変更する方法を示しています。  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 行が削除対象としてマークされていて、 **datatable**オブジェクトの**AcceptChanges**メソッドを呼び出すと、その行が**datatable**から削除されます。 これに対し、 **RejectChanges**を呼び出すと、行の**RowState**は、**削除済み**としてマークされる前の行に戻ります。  
  
> [!NOTE]
> **DataRow**の**RowState**が**追加**された場合、これはテーブルに追加されたばかりであることを意味し、**削除済み**としてマークされ、テーブルから削除されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [DataTable 内のデータの操作](manipulating-data-in-a-datatable.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
