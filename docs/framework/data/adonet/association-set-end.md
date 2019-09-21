---
title: アソシエーション セット End
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 48ba84d46e380462405551cc2d826d84368b351a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786930"
---
# <a name="association-set-end"></a>アソシエーション セット End
*アソシエーションセット end*は、[アソシエーションセット](association-set.md)の末尾にある[エンティティ型](entity-type.md)と[エンティティセット](entity-set.md)を識別します。 アソシエーション セット End はアソシエーション セットの一部として定義されます。アソシエーション セットには、アソシエーション セット End が 2 つ必要です。  
  
 アソシエーション セット End の定義には、次の情報が含まれます。  
  
- アソシエーション セットに含まれるエンティティ型の 1 つ。 (必須)  
  
- アソシエーション セットに含まれるエンティティ型のエンティティ セット。 (必須)  
  
## <a name="example"></a>例  
 下のダイアグラムは、`WrittenBy` および `PublishedBy` という 2 つのアソシエーションの概念モデルを示しています。  
  
 ![3種類のエンティティを持つモデルの例](./media/association-set-end/example-model-three-entity-types.gif)  
  
 次のダイアグラムには、上の概念モデルに基づくアソシエーション セット (`PublishedBy`) と 2 つのエンティティ セット (`Books` および `Publishers`) を示しています。 アソシエーション セット End は `Books` および `Publishers` エンティティ セットです。 `Books`エンティティセット内の Bi は、 `Book`実行時にエンティティ型のインスタンスを表します。 同様に、Pj は`Publisher` `Publishers`エンティティセット内のインスタンスを表します。 Bipj は、 `PublishedBy`アソシエーションセット内`PublishedBy`のアソシエーションのインスタンスを表します。  
  
 ![セットの例を示すスクリーンショット。](./media/association-set-end/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md)は、概念スキーマ定義言語 ([CSDL](./ef/language-reference/csdl-specification.md)) と呼ばれる DSL を使用して概念モデルを定義します。 次の CSDL は、上のダイアグラムの各アソシエーションに対して 1 つのアソシエーション セットを持つエンティティ コンテナーを定義しています。 アソシエーション セット End はアソシエーション セット定義の一部として定義されています。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
