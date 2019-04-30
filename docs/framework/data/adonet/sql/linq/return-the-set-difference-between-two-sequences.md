---
title: 2 つのシーケンスの差集合の取得
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 62efb546-c898-408f-af21-36e7c6fed217
ms.openlocfilehash: 7edc60c7ab8510aadd9ac273529a88adeb41352a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62037532"
---
# <a name="return-the-set-difference-between-two-sequences"></a>2 つのシーケンスの差集合の取得
2 つのシーケンスの差集合を返すには、<xref:System.Linq.Queryable.Except%2A> 演算子を使用します。  
  
## <a name="example"></a>例  
 この例では、<xref:System.Linq.Queryable.Except%2A> を使用して、`Customers` は居住しているが `Employees` は居住していないすべての国のシーケンスを返します。  
  
 [!code-csharp[DLinqQueryExamples#41](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#41)]
 [!code-vb[DLinqQueryExamples#41](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#41)]  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] では、<xref:System.Linq.Queryable.Except%2A> 演算は集合でのみ適切に定義されます。 マルチセットのセマンティクスは未定義です。  
  
## <a name="see-also"></a>関連項目

- [クエリの例](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [標準クエリ演算子の変換](../../../../../../docs/framework/data/adonet/sql/linq/standard-query-operator-translation.md)
