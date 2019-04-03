---
title: ナビゲーションのプロパティ - ADO.NET
ms.date: 03/30/2017
ms.assetid: d0bf1a6a-1d84-484c-b7c3-b410fd8dc0b1
ms.openlocfilehash: b57ecf9329aa9ea8afc07507613c9e3961bfd0a9
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2019
ms.locfileid: "58836599"
---
# <a name="navigation-property"></a>ナビゲーション プロパティ

A*ナビゲーション プロパティ*で、省略可能なプロパティは、[エンティティ型](entity-type.md)から 1 つのナビゲーションの利用できる[エンド](association-end.md)の[アソシエーション](association-type.md)にその他の終了時刻です。 その他とは異なり[プロパティ](property.md)、ナビゲーション プロパティにデータを使用することはありません。

ナビゲーション プロパティの定義には、以下が含まれます。

- 名前。 (必須)

- 移動対象のアソシエーション。 (必須)

- 移動対象のアソシエーションの End。 (必須)

ナビゲーション プロパティは、アソシエーション End の両方のエンティティ型で省略可能です。 1 つのアソシエーション End のエンティティ型にナビゲーション プロパティを定義した場合に、そのアソシエーションの他方の End でもエンティティ型にナビゲーション プロパティを定義する必要はありません。

ナビゲーション プロパティのデータ型はによって決定されます、[多重度](association-end-multiplicity.md)、リモートの[アソシエーション end](association-end.md)します。 たとえば、ナビゲーション プロパティ `OrdersNavProp` が `Customer` エンティティ型に存在し、`Customer` と `Order` の間の一対多のアソシエーションで移動するとします。 ナビゲーション プロパティのリモートのアソシエーション end は、多くの多重度があるため (\*)、そのデータ型は、コレクション (の`Order`)。 同様に、`CustomerNavProp` エンティティ型にナビゲーション プロパティ、`Order` が存在する場合、リモート End の多重度が (1) であるため、データ型は `Customer` になります。

## <a name="example"></a>例

下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。 Book エンティティ型には、ナビゲーション プロパティ、`Publisher` および `Authors` が定義されています。 Publisher エンティティ型と `Books` エンティティ型には、ナビゲーション プロパティ、`Author` が定義されています。

 ![次の 3 つのエンティティ型を持つ概念モデルを示す図。](./media/navigation-property/conceptual-model-entity-types-associations.gif)  

[ADO.NET Entity Framework](./ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](./ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、上のダイアグラムに示された `Book` エンティティ型を定義しています。

[!code-xml[EDM_Example_Model#EntityExample](~/samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]

ナビゲーション プロパティを定義するために必要な情報を伝達する XML 属性が使用されることに注意してください。属性`Name`、プロパティの名前が含まれています`Relationship`、移動対象の関連付けの名前が含まれていますと`FromRole`と`ToRole`アソシエーションの end が含まれています。

## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
- [リレーションシップ、ナビゲーション プロパティ、および外部キー](/ef/ef6/fundamentals/relationships)
