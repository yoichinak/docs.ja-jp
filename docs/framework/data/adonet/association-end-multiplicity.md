---
title: アソシエーション End の多重度
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 151b15a6df021a25f6c3ecea00af147c6b7196ff
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185676"
---
# <a name="association-end-multiplicity"></a>アソシエーション End の多重度
*アソシエーション end の多重度*の数を定義[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)の 1 つの end に存在できるインスタンス、[アソシエーション](../../../../docs/framework/data/adonet/association-type.md)します。  
  
 アソシエーション End の多重度には、次のいずれかの値を指定できます。  
  
-   1 (1):その 1 つのエンティティ型のインスタンスは、アソシエーション end に存在することを示します。  
  
-   0 または 1 (0..1)。アソシエーション end に 0 個または 1 つのエンティティ型のインスタンスが存在することを示します。  
  
-   多数 (\*)。アソシエーション end に 0、1、または複数のエンティティ型のインスタンスが存在することを示します。  
  
 アソシエーションは、多くの場合、そのアソシエーション End の多重度により特徴付けられます。 たとえば、アソシエーションの end が 1 つ (1) と多くの多重度である場合 (\*)、アソシエーションは一対多のアソシエーションと呼ばれます。 次の例で、`PublishedBy` アソシエーションは一対多のアソシエーションです (出版社が多くの書籍を出版し、書籍は 1 社の出版社により出版されます)。 `WrittenBy` アソシエーションは多対多のアソシエーションです (書籍の著者が複数の場合があり、著者は複数の書籍を執筆することができます)。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`PublishedBy` および `WrittenBy` という 2 つのアソシエーションの概念モデルを示しています。 
  `PublishedBy` アソシエーションのアソシエーション End は `Book` および `Publisher` のエンティティ型です。 多重度、 `Publisher` end が 1 つ (1) との多重度、 `Book` end が多く (\*)。  
  
 ![モデルの例](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET Entity Framework は概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された `PublishedBy` アソシエーションを定義しています。  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>関連項目
- [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
