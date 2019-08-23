---
title: メソッド ベースのクエリ構文例:フィルター
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e40e314c-eb30-4f44-a054-41e511e35832
ms.openlocfilehash: 0795784f4090fca02c89cdfb396d217620b1ba68
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948236"
---
# <a name="method-based-query-syntax-examples-filtering"></a>メソッド ベースのクエリ構文例:フィルター
このトピックの例では、メソッドベースの`Where`クエリ`Where…Contains`構文を使用して、メソッドとメソッドを使用して、 [AdventureWorks Sales Model](https://archive.codeplex.com/?p=msftdbprodsamples)に対してクエリを実行する方法を示します。 注意:`Contains` は、[コンパイル済みクエリ](../../../../../../docs/framework/data/adonet/ef/language-reference/compiled-queries-linq-to-entities.md)の一部として使用できません。  
  
 これらの例で使用されている、AdventureWorks Sales Model は、AdventureWorks サンプル データベースの Contact、Address、Product、SalesOrderHeader、SalesOrderDetail の各テーブルから作成されています。  
  
 このトピックの例では、次`using` / `Imports`のステートメントを使用します。  
  
 [!code-csharp[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#importsusing)]
 [!code-vb[DP L2E Examples#ImportsUsing](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#importsusing)]  
  
## <a name="where"></a>場所  
  
### <a name="example"></a>例  
 次の例では、すべてのオンライン注文が返されます。  
  
 [!code-csharp[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where1_mq)]
 [!code-vb[DP L2E Examples#Where1_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where1_mq)]  
  
### <a name="example"></a>例  
 次の例では、注文数量が 3 個以上で 5 個以下の注文が返されます。  
  
 [!code-csharp[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where2_mq)]
 [!code-vb[DP L2E Examples#Where2_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where2_mq)]  
  
### <a name="example"></a>例  
 次の例では、色が赤の製品がすべて返されます。  
  
 [!code-csharp[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#where3_mq)]
 [!code-vb[DP L2E Examples#Where3_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#where3_mq)]  
  
### <a name="example"></a>例  
 次の例では、`Where` メソッドを使用して、2003 年 12 月 1 日以降に受けた注文を検索します。次に、`order.SalesOrderDetail` ナビゲーション プロパティを使用して、各注文の詳細を取得します。  
  
 [!code-csharp[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DP L2E Examples/CS/Program.cs#wherenavproperty_mq)]
 [!code-vb[DP L2E Examples#WhereNavProperty_MQ](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DP L2E Examples/VB/Module1.vb#wherenavproperty_mq)]  
  
## <a name="wherecontains"></a>Where…Contains  
  
### <a name="example"></a>例  
 次の例では、配列を `Where…Contains` 句の一部として使用し、その配列内の値と一致する `ProductModelID` を持つすべての製品を検出します。  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#3)]
 [!code-vb[DP L2E ArraysAndListsInQueries#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#3)]  
  
> [!NOTE]
> `Where…Contains` 句の述語として、<xref:System.Array>、<xref:System.Collections.Generic.List%601>、または <xref:System.Collections.Generic.IEnumerable%601> インターフェイスを実装する任意の型のコレクションを使用できます。 さらに、LINQ to Entities クエリ内でコレクションを宣言および初期化できます。 詳細については、次の例を参照してください。  
  
### <a name="example"></a>例  
 次の例では、`Where…Contains` 句で配列を宣言および初期化し、その配列内の値と一致する `ProductModelID` または `Size` を持つすべての製品を検出します。  
  
 [!code-csharp[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp l2e arraysandlistsinqueries/cs/program.cs#4)]
 [!code-vb[DP L2E ArraysAndListsInQueries#4](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp l2e arraysandlistsinqueries/vb/module1.vb#4)]  
  
## <a name="see-also"></a>関連項目

- [LINQ to Entities でのクエリ](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)
