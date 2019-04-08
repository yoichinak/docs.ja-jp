---
title: シーケンスの最初の要素の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: ccdc3777-b2c2-44e3-a627-abef8d79a555
ms.openlocfilehash: dca917b3c12b0f9923cc9ea34a2568c412a09831
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59081837"
---
# <a name="return-the-first-element-in-a-sequence"></a>シーケンスの最初の要素の取得
<xref:System.Linq.Enumerable.First%2A> 演算子を使用すると、シーケンスの内最初の要素を返すことができます。 <xref:System.Linq.Enumerable.First%2A> を使用するクエリは直ちに実行されます。  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] サポートしていません、<xref:System.Linq.Enumerable.Last%2A>演算子。  
  
## <a name="example"></a>例  
 次のコードは、テーブル内の最初の `Shipper` を見つけます。  
  
 Northwind サンプル データベースに対してこのクエリを実行すると、結果は次のようになります。  
  
 `ID = 1, Company = Speedy Express`.  
  
 [!code-csharp[DLinqQueryExamples#14](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#14)]
 [!code-vb[DLinqQueryExamples#14](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#14)]  
  
## <a name="example"></a>例  
 次のコードは、`Customer` が BONAP の単一の `CustomerID` を見つけます。  
  
 Northwind サンプル データベースに対してこのクエリを実行すると、結果は `ID = BONAP, Contact = Laurence Lebihan` になります。  
  
 [!code-csharp[DLinqQueryExamples#15](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#15)]
 [!code-vb[DLinqQueryExamples#15](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#15)]  
  
## <a name="see-also"></a>関連項目

- [クエリの例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [サンプル データベースのダウンロード](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
