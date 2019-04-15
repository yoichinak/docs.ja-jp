---
title: DataRelation の移動
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e5e673f4-9b44-45ae-aaea-c504d1cc5d3e
ms.openlocfilehash: f4dfccad23bf5d15f5cbd0a33e76a136417e13ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204160"
---
# <a name="navigating-datarelations"></a>DataRelation の移動
<xref:System.Data.DataRelation> の主な機能の 1 つは、<xref:System.Data.DataTable> の 1 つの <xref:System.Data.DataSet> から別の  を移動できることです。 すべてを取得することができます、関連する<xref:System.Data.DataRow>にあるオブジェクトの**DataTable**指定されると、1 つ**DataRow**関連から**DataTable**。 確立した後など、 **DataRelation**を使用して特定の顧客行のすべての注文行を取得する顧客のテーブルと orders のテーブルでは、間**GetChildRows**。  
  
 次のコード例を作成、 **DataRelation**間、**顧客**テーブルおよび**注文**のテーブルを**データセット**を返します各顧客のすべての注文します。  
  
 [!code-csharp[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableRelation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableRelation/VB/source.vb#1)]  
  
 上記の例に基づいて、4 つのテーブルを相互に関連付け、そのテーブルのリレーションシップ間を移動する例を次に示します。 前の例のように**CustomerID**関連、**顧客**テーブル、**注文**テーブル。 顧客ごとに、**顧客**テーブル内のすべての子行、**注文**特定の顧客が注文の数を返すために、テーブルが決定され、その**OrderID**値。  
  
 展開された例もから値を返します、 **OrderDetails**と**製品**テーブル。 **注文**テーブルに関連する、 **OrderDetails**テーブルを使用して**OrderID**を決める際に、各顧客の注文、どのような製品と数量を注文しました。 **OrderDetails**テーブルにはのみが含まれています、 **ProductID**注文の製品の**OrderDetails**に関連する**製品**使用して**ProductID**を返すために、 **ProductName**します。 このリレーションで、**製品**テーブルが親と**Order Details**テーブルが子。 その結果、反復処理時、 **OrderDetails**テーブル**GetParentRow**取得、関連するために呼び出される**ProductName**値。  
  
 された場合、 **DataRelation**用に作成、**顧客**と**注文**テーブル、値が指定されていない、 **createConstraints**フラグ (既定値は**true**)。 これですべての行、**注文**テーブルが、 **CustomerID** 、親が存在する値**顧客**テーブル。 場合、 **CustomerID**内に存在する、**注文**テーブルに存在しない、**顧客**、テーブル、<xref:System.Data.ForeignKeyConstraint>例外がスローされます。  
  
 子の列には、親列を含まない値が含まれます、設定、 **createConstraints**フラグを**false**を追加するとき、 **DataRelation**します。 例では、 **createConstraints**にフラグが設定されている**false**の**DataRelation**間、**注文**テーブルと、 **OrderDetails**テーブル。 これにより、アプリケーションからのすべてのレコードを返す、 **OrderDetails**テーブルとレコードのサブセットのみ、**注文**せず、実行時に例外を生成するテーブル。 展開された例では、次の形式で出力が生成されます。  
  
```  
Customer ID: NORTS  
  Order ID: 10517  
        Order Date: 4/24/1997 12:00:00 AM  
           Product: Filo Mix  
          Quantity: 6  
           Product: Raclette Courdavault  
          Quantity: 4  
           Product: Outback Lager  
          Quantity: 6  
  Order ID: 11057  
        Order Date: 4/29/1998 12:00:00 AM  
           Product: Outback Lager  
          Quantity: 3  
```  
  
 次のコード例は、展開された例場所からの値、 **OrderDetails**と**製品**内のレコードのサブセットのみをテーブルが返されます、**注文**返されるテーブル。  
  
 [!code-csharp[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/CS/source.cs#1)]
 [!code-vb[DataWorks Data.DataTableNavigation#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks Data.DataTableNavigation/VB/source.vb#1)]  
  
## <a name="see-also"></a>関連項目

- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
