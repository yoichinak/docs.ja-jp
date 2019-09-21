---
title: '方法: データサービスの結果のページングを有効にする (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- paging output [WCF Data Services]
ms.assetid: 9a316cbd-9612-4482-a541-a10bc78b2635
ms.openlocfilehash: 82b4d0fd3531778ab494d6526a56b092edf9481a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780053"
---
# <a name="how-to-enable-paging-of-data-service-results-wcf-data-services"></a>方法: データサービスの結果のページングを有効にする (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、データ サービス クエリによって返されるエンティティの数を制限できます。 ページ制限は、サービスの初期化時に呼び出されるメソッドで定義され、エンティティ セットごとに設定できます。  
  
 ページングが有効である場合、フィードの最終的なエントリには、データの次のページへのリンクが含まれます。 詳細については、「[データサービスの構成](configuring-the-data-service-wcf-data-services.md)」を参照してください。  
  
 このトピックでは、返された `Customers` エンティティ セットおよび `Orders` エンティティ セットのページングを有効にするためにデータ サービスを変更する方法について説明します。 このトピックの例では、Northwind サンプル データ サービスを使用します。 このサービスは、 [WCF Data Services のクイックスタート](quickstart-wcf-data-services.md)を完了したときに作成されます。  
  
### <a name="how-to-enable-paging-of-returned-customers-and-orders-entity-sets"></a>返された Customer エンティティ セットおよび Orders エンティティ セットのページングを有効化する方法  
  
- データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。  
  
     [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
     [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
## <a name="see-also"></a>関連項目

- [遅延コンテンツの読み込み](loading-deferred-content-wcf-data-services.md)
- [方法: ページング結果の読み込み](how-to-load-paged-results-wcf-data-services.md)
