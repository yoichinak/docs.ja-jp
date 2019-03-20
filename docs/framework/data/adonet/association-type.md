---
title: アソシエーション型
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 65fb5c8e37c8edf7f36cc08258874eeaf234c402
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185598"
---
# <a name="association-type"></a>アソシエーション型
*アソシエーション型*(アソシエーションとも呼ばれます) は、Entity Data Model (EDM) でのリレーションシップを記述するための基本的なビルド ブロックです。 概念モデルでは、アソシエーションは 2 つの間のリレーションシップを表します。[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)(など`Customer`と`Order`)。 アプリケーションでは、アソシエーションのインスタンスが特定のアソシエーション (`Customer` のインスタンスと `Order` のインスタンスの間のアソシエーションなど) を表します。 アソシエーション インスタンスはで論理的にグループ化、[アソシエーション セット](../../../../docs/framework/data/adonet/association-set.md)します。  
  
 アソシエーションの定義には、次の情報が含まれます。  
  
-   一意の名前  (必須)  
  
-   2 つ[アソシエーション end](../../../../docs/framework/data/adonet/association-end.md)リレーションシップのエンティティ型ごとに 1 つ。 (必須)  
  
    > [!NOTE]
    >  アソシエーションは、2 つ以上のエンティティ型のリレーションシップを表すことができません。 しかし、各アソシエーション End に同じエンティティ型を指定することによって、アソシエーションで自己リレーションシップを定義できます。  
  
-   A[参照整合性制約](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)します。 (オプション)。  
  
 各アソシエーション end を指定する必要があります、[アソシエーション end の多重度](../../../../docs/framework/data/adonet/association-end-multiplicity.md)アソシエーションの 1 つの end に存在できるエンティティ型のインスタンスの数を示します。 値の 1 つ (1)、0 個または 1 (0..1)、または複数のアソシエーション end の多重度を持つことができます (\*)。 アソシエーションの一方の end のエンティティ型のインスタンスを介してアクセスできる[ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)またはエンティティ型で公開されている場合、外部キーです。 詳細については、次を参照してください[Entity Data Model:。外部キー](../../../../docs/framework/data/adonet/foreign-key-property.md)します。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。 
  `PublishedBy` アソシエーションのアソシエーション End は `Book` および `Publisher` のエンティティ型です。 多重度、 `Publisher` end が 1 つ (1) との多重度、 `Book` end が多く (\*)、出版社が多くの書籍、書籍は 1 つのパブリッシャーによって公開されたことを示します。  
  
 ![モデルの例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された `PublishedBy` アソシエーションを定義しています。  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
