---
title: 外部キーのプロパティ
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: e2f41c2db9aea26c7954a99ebf3f40b03e8df735
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795033"
---
# <a name="foreign-key-property"></a>外部キーのプロパティ
Entity Data Model (EDM) の*外部キープロパティ*は、別のエンティティ型の[エンティティキー](entity-key.md)を含む[エンティティ型](entity-type.md)のプリミティブ型の[プロパティ](property.md)(またはプリミティブ型のプロパティのセット) です。  
  
 外部キーのプロパティは、リレーショナル データベースの外部キー列に似ています。 リレーショナルデータベースで外部キー列を使用してテーブル内の行間のリレーションシップを作成するのと同じように、概念モデルの外部キープロパティを使用してエンティティ型間の[アソシエーション](association-type.md)を確立します。 [参照整合性制約](referential-integrity-constraint.md)は、型の1つに外部キープロパティがある場合に、2つのエンティティ型間のアソシエーションを定義するために使用されます。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。 `Book` エンティティ型には、`PublisherId` というプロパティがあります。`Publisher` アソシエーションに参照整合性制約を定義するときに、このプロパティは `PublishedBy` エンティティ型のエンティティ キーを参照します。  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "参照制約モデルの例")  
  
 [ADO.NET Entity Framework](./ef/index.md)は、概念スキーマ定義言語 ([CSDL](./ef/language-reference/csdl-specification.md)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。 次の CSDL は、外部キーのプロパティ `PublisherId` を使用して、上の概念モデルに示された `PublishedBy` アソシエーションに参照整合性制約を定義します。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
