---
title: '方法: クエリ結果のプロジェクト (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- projection [WCF Data Services]
- WCF Data Services, projection
- query projection [WCF Data Services]
- WCF Data Services, querying
ms.assetid: 474ac625-8770-43ba-8320-d3315ea9530f
ms.openlocfilehash: 4b0646c2ad45a86691b86b1dd5f112f598ee2dfd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974797"
---
# <a name="how-to-project-query-results-wcf-data-services"></a>方法: クエリ結果のプロジェクト (WCF Data Services)
射影は、エンティティの特定のプロパティのみが応答で返されるように指定することにより、クエリによって返されるデータの量を減らすためのメカニズムです。 結果に射影を実行することができます、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]クエリを使用するか、`$select`クエリ オプションまたはを使用して、[選択](~/docs/csharp/language-reference/keywords/select-clause.md)句 ([選択](~/docs/visual-basic/language-reference/queries/select-clause.md)Visual Basic で)、LINQ クエリでします。 詳細については、次を参照してください。[データ サービスのクエリ](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)します。  
  
 このトピックの例では、Northwind サンプル データ サービスおよび自動生成されたクライアント データ サービス クラスを使用します。 このサービスとクライアント データ クラスを作成を完了すると、 [WCF Data Services クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)します。  
  
## <a name="example"></a>例  
 次の例では、アドレス特有のプロパティと Identity プロパティのみを含む新しい CustomerAddress 型に Customer エンティティを射影する LINQ クエリを示します。 この `CustomerAddress` クラスはクライアントで定義され、クライアント ライブラリがエンティティ型として認識できるように属性化されています。  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddress)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddress](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddress)]  
  
## <a name="example"></a>例  
 次の例では、返された Customers エンティティを、Identity プロパティは含まずにアドレス特有のプロパティのみを含む新しい CustomerAddressNonEntity 型に射影する LINQ クエリを示します。 この `CustomerAddressNonEntity` クラスはクライアントで定義され、エンティティ型としては属性化されません。  
  
 [!code-csharp[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#selectcustomeraddressnonentity)]
 [!code-vb[Astoria Northwind Client#SelectCustomerAddressNonEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#selectcustomeraddressnonentity)]  
  
## <a name="example"></a>例  
 次の例では、定義、`CustomerAddress`と`CustomerAddressNonEntity`前の例で使用される型。  
  
 [!code-csharp[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customeraddress.cs#customeraddressdefinition)]
 [!code-vb[Astoria Northwind Client#CustomerAddressDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customeraddress.vb#customeraddressdefinition)]
