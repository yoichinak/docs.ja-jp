---
title: '方法: データ サービス メッセージ (WCF Data Services) をインターセプトします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: ad0673f72b1a81d6bcfaf0704ccd698eda7bb20c
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517835"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a>方法: データ サービス メッセージ (WCF Data Services) をインターセプトします。
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、要求メッセージを先に取得して、操作にカスタム ロジックを追加することができます。 メッセージをインターセプトするには、データ サービスで特別なメソッドを使用します。 詳細については、次を参照してください。[インターセプター](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)します。  
  
 このトピックの例では、Northwind サンプル データ サービスを使用します。 このサービスの作成を完了すると、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)します。  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a>Orders エンティティ セットのクエリ インターセプターを定義するには  
  
1. Northwind データ サービス プロジェクトで Northwind.svc ファイルを開きます。  
  
2. `Northwind` クラスのコード ページで次の `using` ステートメント (Visual Basic の場合は `Imports`) を追加します。  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3. `Northwind` クラスで、次に示すように `OnQueryOrders` というサービス操作メソッドを定義します。  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a>Products エンティティ セットの変更インターセプターを定義するには  
  
1. Northwind データ サービス プロジェクトで Northwind.svc ファイルを開きます。  
  
2. `Northwind` クラスで、次に示すように `OnChangeProducts` というサービス操作メソッドを定義します。  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a>例  
 この例では、ラムダ式を返す `Orders` エンティティ セットのクエリ インターセプター メソッドを定義します。 この式には、要求された `Orders` を特定の連絡先名が付けられた関連 `Customers` に基づいてフィルターするデリゲートが含まれます。 この名前は、要求ユーザーに基づいて決定されます。 この例では、認証が有効化され、WCF を使用する ASP.NET Web アプリケーション内でデータ サービスがホストされていることを前提とします。 <xref:System.Web.HttpContext> クラスは、現在の要求の原則を取得するために使用されます。  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a>例  
 この例は、`Products` エンティティ セットの変更インターセプター メソッドを定義します。 このメソッドは、<xref:System.Data.Services.UpdateOperations.Add> 操作または <xref:System.Data.Services.UpdateOperations.Change> 操作に関するサービスへの入力を検証し、生産が中止されている製品への変更が行われた場合に例外を発生させます。 また、サポートされない操作として製品の削除をブロックします。  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a>関連項目

- [方法: サービス操作を定義します。](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)
- [WCF Data Services の定義](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
