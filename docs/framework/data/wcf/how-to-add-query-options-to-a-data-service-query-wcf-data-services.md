---
title: '方法: データサービスクエリにクエリオプションを追加する (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
ms.openlocfilehash: f7b0557938d1419b79c3191cf8f9110cab2f5ce6
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790787"
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>方法: データサービスクエリにクエリオプションを追加する (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、生成されたクライアント データ サービス クラスを使用して .NET Framework ベースのクライアント アプリケーションからデータ サービスをクエリできます。 このために最も簡単な方法は、必要なクエリ オプションを含む言語統合クエリ (LINQ) 式を作成することです。 また、一連の LINQ クエリ メソッドを呼び出しても同等のクエリを作成できます。 最後に <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> メソッドを使用して、クエリにクエリ オプションを追加できます。 これらの場合のそれぞれにおいて、クライアントによって生成される URI には、要求されたエンティティ セットに選択したクエリ オプションを適用したものが含まれます。 詳細については、「[データサービスのクエリ](querying-the-data-service-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアントデータクラスは、 [WCF Data Services のクイックスタート](quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
## <a name="example"></a>例  
 次の例では、運賃が $30 以上の注文だけを返し、結果を出荷日で降順に並べ替える LINQ クエリ式の作成方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinq)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinq)]  
  
## <a name="example"></a>例  
 次の例では、前のクエリと同等の LINQ クエリ メソッドを使用して LINQ クエリを作成する方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpression)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpression)]  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> メソッドを使用して、前の例と同等の <xref:System.Data.Services.Client.DataServiceQuery%601> を作成する方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>例  
 次の例は、`$orderby` クエリ オプションを使用して、返された Orders オブジェクトをフィルターして Freight プロパティで並べ替える方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>関連項目

- [データ サービスに対するクエリ](querying-the-data-service-wcf-data-services.md)
- [方法: プロジェクトクエリの結果](how-to-project-query-results-wcf-data-services.md)
