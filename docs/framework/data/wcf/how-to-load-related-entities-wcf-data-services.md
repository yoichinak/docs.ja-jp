---
title: '方法: 関連エンティティ (WCF Data Services) を読み込む'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 6f143d30-d997-4e6b-bcf0-d5c394ecb108
ms.openlocfilehash: 7687378ae2a6c7d8021acc53b19544206ee0cc84
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092631"
---
# <a name="how-to-load-related-entities-wcf-data-services"></a>方法: 関連エンティティ (WCF Data Services) を読み込む
関連付けられたエンティティを [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で読み込む必要がある場合、<xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> クラスで <xref:System.Data.Services.Client.DataServiceContext> メソッドを使用できます。 使用することも、<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>メソッドを<xref:System.Data.Services.Client.DataServiceQuery%601>に関連するエンティティを同じクエリの応答で頻繁に読み込むことが必要です。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアント データ クラスを作成を完了すると、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)します。  
  
## <a name="example"></a>例  
 次の例は、返される各 `Customer` インスタンスに関連付けられた `Orders` を明示的に読み込む方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadrelatedordercustomer)]
 [!code-vb[Astoria Northwind Client#LoadRelatedOrderCustomer](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadrelatedordercustomer)]  
  
## <a name="example"></a>例  
 次の例は、<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> メソッドを使用して、クエリによって返される `Order Details` に属する `Orders` を返す方法を示します。  
  
 [!code-csharp[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#expandorderdetails)]
 [!code-vb[Astoria Northwind Client#ExpandOrderDetails](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#expandorderdetails)]  
  
## <a name="see-also"></a>関連項目

- [データ サービスに対するクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
