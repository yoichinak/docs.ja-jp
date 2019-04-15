---
title: '方法: サービス操作 (WCF Data Services) の定義します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: fc738f7e81c02e44075ce5ed151ed42452650c94
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59518124"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a>方法: サービス操作 (WCF Data Services) の定義します。
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] は、サーバー上でサービス操作として定義されたメソッドを公開します。 サービス操作では、サーバーで定義されているメソッドに URI を介してアクセスを提供するデータ サービスを使用します。 サービス操作を定義するには、適用、[`WebGet]`または`[WebInvoke]`属性をメソッド。 クエリ演算子をサポートするために、サービス操作を返す必要があります、<xref:System.Linq.IQueryable%601>インスタンス。 サービス操作は、<xref:System.Data.Services.DataService%601.CurrentDataSource%2A> の <xref:System.Data.Services.DataService%601> プロパティを介して、基になるデータ ソースにアクセスできます。 詳細については、次を参照してください。[サービス操作](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md)します。  
  
 このトピックの例では、`GetOrdersByCity` という名前のサービス操作を定義します。このサービス操作は、<xref:System.Linq.IQueryable%601> オブジェクトおよび関連する `Orders` オブジェクトのフィルターされた `Order_Details` インスタンスを返します。 この例は、Northwind サンプル データ サービスのデータ ソースである <xref:System.Data.Objects.ObjectContext> インスタンスにアクセスします。 このサービスの作成を完了すると、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)します。  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a>Northwind データ サービスのサービス操作を定義するには  
  
1. Northwind データ サービス プロジェクトで Northwind.svc ファイルを開きます。  
  
2. `Northwind` クラスで、次に示すように `GetOrdersByCity` というサービス操作メソッドを定義します。  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3. `InitializeService` クラスの `Northwind` メソッドで次のコードを追加して、サービス操作へのアクセスを有効にします。  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a>GetOrdersByCity サービス操作をクエリするには  
  
-   Web ブラウザーで次のいずれかの URI を入力して、次の例で定義されているサービス操作を呼び出します。  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a>例  
 次の例は、`GetOrderByCity` という名前のサービス操作を Northwind データ サービスに実装します。 この操作は、ADO.NET Entity Framework を使用して、`Orders` オブジェクトのセットおよび関連する `Order_Details` オブジェクトを、指定した都市名に基づく <xref:System.Linq.IQueryable%601> インスタンスとして返します。  
  
> [!NOTE]
>  メソッドは <xref:System.Linq.IQueryable%601> インスタンスを返すので、クエリ操作は、このサービス操作エンドポイントでサポートされています。  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a>関連項目

- [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
