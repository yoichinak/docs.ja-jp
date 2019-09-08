---
title: property
ms.date: 03/30/2017
ms.assetid: a941c53f-fc97-42c2-8832-0fb9f1d55c06
ms.openlocfilehash: 97d934ac581e7b1a923bf77dcf46121782fe8eab
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783179"
---
# <a name="property"></a>property
*プロパティ*は、[エンティティ型](entity-type.md)と[複合型](complex-type.md)の基本的な構成要素です。 プロパティは、エンティティ型または複合型のインスタンスに含まれるデータの形と特性を定義します。 概念モデルのプロパティは、クラスに定義されるプロパティに似ています。 クラスのプロパティがクラスの構造を定義し、オブジェクトに関する情報を伝達するのと同様に、概念モデルのプロパティはエンティティ型の構造を定義し、エンティティ型のインスタンスに関する情報を伝達します。  
  
> [!NOTE]
> このトピックで説明するプロパティは、ナビゲーション プロパティとは異なります。 詳細については、「[ナビゲーションプロパティ](navigation-property.md)」を参照してください。  
  
 プロパティの定義には、次の情報が含まれます。  
  
- プロパティ名。 (必須)  
  
- プロパティの型。 (必須)  
  
- [ファ](facet.md)セットのセット。 (オプション)。  
  
 プロパティには、プリミティブ データ (文字列、整数、ブール値など) または構造化データ (複合型) を含めることができます。 プリミティブ型のプロパティは、スカラー プロパティとも呼ばれます。 詳細については[、Entity Data Model を参照してください。プリミティブデータ型](entity-data-model-primitive-data-types.md)。  
  
> [!NOTE]
> 複合型自体に、複合型のプロパティを指定することができます。  
  
## <a name="example"></a>例  
 下のダイアグラムは、`Book`、`Publisher`、および `Author` という 3 つのエンティティ型の概念モデルを示しています。 各エンティティ型には、いくつかのプロパティがありますが、ダイアグラムには各プロパティの型情報が示されていません。 [エンティティキー](entity-key.md)であるプロパティは、(キー) で示されます。  
  
 ![3種類のエンティティを持つモデルの例](./media/property/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md)は、概念スキーマ定義言語 ([CSDL](./ef/language-reference/csdl-specification.md)) と呼ばれるドメイン固有言語 (DSL) を使用して概念モデルを定義します。 次の CSDL は、`Book` エンティティ型 (上のダイアグラムに示されたように) を定義し、XML 属性により各プロパティの型と名前を示しています。 ファセット `Nullable` (省略可能) も XML 属性により定義されています。  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 ダイアグラムに示されたいずれかのプロパティが複合型のプロパティであることも考えられます。 たとえば、`Address` エンティティ型の `Publisher` プロパティは、`StreetAddress`、`City`、`StateOrProvince`、`Country`、`PostalCode` などいくつかのスカラー プロパティから構成された複合型のプロパティである可能性があります。 このような複合型の CSDL 表現は、次のようになります。  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
## <a name="see-also"></a>関連項目

- [Entity Data Model キーの概念](entity-data-model-key-concepts.md)
- [Entity Data Model](entity-data-model.md)
