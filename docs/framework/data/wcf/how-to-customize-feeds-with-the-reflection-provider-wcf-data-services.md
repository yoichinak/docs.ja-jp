---
title: '方法: リフレクション プロバイダー (WCF Data Services) を使用したフィードをカスタマイズします。'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: 00c23dcf-9bb8-459a-a012-6c4d9bcad7e9
ms.openlocfilehash: fe6e65a0030ca016f280e6b2c1106b4aa302d26e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637704"
---
# <a name="how-to-customize-feeds-with-the-reflection-provider-wcf-data-services"></a>方法: リフレクション プロバイダー (WCF Data Services) を使用したフィードをカスタマイズします。
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] では、データ サービス応答の Atom シリアル化をカスタマイズして、AtomPub プロトコルで定義されている未使用の要素にエンティティのプロパティをマップできます。 このトピックでは、リフレクション プロバイダーを使用して、定義されているデータ モデル内のエンティティ型のマッピング属性を定義する方法について説明します。 詳細については、[フィードのカスタマイズ](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md)を参照してください。  
  
 この例では、データ モデルが、トピックで定義されている[方法。リフレクション プロバイダーを使用してデータ サービスを作成します。](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)  
  
## <a name="example"></a>例  
 次の例では、`Order` 型の両方のプロパティが既存の Atom 要素にマップされます。 `Product` 型の `Item` プロパティは、別の名前空間のカスタム フィード属性にマップされます。  
  
 [!code-csharp[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria custom feeds/cs/orderitems.svc.cs#customiqueryablefeeds)]
 [!code-vb[Astoria Custom Feeds#CustomIQueryableFeeds](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria custom feeds/vb/orderitems.svc.vb#customiqueryablefeeds)]  
  
## <a name="example"></a>例  
 前の例では、URI `http://myservice/OrderItems.svc/Orders(0)?$expand=Items` に次の結果が返されます。  
  
 [!code-xml[Astoria Custom Feeds#IQueryableFeedResultInline](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/iqueryablefeedresultinline.xml#iqueryablefeedresultinline)]  
  
## <a name="see-also"></a>関連項目
- [リフレクション プロバイダー](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
