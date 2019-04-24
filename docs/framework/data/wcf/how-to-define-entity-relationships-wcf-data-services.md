---
title: '方法: エンティティのリレーションシップ (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: cc255524-1534-4fae-b83c-250933d5a72b
ms.openlocfilehash: 3bd2293f02e77ab2db5c3ba245596021e08b04c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517829"
---
# <a name="how-to-define-entity-relationships-wcf-data-services"></a>方法: エンティティのリレーションシップ (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で新しいエンティティを追加するとき、新しいエンティティと関連エンティティの間のリレーションシップは自動的には定義されません。 エンティティ インスタンス間のリレーションシップを作成および変更し、クライアント ライブラリを使用して、これらの変更をデータ サービスに反映できます。 詳細については、次を参照してください。[データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)します。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアント データ クラスを作成を完了すると、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)します。  
  
## <a name="example"></a>例  
 次の例では、新しいオブジェクト インスタンスを作成し、<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> で <xref:System.Data.Services.Client.DataServiceContext> メソッドを呼び出して、関連する注文へのリンクと共に、コンテキスト内に項目を作成します。 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> メソッドが呼び出されたときに HTTP POST メッセージがデータ サービスに送信されます。  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderauto)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderAuto](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderauto)]  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> メソッドを使用して、特定の `Order_Details` オブジェクトへの参照と共に、`Orders` オブジェクトを関連する `Products` オブジェクトに追加する方法を示します。 <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> メソッドおよび <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> メソッドは、リレーションシップを定義します。 この例では、`Order_Details` オブジェクトのナビゲーション プロパティも明示的に設定されます。  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorder)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrder](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorder)]  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services クライアント ライブラリ](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [方法: 追加、変更、およびエンティティの削除](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md)
