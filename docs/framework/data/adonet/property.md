---
title: property
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 71a04f334ec465b0f11cc8f18f2680df651081eb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59181650"
---
# <a name="property"></a>property
*プロパティ*の基本的な構成要素を[エンティティ型](../../../../docs/framework/data/adonet/entity-type.md)と[複合型](../../../../docs/framework/data/adonet/complex-type.md)します。 プロパティは、エンティティ型または複合型のインスタンスに含まれるデータの形と特性を定義します。 概念モデルのプロパティは、クラスに定義されるプロパティに似ています。 クラスのプロパティがクラスの構造を定義し、オブジェクトに関する情報を伝達するのと同様に、概念モデルのプロパティはエンティティ型の構造を定義し、エンティティ型のインスタンスに関する情報を伝達します。  
  
> [!NOTE]
>  このトピックで説明するプロパティは、ナビゲーション プロパティとは異なります。 詳細については、次を参照してください。[ナビゲーション プロパティ](../../../../docs/framework/data/adonet/navigation-property.md)します。  
  
 プロパティの定義には、次の情報が含まれます。  
  
-   プロパティ名。 (必須)  
  
-   プロパティの型。 (必須)  
  
-   一連の[ファセット](../../../../docs/framework/data/adonet/facet.md)します。 (オプション)。  
  
 プロパティには、プリミティブ データ (文字列、整数、ブール値など) または構造化データ (複合型) を含めることができます。 プリミティブ型のプロパティは、スカラー プロパティとも呼ばれます。 詳細については、次を参照してください[Entity Data Model:。プリミティブ データ型](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)します。  
  
> [!NOTE]
>  複合型自体に、複合型のプロパティを指定することができます。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。 各エンティティ型には、いくつかのプロパティがありますが、ダイアグラムには各プロパティの型情報が示されていません。 プロパティを[エンティティ キー](../../../../docs/framework/data/adonet/entity-key.md) (キー) と示されています。  
  
 ![次の 3 つのエンティティの種類とモデルの例](./media/property/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)概念スキーマ定義言語と呼ばれるドメイン固有言語 (DSL) を使用して ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 概念モデルを定義します。 次の CSDL は、`Book` エンティティ型 (上のダイアグラムに示されたように) を定義し、XML 属性により各プロパティの型と名前を示しています。 ファセット `Nullable` (省略可能) も XML 属性により定義されています。  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 ダイアグラムに示されたいずれかのプロパティが複合型のプロパティであることも考えられます。 たとえば、`Address` エンティティ型の `Publisher` プロパティは、`StreetAddress`、`City`、`StateOrProvince`、`Country`、`PostalCode` などいくつかのスカラー プロパティから構成された複合型のプロパティである可能性があります。 このような複合型の CSDL 表現は、次のようになります。  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [エンティティ データ モデル](../../../../docs/framework/data/adonet/entity-data-model.md)
