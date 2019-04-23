---
title: DataRow の削除
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c34f531d-4b9b-4071-b2d7-342c402aa586
ms.openlocfilehash: 57f51ada00bf24617ca3e295a010aae64f0aa849
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196139"
---
# <a name="datarow-deletion"></a>DataRow の削除
2 つのメソッドを使用して削除できます、<xref:System.Data.DataRow>オブジェクトから、<xref:System.Data.DataTable>オブジェクト:**削除**のメソッド、<xref:System.Data.DataRowCollection>オブジェクト、および<xref:System.Data.DataRow.Delete%2A>のメソッド、 **DataRow**オブジェクト。 一方、<xref:System.Data.DataRowCollection.Remove%2A>メソッドの削除、 **DataRow**から、 **DataRowCollection**、<xref:System.Data.DataRow.Delete%2A>メソッドは、行の削除をマークするだけです。 実際の削除は、アプリケーションを呼び出すときに発生します。、 **AcceptChanges**メソッド。 <xref:System.Data.DataRow.Delete%2A> を使用すると、行を実際に削除する前に、削除対象としてどの行がマークされているかをプログラムによってチェックできます。 削除対象としてマークされている行の <xref:System.Data.DataRow.RowState%2A> プロパティは、<xref:System.Data.DataRow.Delete%2A> に設定されています。  
  
 <xref:System.Data.DataRow.Delete%2A> オブジェクトを反復処理している間は、foreach ループで <xref:System.Data.DataRowCollection.Remove%2A> も <xref:System.Data.DataRowCollection> も呼び出すことはできません。 <xref:System.Data.DataRow.Delete%2A> または <xref:System.Data.DataRowCollection.Remove%2A> はコレクションの状態を変更します。  
  
 使用する場合、<xref:System.Data.DataSet>または**DataTable**と組み合わせて、 **DataAdapter**とリレーショナル データ ソース、使用、**削除**のメソッド、 **DataRow**行を削除します。 **削除**メソッドとしての行をマークする**Deleted**で、**データセット**または**DataTable**は削除されません。 代わりに、 **DataAdapter**としてマークされている行を検出する**Deleted**が実行されます、 **DeleteCommand**メソッドは、データ ソースで行を削除します。 行のできますし、完全に削除するを使用して、 **AcceptChanges**メソッド。 使用する場合**削除**行を削除する、行は、テーブルから完全に削除されますが、 **DataAdapter**データ ソースの行は削除されません。  
  
 **削除**のメソッド、 **DataRowCollection**は、 **DataRow**を引数としてし、次の例に示すように、コレクションから削除します。  
  
```vb  
workTable.Rows.Remove(workRow)  
```  
  
```csharp  
workTable.Rows.Remove(workRow);  
```  
  
 これに対し、次の例に示しますを呼び出す方法、**削除**メソッドを**DataRow**を変更するその**RowState**に**Deleted**.  
  
```vb  
workRow.Delete  
```  
  
```csharp  
workRow.Delete();  
```  
  
 行は削除対象としてマークしを呼び出す場合、 **AcceptChanges**のメソッド、 **DataTable**オブジェクトから行を削除、 **DataTable**します。 呼び出す場合とは異なり、 **RejectChanges**、 **RowState**行としてマークされる前に戻ります**Deleted**します。  
  
> [!NOTE]
>  場合、 **RowState**の**DataRow**は**Added**つまりが追加された直後に、テーブルとしてマークされているし、 **Deleted**はテーブルから削除します。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataRow>
- <xref:System.Data.DataRowCollection>
- <xref:System.Data.DataTable>
- [DataTable 内のデータの操作](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/manipulating-data-in-a-datatable.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
