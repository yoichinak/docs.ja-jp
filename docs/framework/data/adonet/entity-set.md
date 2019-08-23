---
title: エンティティ セット
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 4473b74a4142bb49076068b50dc8b6f9c2c0d54a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959233"
---
# <a name="entity-set"></a>エンティティ セット
エンティティ*セット*は、[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)のインスタンスと、そのエンティティ型から派生した任意の型のインスタンスの論理コンテナーです。 派生型の詳細については[、Entity Data Model を参照してください。継承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)。)エンティティ型とエンティティセットのリレーションシップは、リレーショナルデータベースの行とテーブルのリレーションシップに似ています。行と同様に、エンティティ型はデータ構造を記述します。また、テーブルと同様に、エンティティセットには特定の構造体のインスタンスが含まれます。 エンティティ セットは、データ モデリング構造ではなく、データ構造を表しません。 エンティティ セットは、エンティティ型のインスタンスをグループ化してデータ ストアにマップするための、ホスト環境またはストレージ環境 (共通言語ランタイムや SQL Server データベースなど) の構造を提供します。  
  
 エンティティセットは、エンティティセットと[アソシエーションセット](../../../../docs/framework/data/adonet/association-set.md)の論理的なグループである[エンティティコンテナー](../../../../docs/framework/data/adonet/entity-container.md)内で定義されます。  
  
 エンティティ型のインスタンスがエンティティ セット内に存在できるようにするには、次の条件を満たしている必要があります。  
  
- インスタンスの型がエンティティ セットの基本になるエンティティ型と同じであるか、インスタンスの型がエンティティ型のサブタイプであること。  
  
- インスタンスの[エンティティキー](../../../../docs/framework/data/adonet/entity-key.md)は、エンティティセット内で一意です。  
  
- インスタンスが他のエンティティ セットに存在しないこと。  
  
    > [!NOTE]
    > 同じエンティティ型を使用して複数のエンティティ セットを定義できますが、特定のエンティティ型のインスタンスは、1 つのエンティティ セット内のみに存在できます。  
  
 概念モデルの各エンティティ型にはエンティティ セットを定義する必要がありません。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。  
  
 ![3種類のエンティティを持つモデルの例](./media/entity-set/example-model-three-entity-types.gif)  
  
 次のダイアグラムには、上の概念モデルに基づく 2 つのエンティティ セット (`Books` および `Publishers`) と、アソシエーション セット(`PublishedBy`) を示しています。 `Books`エンティティセット内の Bi は、 `Book`実行時にエンティティ型のインスタンスを表します。 同様に、Pj は`Publisher` `Publishers`エンティティセット内のインスタンスを表します。 Bipj は、 `PublishedBy`アソシエーションセット内`PublishedBy`のアソシエーションのインスタンスを表します。  
  
 ![セットの例を示すスクリーンショット。](./media/entity-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)は、概念スキーマ定義言語 ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。 次の CSDL は、上の概念モデルに示された各エンティティ型に対して 1 つのエンティティ セットを持つエンティティ コンテナーを定義しています。 各エンティティ セットの名前とエンティティ型は、XML 属性で定義されています。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 型ごとに複数のエンティティ セット (Multiple-Entity-Sets-per-Type: MEST) を定義できます。 次の CSDL は、`Book` エンティティ型のエンティティ セットを 2 つ持つエンティティ コンテナーを定義しています。  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
