---
title: Entity Framework プロバイダー (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: 612888aaa11c606112527f01864897560061845f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790850"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Entity Framework プロバイダー (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] と同様に、ADO.NET Entity Framework は、エンティティ リレーションシップ モデルの型である Entity Data Model をベースにしています。 Entity Framework は、*概念モデル*と呼ばれる Entity Data Model の実装に対する操作を、データソースに対する同等の操作に変換します。 このことから、Entity Framework はリレーショナル データに基づくデータ サービスの理想的なプロバイダーとして使用でき、また、Entity Framework をサポートするデータ プロバイダーが存在するデータベースであれば、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で使用できます。 現在 Entity Framework をサポートしているデータソースの一覧については、「 [Entity Framework のサードパーティプロバイダー](https://go.microsoft.com/fwlink/?LinkId=143699)」を参照してください。  
  
 概念モデルでは、エンティティ コンテナーはサービスのルートです。 データ サービスでデータを公開する前に、Entity Framework で概念モデルを定義する必要があります。 詳細については、「[方法 :ADO.NET Entity Framework データソース](create-a-data-service-using-an-adonet-ef-data-wcf.md)を使用してデータサービスを作成します。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]は、エンティティの同時実行トークンを定義できるようにすることで、オプティミスティック同時実行制御モデルをサポートします。 このコンカレンシー トークンは、エンティティの 1 つ以上のプロパティが含まれており、要求、更新、または削除されているデータに対して行われた変更があるかどうかを判断するためにデータ サービスによって使用されます。 要求内の eTag から取得したトークンの値がエンティティの現在の値と異なる場合、データ サービスで例外が発生します。 プロパティがコンカレンシー トークンの一部であることを示す場合、`ConcurrencyMode="Fixed"` プロバイダーで定義されているデータ モデルに属性 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] を適用する必要があります。 コンカレンシー トークンには、キー プロパティまたはナビゲーション プロパティを含めることはできません。 詳細については、「[データサービスの更新](updating-the-data-service-wcf-data-services.md)」を参照してください。  
  
 Entity Framework の詳細については、「 [Entity Framework の概要](../adonet/ef/overview.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [Data Services プロバイダー](data-services-providers-wcf-data-services.md)
- [リフレクション プロバイダー](reflection-provider-wcf-data-services.md)
- [Entity Data Model](../adonet/entity-data-model.md)
