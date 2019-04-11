---
title: アソシエーション End
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: e549254533f8362ce3475fb3aa5dbaffb3e900e5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108291"
---
# <a name="association-end"></a>アソシエーション End
*アソシエーション end*を識別、[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)の一端を[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)とアソシエーションの end に存在できるインスタンスを入力するエンティティの数。 アソシエーション End はアソシエーションの一部として定義され、アソシエーションには必ず 2 つのアソシエーション End が必要です。 [ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)他の 1 つのアソシエーション end から移動できるようにします。  
  
 アソシエーション End の定義には、次の情報が含まれます。  
  
-   アソシエーションに含まれるエンティティ型の 1 つ。 (必須)  
  
    > [!NOTE]
    >  アソシエーションでは、各アソシエーション End に同じエンティティ型を指定することができます。 これにより、自己アソシエーションが作成されます。  
  
-   [アソシエーション end の多重度](../../../../docs/framework/data/adonet/association-end-multiplicity.md)アソシエーションの 1 つの end に存在できるエンティティ型のインスタンスの数を示します。 値の 1 つ (1)、0 個または 1 (0..1)、または複数のアソシエーション end の多重度を持つことができます (\*)。  
  
-   アソシエーション End の名前。 (オプション)。  
  
-   アソシエーション End に実行する CASCADE ON DELETE などの操作の情報。 (オプション)。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。 `PublishedBy` アソシエーションのアソシエーション End は `Book` および `Publisher` のエンティティ型です。 多重度、 `Publisher` end が 1 つ (1) との多重度、 `Book` end が多く (\*)、出版社が多くの書籍、書籍は 1 つのパブリッシャーによって公開されたことを示します。  
  
 ![次の 3 つのエンティティの種類とモデルの例](./media/association-end/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework は概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された `PublishedBy` アソシエーションを定義します。 各アソシエーション End の型、名前、および多重度は、XML 属性 (それぞれ `Type` 属性、`Role` 属性、および `Multiplicity` 属性) で指定されます。 アソシエーション End に実行する操作に関するオプション情報は、XML 要素 (`OnDelete` 要素) に指定します。 この場合、出版社を削除すると、関連付けられたすべての書籍も削除されます。  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [エンティティ データ モデル](../../../../docs/framework/data/adonet/entity-data-model.md)
