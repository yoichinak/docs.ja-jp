---
title: 関連付けセット
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: 43ab6cf9f1ee8cb971810add6b9a89467726f3e2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785032"
---
# <a name="association-set"></a>関連付けセット
*アソシエーションセット*は、同じ型の[アソシエーション](association-type.md)インスタンスの論理コンテナーです。 アソシエーション セットは、データ モデリング構造ではなく、データ構造やリレーションシップを表しません。 アソシエーション セットは、アソシエーション インスタンスをグループ化してデータ ストアにマップするための、ホスト環境またはストレージ環境 (共通言語ランタイムや SQL Server データベースなど) の構造を提供します。  
  
 アソシエーションセットは、エンティティ[セット](entity-set.md)とアソシエーションセットの論理的なグループである[エンティティコンテナー](entity-container.md)内で定義されます。  
  
 アソシエーション セットの定義には、次の情報が含まれます。  
  
- アソシエーション セット名。 (必須)  
  
- インスタンスを含むアソシエーション。 (必須)  
  
- 2つの[アソシエーションセットが終了](association-set-end.md)します。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。 このダイアグラムにはアソシエーション セットに関する情報が示されていませんが、次のダイアグラムはこのモデルに基づくアソシエーション セットとエンティティ セットの例を示しています。  
  
 ![3種類のエンティティを持つモデルの例](./media/association-set/example-model-three-entity-types.gif)  
  
 次の例は、上の概念モデルに基づくアソシエーション セット(`PublishedBy`) と 2 つのエンティティ セット (`Books` および `Publishers`) を示しています。 `Books`エンティティセット内の Bi は、 `Book`実行時にエンティティ型のインスタンスを表します。 同様に、Pj は`Publisher` `Publishers`エンティティセット内のインスタンスを表します。 Bipj は、 `PublishedBy`アソシエーションセット内`PublishedBy`のアソシエーションのインスタンスを表します。  
  
 ![セットの例を示すスクリーンショット。](./media/association-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md)は、概念スキーマ定義言語 ([CSDL](./ef/language-reference/csdl-specification.md)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。 次の CSDL は、上のダイアグラムの各アソシエーションに対して 1 つのアソシエーション セットを持つエンティティ コンテナーを定義しています。 各アソシエーション セットの名前とアソシエーションは、XML 属性で定義しています。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 アソシエーション[セット end](association-set-end.md)を共有する2つのアソシエーションセットがない限り、アソシエーションごとに複数のアソシエーションセットを定義できます。 次の CSDL は、`WrittenBy` アソシエーションの 2 つのアソシエーション セットを含むエンティティ コンテナーを定義しています。 `Book` エンティティ型と `Author` エンティティ型には複数のエンティティ セットが定義され、同じアソシエーション セット End を共有するアソシエーション セットがないことに注意してください。  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
- [外部キーのプロパティ](foreign-key-property.md)
