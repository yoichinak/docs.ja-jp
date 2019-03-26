---
title: 型指定された DataSet のクエリ
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: d956fd5f07c108146d20623bcf811266380c132c
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2018
ms.locfileid: "45963745"
---
# <a name="query-typed-datasets"></a>型指定されたデータセットのクエリ

場合のスキーマ、 <xref:System.Data.DataSet> 、型指定されたを使用することをお勧めします。 アプリケーションのデザイン時に認識が<xref:System.Data.DataSet>LINQ to DataSet を使用する場合。 型指定された<xref:System.Data.DataSet>から派生したクラスには、<xref:System.Data.DataSet>します。 したがって、型指定されたデータセットは <xref:System.Data.DataSet> のすべてのメソッド、イベント、およびプロパティを継承します。 さらに、型指定された<xref:System.Data.DataSet>厳密に型指定されたメソッド、イベント、およびプロパティを提供します。 つまり、コレクションベースのメソッドを使用せずに名前でテーブルおよび列にアクセスできます。 これによりクエリが簡素化され、読みやすくなります。 詳細については、[型指定されたデータセット](../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)を参照してください。

LINQ to DataSet がに対する型指定されたクエリの実行をサポートしても<xref:System.Data.DataSet>します。 型指定された<xref:System.Data.DataSet>、ジェネリックを使用する必要はありません<xref:System.Data.DataRowExtensions.Field%2A>メソッドまたは<xref:System.Data.DataRowExtensions.SetField%2A>列データにアクセスするメソッド。 型情報が含まれているために、プロパティ名はコンパイル時に使用可能な<xref:System.Data.DataSet>します。 LINQ to DataSet では、実行時の代わりに、コードがコンパイルされるときに、型の不一致エラーがキャッチされるように、適切な型として列の値へのアクセスを提供します。

型指定されたクエリを開始する前に<xref:System.Data.DataSet>を使用して、クラスを生成する必要があります、**データセット デザイナー** Visual Studio でします。 詳細については、[作成し、データセットを構成](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)を参照してください。

## <a name="example"></a>例

次の例では、型指定された <xref:System.Data.DataSet> に対してクエリを実行しています。

```csharp
var query = from o in orders
            where o.OnlineOrderFlag == true
            select new { o.SalesOrderID,
                         o.OrderDate,
                         o.SalesOrderNumber };

foreach(var order in query)
{
    Console.WriteLine("{0}\t{1:d}\t{2}",
      order.SalesOrderID,
      order.OrderDate,
      order.SalesOrderNumber);
}
```

```vb
Dim orders = ds.Tables("SalesOrderHeader")

Dim query = _
       From o In orders _
       Where o.OnlineOrderFlag = True _
       Select New {SalesOrderID := o.SalesOrderID, _
                   OrderDate := o.OrderDate, _
                   SalesOrderNumber := o.SalesOrderNumber}

For Each Dim onlineOrder In query
 Console.WriteLine("{0}\t{1:d}\t{2}", _
 onlineOrder.SalesOrderID, _
 onlineOrder.OrderDate, _
 onlineOrder.SalesOrderNumber)
Next
```

## <a name="see-also"></a>関連項目

- [DataSet のクエリ](../../../../docs/framework/data/adonet/querying-datasets-linq-to-dataset.md)
- [複数テーブルにまたがるクエリ](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)
- [単一テーブルのクエリ](../../../../docs/framework/data/adonet/single-table-queries-linq-to-dataset.md)
