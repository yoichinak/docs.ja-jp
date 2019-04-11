---
title: '方法: データ サービス結果 (WCF Data Services) のページングを有効にします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 77dbeba89b352fa470ab0523a830db9175a1a21a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122903"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>方法: データ サービス結果 (WCF Data Services) のページングを有効にします。
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] データ サービス クエリによって返されるエンティティの数を制限できます。 ページ制限は、サービスの初期化時に呼び出されるメソッドで定義され、エンティティ セットごとに設定できます。  
  
 ページングが有効である場合、フィードの最終的なエントリには、データの次のページへのリンクが含まれます。 詳細については、次を参照してください。[データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)します。  
  
 このトピックでは、返された `Customers` エンティティ セットおよび `Orders` エンティティ セットのページングを有効にするためにデータ サービスを変更する方法について説明します。 このトピックの例では、Northwind サンプル データ サービスを使用します。 このサービスの作成を完了すると、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)します。  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>返された Customer エンティティ セットおよび Orders エンティティ セットのページングを有効化する方法  
  
-   データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>関連項目

- [遅延コンテンツの読み込み](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)
- [方法: ページングされた結果を読み込む](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md)
