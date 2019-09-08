---
title: '方法: ページング結果の読み込み (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
ms.openlocfilehash: e718aad904a43d118a243afafc17834cba31f028
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790447"
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>方法: ページング結果の読み込み (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、1 つの応答フィードで返されるエンティティの数をデータ サービスで制限できます。 この処理を行うと、フィードの最終的なエントリには、データの次のページへのリンクが含まれます。 データの次のページへの URI は、<xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> が実行されたときに返される <xref:System.Data.Services.Client.QueryOperationResponse%601> の <xref:System.Data.Services.Client.DataServiceQuery%601> メソッドを呼び出すことによって取得されます。 このオブジェクトによって表される URI は、結果の次のページを読み込むために使用されます。 詳細については、「[遅延コンテンツの読み込み](loading-deferred-content-wcf-data-services.md)」を参照してください。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアントデータクラスは、 [WCF Data Services のクイックスタート](quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
## <a name="example"></a>例  
 次の例は、`do…while` ループを使用して、データ サービスからのページングされた結果の `Customers` エンティティを読み込みます。  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>例  
 次の例は、関連する `Orders` エンティティと各 `Customers` エンティティを返し、`do…while` ループを使用して `Customers` エンティティ ページおよび入れ子になった `while` ループを読み込んで、データ サービスから関連する `Orders` エンティティのページを読み込みます。  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>関連項目

- [遅延コンテンツの読み込み](loading-deferred-content-wcf-data-services.md)
- [方法: 関連エンティティの読み込み](how-to-load-related-entities-wcf-data-services.md)
