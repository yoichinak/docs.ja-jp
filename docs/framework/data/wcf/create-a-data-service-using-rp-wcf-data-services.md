---
title: '方法: リフレクション プロバイダー (WCF Data Services) を使用してデータ サービスを作成します。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 233b17de17b7f50547b2f4fbf6a543d7258183cf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517097"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>方法: リフレクション プロバイダー (WCF Data Services) を使用してデータ サービスを作成します。
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、<xref:System.Linq.IQueryable%601> インターフェイスを実装するオブジェクトとして公開されているクラスに基づいてデータ モデルを定義できます。 詳細については、次を参照してください。[データ サービス プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)します。  
  
## <a name="example"></a>例  
 次の例は、`Orders` および `Items` を含むデータ モデルを定義します。 エンティティ コンテナー クラス `OrderItemData` には、<xref:System.Linq.IQueryable%601> インターフェイスを返す 2 つのパブリック メソッドがあります。 これらのインターフェイスは、`Orders` エンティティ型と `Items` エンティティ型のエンティティ セットです。 `Order` には複数の `Items` を含めることができるので、`Orders` エンティティ型には `Items` オブジェクトのコレクションを返す `Items` ナビゲーション プロパティがあります。 `OrderItemData` エンティティ コンテナー クラスは、<xref:System.Data.Services.DataService%601> データ サービスが派生する `OrderItems` クラスのジェネリック型です。  
  
> [!NOTE]
>  この例はメモリ内のデータ プロバイダーを示し、変更は現在のオブジェクト インスタンスの外部で永続化されないので、<xref:System.Data.Services.IUpdatable> インターフェイスを実装する利点はありません。 実装する例については、<xref:System.Data.Services.IUpdatable>インターフェイスは、「[方法。SQL データ ソースを LINQ を使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)します。  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>関連項目

- [方法: SQL データ ソースを LINQ を使用してデータ サービスを作成します。](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
- [Data Services プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [方法: ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成します。](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
