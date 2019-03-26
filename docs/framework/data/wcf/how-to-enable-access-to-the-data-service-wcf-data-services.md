---
title: '方法: データ サービス (WCF Data Services) へのアクセスを有効にします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, configuring
ms.assetid: 3d830bcd-32b4-4f26-9287-d58a071452c6
ms.openlocfilehash: d1ce582096de63f60c7f2c99925fa39710bedfb3
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56091943"
---
# <a name="how-to-enable-access-to-the-data-service-wcf-data-services"></a>方法: データ サービス (WCF Data Services) へのアクセスを有効にします。

  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、データ サービスによって公開されているリソースに明示的にアクセス権を付与する必要があります。 つまり、新しいデータ サービスを作成した後も、個々のリソースに対し、エンティティ セットとして明示的にアクセスを許可する必要があります。 このトピックでは読み取りを有効にする方法と、5 つのエンティティへの書き込みアクセスが完了するときに作成される Northwind データ サービスの設定、[クイック スタート](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)します。 
  <xref:System.Data.Services.EntitySetRights> 列挙体は <xref:System.FlagsAttribute> を使用して定義されているので、論理和演算子を使用して 1 つのエンティティ セットに複数のアクセス許可を指定できます。  
  
> [!NOTE]
>  ASP.NET アプリケーションにアクセスできるクライアントは、データ サービスによって公開されるリソースにもアクセスできます。 運用データ サービスで、リソースへの承認されていないアクセスを防止するために、アプリケーション自身もセキュリティで保護する必要があります。 詳細については、[ASP.NET Web サイトをセキュリティで保護する](https://docs.microsoft.com/previous-versions/aspnet/91f66yxt(v=vs.100))を参照してください。  
  
### <a name="to-enable-access-to-the-data-service"></a>データ サービスへのアクセスを有効にするには  
  
-   データ サービスのコードで、`InitializeService` 関数のプレースホルダーのコードを次の内容で置き換えます。  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     これにより、クライアントから `Orders` および `Order_Details` エンティティ セットへの読み取りおよび書き込みアクセスと、`Customers` エンティティ セットへの読み取り専用アクセスが有効になります。  
  
## <a name="see-also"></a>関連項目
- [方法: IIS で実行されている WCF データ サービスを開発します。](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md)
- [データ サービスの構成](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md)
