---
title: Entity Framework プロバイダー (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 650b5eb6-c71d-4dc1-8b64-b6beaf752114
ms.openlocfilehash: 94a708ca33aa94c7a0143d195803d17d49be4bdb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569116"
---
# <a name="entity-framework-provider-wcf-data-services"></a>Entity Framework プロバイダー (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] と同様に、ADO.NET Entity Framework は、エンティティ リレーションシップ モデルの型である Entity Data Model をベースにしています。 Entity Framework と呼ばれるエンティティ データ モデルの実装に対する操作の変換、*概念モデル*、データ ソースに対する同等の操作にします。 このことから、Entity Framework はリレーショナル データに基づくデータ サービスの理想的なプロバイダーとして使用でき、また、Entity Framework をサポートするデータ プロバイダーが存在するデータベースであれば、[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] で使用できます。 現在、Entity Framework をサポートするデータ ソースの一覧では、[Entity Framework 用のサード パーティ プロバイダー](https://go.microsoft.com/fwlink/?LinkId=143699)を参照してください。  
  
 概念モデルでは、エンティティ コンテナーはサービスのルートです。 データ サービスでデータを公開する前に、Entity Framework で概念モデルを定義する必要があります。 詳細については、「[方法 :ADO.NET Entity Framework データ ソースを使用してデータ サービスを作成する](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)します。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 有効にすると、エンティティの同時実行トークンを定義するには、オプティミスティック同時実行制御モデルをサポートします。 このコンカレンシー トークンは、エンティティの 1 つ以上のプロパティが含まれており、要求、更新、または削除されているデータに対して行われた変更があるかどうかを判断するためにデータ サービスによって使用されます。 要求内の eTag から取得したトークンの値がエンティティの現在の値と異なる場合、データ サービスで例外が発生します。 プロパティがコンカレンシー トークンの一部であることを示す場合、`ConcurrencyMode="Fixed"` プロバイダーで定義されているデータ モデルに属性 [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] を適用する必要があります。 コンカレンシー トークンには、キー プロパティまたはナビゲーション プロパティを含めることはできません。 詳細については、[データ サービスの更新](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)を参照してください。  
  
 Entity Framework の詳細については、[Entity Framework の概要](../../../../docs/framework/data/adonet/ef/overview.md)を参照してください。  
  
## <a name="see-also"></a>関連項目
- [Data Services プロバイダー](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [リフレクション プロバイダー](../../../../docs/framework/data/wcf/reflection-provider-wcf-data-services.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
