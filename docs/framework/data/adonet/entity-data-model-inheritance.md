---
title: Entity Data Model:継承
ms.date: 03/30/2017
ms.assetid: 42c7ef24-710a-4af9-8493-cd41c399ecb0
ms.openlocfilehash: 9f77f2ebb86ea050c124fbd1c6f2b30ed9e75a1c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667204"
---
# <a name="entity-data-model-inheritance"></a>Entity Data Model:継承
Entity Data Model (EDM) の継承をサポートしている[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)します。 EDM の継承は、オブジェクト指向プログラミング言語におけるクラスの継承に似ています。 オブジェクト指向言語でクラスでは、概念モデルで定義できますエンティティ型と同様に (、*派生型*) 別のエンティティ型から継承する (、*基本型*)。 ただし、オブジェクト指向プログラミング、クラスとは異なり、概念モデルで、派生型常にすべて継承、[プロパティ](../../../../docs/framework/data/adonet/property.md)と[ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)の基本型。 派生型の継承プロパティは、オーバーライドできません。  
  
 概念モデルでは、派生型が別の派生型を継承する継承階層を構築することができます。 階層 (派生型ではない階層内の 1 つの型) の上部にある型が呼び出される、*ルート型*します。 継承階層で、[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md)ルート型で定義する必要があります。  
  
 複数の型から派生型を継承する継承階層を構築することはできません。 たとえば、`Book` エンティティ型の概念モデルでは、それぞれ `FictionBook` から継承する派生型、`NonFictionBook` および `Book` を定義することができます。 しかし、`FictionBook` 型と `NonFictionBook` 型の両方から継承する型を定義することはできません。  
  
## <a name="example"></a>例  

次の図は、次の 4 つのエンティティ型を持つ概念モデル: `Book`、 `FictionBook`、 `Publisher`、および`Author`します。 `FictionBook` エンティティ型は、`Book` エンティティ型から継承する派生型です。 `FictionBook` 型は、`ISBN (Key)` プロパティ、`Title` プロパティ、および `Revision` プロパティを継承し、`Genre` と呼ばれる追加プロパティを定義します。  
  
 ![次の 4 つのエンティティ型を持つ概念モデルを示す図。](./media/entity-data-model-inheritance/entity-type-inheritance.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された `FictionBook` 型を継承する `Book` エンティティ型を定義しています。  
  
 [!code-xml[EDM_Example_Model#DerivedType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books5.edmx#derivedtype)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Entity Data Model](../../../../docs/framework/data/adonet/entity-data-model.md)
