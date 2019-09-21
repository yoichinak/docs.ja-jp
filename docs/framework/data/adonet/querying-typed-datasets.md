---
title: 型指定された DataSet のクエリ
ms.date: 08/15/2018
dev_langs:
- csharp
- vb
ms.assetid: ad712fa1-2baf-462a-b163-574cce6d376a
ms.openlocfilehash: 55714c4dae73cd17a849cc35681797dfa4266e3b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70782968"
---
# <a name="query-typed-datasets"></a>型指定されたデータセットのクエリ

アプリケーションのデザイン時に<xref:System.Data.DataSet>のスキーマがわかっている場合は、LINQ to DataSet を使用するとき<xref:System.Data.DataSet>に、型指定されたを使用することをお勧めします。 型指定<xref:System.Data.DataSet>されたは、 <xref:System.Data.DataSet>から派生するクラスです。 したがって、型指定されたデータセットは <xref:System.Data.DataSet> のすべてのメソッド、イベント、およびプロパティを継承します。 さらに、型<xref:System.Data.DataSet>指定されたは、厳密に型指定されたメソッド、イベント、およびプロパティを提供します。 つまり、コレクションベースのメソッドを使用せずに名前でテーブルおよび列にアクセスできます。 これによりクエリが簡素化され、読みやすくなります。 詳細については、「型指定された[データセット](./dataset-datatable-dataview/typed-datasets.md)」をご覧ください。

LINQ to DataSet は、型指定<xref:System.Data.DataSet>されたに対するクエリもサポートしています。 型指定<xref:System.Data.DataSet>されたを使用する場合、列データにアクセス<xref:System.Data.DataRowExtensions.SetField%2A>するためにジェネリック<xref:System.Data.DataRowExtensions.Field%2A>メソッドまたはメソッドを使用する必要はありません。 型情報はに<xref:System.Data.DataSet>含まれるため、コンパイル時にプロパティ名を使用できます。 LINQ to DataSet は、列の値へのアクセスを正しい型として提供するため、実行時ではなく、コードをコンパイルするときに型の不一致エラーがキャッチされます。

型指定<xref:System.Data.DataSet>されたのクエリを開始するには、Visual Studio の**データセットデザイナー**を使用してクラスを生成する必要があります。 詳細については、「[データセットの作成と構成](/visualstudio/data-tools/create-and-configure-datasets-in-visual-studio)」を参照してください。

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

- [DataSet のクエリ](querying-datasets-linq-to-dataset.md)
- [複数テーブルにまたがるクエリ](cross-table-queries-linq-to-dataset.md)
- [単一テーブルのクエリ](single-table-queries-linq-to-dataset.md)
