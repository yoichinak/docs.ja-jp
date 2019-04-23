---
title: エンティティ コンテナー
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 4a629a800df63c67dc17d3fc1531a9862861e9c4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144067"
---
# <a name="entity-container"></a>エンティティ コンテナー
*エンティティ コンテナー*の論理的なグループは、[エンティティ セット](../../../../docs/framework/data/adonet/entity-set.md)、[アソシエーション セット](../../../../docs/framework/data/adonet/association-set.md)、および[関数インポート](../../../../docs/framework/data/adonet/model-declared-function.md)します。  
  
 概念モデルで定義するエンティティ コンテナーは、次の条件を満たしている必要があります。  
  
-   1 つ以上のエンティティ コンテナーを各概念モデルに定義すること。  
  
-   各概念モデル内のエンティティ コンテナー名が一意であること。  
  
 エンティティ コンテナーは、1 つ以上の名前空間に定義されたエンティティ型またはアソシエーションを使用するエンティティ セットまたはアソシエーション セットを定義できます。 詳細については、次を参照してください[Entity Data Model:。名前空間](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)します。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  詳細については、次の例を参照してください。  
  
 ![次の 3 つのエンティティの種類とモデルの例](./media/entity-container/example-model-three-entity-types.gif)  
  
 ダイアグラムにはエンティティ コンテナー情報が示されていませんが、概念モデルにはエンティティ コンテナーを定義する必要があります。 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれる DSL を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された概念モデルのエンティティ コンテナーを定義しています。 エンティティ コンテナー名は XML 属性に定義されています。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
