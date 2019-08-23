---
title: アソシエーション型
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 17465dbec3f5e2896cf755a1f8585734388f54ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948296"
---
# <a name="association-type"></a>アソシエーション型
*アソシエーション型*(アソシエーションとも呼ばれます) は、ENTITY DATA MODEL (EDM) でリレーションシップを記述するための基本的な構成要素です。 概念モデルでは、アソシエーションは、2つの[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)( `Customer`や`Order`など) 間のリレーションシップを表します。 アプリケーションでは、アソシエーションのインスタンスが特定のアソシエーション (`Customer` のインスタンスと `Order` のインスタンスの間のアソシエーションなど) を表します。 アソシエーションインスタンスは、[アソシエーションセット](../../../../docs/framework/data/adonet/association-set.md)に論理的にグループ化されます。  
  
 アソシエーションの定義には、次の情報が含まれます。  
  
- 一意の名前 (必須)  
  
- リレーションシップのエンティティ型ごとに1つずつ、2つの[アソシエーションが終了](../../../../docs/framework/data/adonet/association-end.md)します。 (必須)  
  
    > [!NOTE]
    > アソシエーションは、2 つ以上のエンティティ型のリレーションシップを表すことができません。 しかし、各アソシエーション End に同じエンティティ型を指定することによって、アソシエーションで自己リレーションシップを定義できます。  
  
- [参照整合性制約](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)。 (オプション)  
  
 各アソシエーション end には、アソシエーションの1つの end に存在できるエンティティ型インスタンスの数を示す[アソシエーション end の多重度](../../../../docs/framework/data/adonet/association-end-multiplicity.md)を指定する必要があります。 アソシエーション end の多重度には、1 (1)、0または 1 (0 ..1)、または many (\*) を指定できます。 アソシエーションの1つの end にあるエンティティ型のインスタンスは、エンティティ型で公開されている場合、[ナビゲーションプロパティ](../../../../docs/framework/data/adonet/navigation-property.md)または外部キーを使用してアクセスできます。 詳細については[、Entity Data Model を参照してください。外部キー](../../../../docs/framework/data/adonet/foreign-key-property.md)。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。 `PublishedBy` アソシエーションのアソシエーション End は `Book` および `Publisher` のエンティティ型です。 `Publisher` End の多重度は 1 (1) で、 `Book` end の多重度は多数 (\*) であり、出版社が多数の書籍を出版し、書籍が1つの出版社によって発行されていることを示します。  
  
 ![3種類のエンティティを持つモデルの例](./media/association-type/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)は、概念スキーマ定義言語 ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された `PublishedBy` アソシエーションを定義しています。  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
