---
title: XML スキーマ (XSD) 制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b44c3193e1b9e2e52e086111eab0ab0b0cae5c97
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786075"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML スキーマ (XSD) 制約の DataSet 制約への割り当て
XML スキーマ定義言語 (XSD) を使用すると、定義する要素と属性で制約を指定できます。 Xml スキーマを内の<xref:System.Data.DataSet>リレーショナルスキーマにマップする場合、xml スキーマ制約は、**データセット**内のテーブルおよび列に対する適切なリレーショナル制約にマップされます。  
  
 このセクションでは、次の XML スキーマの制約の割り当てについて説明します。  
  
- **Unique**要素を使用して指定された一意性制約。  
  
- **Key**要素を使用して指定されたキー制約。  
  
- **Keyref**要素を使用して指定された keyref 制約。  
  
 要素または属性に対して制約を指定することにより、同じスキーマに基づくあらゆるドキュメントで、その要素の値について特定の制限を適用できます。 たとえば、スキーマ内の**Customer**要素の**customerid**子要素のキー制約は、 **customerid**子要素の値がドキュメントインスタンス内で一意であること、および null 値が許可されていないことを示します。  
  
 さらに、ドキュメント内のリレーションシップを確立するために、ドキュメント内の要素および属性間に制約を指定することもできます。 ドキュメント内で制約を指定するためにスキーマ内で key 制約または keyref 制約を使用すると、ドキュメントの要素と属性間にリレーションシップを持つことになります。  
  
 マッピングプロセスでは、これらのスキーマ制約が、**データセット**内に作成されたテーブルに対する適切な制約に変換されます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 **データセット**内に unique 制約を作成するために使用される XML スキーマ要素について説明します。  
  
 [XML スキーマ (XSD) のキー制約の DataSet 制約への割り当て](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 **データセット**内のキー制約 (null 値が許可されない) を作成するために使用される XML スキーマ要素について説明します。  
  
 [XML スキーマ (XSD) のキー参照制約の DataSet 制約への割り当て](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 **DataSet**で keyref (外部キー) 制約を作成するために使用される XML スキーマ要素について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 XSD スキーマから作成される**データセット**のリレーショナル構造 (スキーマ) について説明します。  
  
 [XML スキーマ (XSD) からの DataSet リレーションの生成](generating-dataset-relations-from-xml-schema-xsd.md)  
 **データセット**内のテーブル列間のリレーションを作成するために使用される XML スキーマ要素について説明します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../ado-net-overview.md)
