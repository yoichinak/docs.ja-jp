---
title: Entity Data Model:名前空間
ms.date: 03/30/2017
ms.assetid: 98ab4226-bb9f-44e7-af46-61a9b1a4e47c
ms.openlocfilehash: 7772172512d35b9ce9cf07a992c1c5f0ecd8c55b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59180572"
---
# <a name="entity-data-model-namespaces"></a>Entity Data Model:名前空間
名前空間の Entity Data Model (EDM) では、抽象コンテナー[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)、[複合型](../../../../docs/framework/data/adonet/complex-type.md)、および[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)します。 EDM の名前空間はプログラミング言語の名前空間と似ており、その中に含まれるオブジェクトのコンテキストを指定し、同じ名前を持つ (しかし、別の名前空間に含まれる) オブジェクトを明確に区別する手段になります。  
  
## <a name="example"></a>例  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL コードは、名前空間を使用して異なる概念モデルに定義された型を識別します。 この例は、`Publisher` 名前空間からインポートされた複合型のプロパティ (`Address`) を持つエンティティ型 (`ExtendedBooksModel`) を定義します。 `Using` 要素は、名前空間がインポートされていることを示します。 さらに、`Address` プロパティの型は、完全修飾名 (`ExtendedBooksModel.Address`) で定義されており、この型が `ExtendedBooksModel` 名前空間で定義されていることを示します。  
  
 [!code-xml[EDM_Example_Model#ImportedNamespace](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books6.edmx#importednamespace)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [エンティティ データ モデル](../../../../docs/framework/data/adonet/entity-data-model.md)
