---
title: '方法: リフレクションプロバイダー (WCF Data Services) を使用してデータサービスを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: feee679c37cd3dafb80021752ee25444c54f0809
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791000"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a>方法: リフレクションプロバイダー (WCF Data Services) を使用してデータサービスを作成する
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、<xref:System.Linq.IQueryable%601> インターフェイスを実装するオブジェクトとして公開されているクラスに基づいてデータ モデルを定義できます。 詳細については、「 [Data Services プロバイダー](data-services-providers-wcf-data-services.md)」を参照してください。  
  
## <a name="example"></a>例  
 次の例は、`Orders` および `Items` を含むデータ モデルを定義します。 エンティティ コンテナー クラス `OrderItemData` には、<xref:System.Linq.IQueryable%601> インターフェイスを返す 2 つのパブリック メソッドがあります。 これらのインターフェイスは、`Orders` エンティティ型と `Items` エンティティ型のエンティティ セットです。 `Order` には複数の `Items` を含めることができるので、`Orders` エンティティ型には `Items` オブジェクトのコレクションを返す `Items` ナビゲーション プロパティがあります。 `OrderItemData` エンティティ コンテナー クラスは、<xref:System.Data.Services.DataService%601> データ サービスが派生する `OrderItems` クラスのジェネリック型です。  
  
> [!NOTE]
> この例はメモリ内のデータ プロバイダーを示し、変更は現在のオブジェクト インスタンスの外部で永続化されないので、<xref:System.Data.Services.IUpdatable> インターフェイスを実装する利点はありません。 <xref:System.Data.Services.IUpdatable>インターフェイスを実装する例については[、「方法:LINQ to SQL データソース](create-a-data-service-using-linq-to-sql-wcf.md)を使用してデータサービスを作成します。  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a>関連項目

- [方法: LINQ to SQL データソースを使用してデータサービスを作成する](create-a-data-service-using-linq-to-sql-wcf.md)
- [Data Services プロバイダー](data-services-providers-wcf-data-services.md)
- [方法: ADO.NET Entity Framework データソースを使用してデータサービスを作成する](create-a-data-service-using-an-adonet-ef-data-wcf.md)
