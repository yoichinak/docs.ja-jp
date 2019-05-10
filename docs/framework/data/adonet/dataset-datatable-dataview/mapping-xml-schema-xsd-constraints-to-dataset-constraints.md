---
title: XML スキーマ (XSD) 制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: cdbfba96c4cfe52cfbd58246be60842540a84754
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64603997"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML スキーマ (XSD) 制約の DataSet 制約への割り当て
XML スキーマ定義言語 (XSD) を使用すると、定義する要素と属性で制約を指定できます。 リレーショナル スキーマに XML スキーマをマップするとき、 <xref:System.Data.DataSet>、XML スキーマの制約は、テーブルや列内で適切なリレーショナル制約にマップされて、**データセット**します。  
  
 このセクションでは、次の XML スキーマの制約の割り当てについて説明します。  
  
- 使用して指定される unique 制約、**一意**要素。  
  
- 使用して指定されたキーの制約、**キー**要素。  
  
- 使用して指定されるキー参照制約、 **keyref**要素。  
  
 要素または属性に対して制約を指定することにより、同じスキーマに基づくあらゆるドキュメントで、その要素の値について特定の制限を適用できます。 たとえば、キー制約を**CustomerID**の子要素、**顧客**スキーマ内の要素には、ことを示しますの値、 **CustomerID**子要素である必要があります任意のドキュメント インスタンス内で一意で null 値は許可されていません。  
  
 さらに、ドキュメント内のリレーションシップを確立するために、ドキュメント内の要素および属性間に制約を指定することもできます。 ドキュメント内で制約を指定するためにスキーマ内で key 制約または keyref 制約を使用すると、ドキュメントの要素と属性間にリレーションシップを持つことになります。  
  
 マッピング プロセス内で作成されたテーブルに適切な制約にこれらのスキーマの制約を変換する、**データセット**します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 Unique 制約を作成するために使用する XML スキーマの要素について説明します、**データセット**します。  
  
 [XML スキーマ (XSD) のキー制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 キー制約 (一意制約は null 値が許可されていません) を作成するために使用する XML スキーマの要素について説明します、**データセット**します。  
  
 [XML スキーマ (XSD) のキー参照制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 参照で (外部キー) 制約の作成に使用する XML スキーマ要素について説明します、**データセット**します。  
  
## <a name="related-sections"></a>関連項目  
 [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 リレーショナル構造体、またはスキーマをについて説明します、**データセット**XSD スキーマから作成されました。  
  
 [XML スキーマ (XSD) からの DataSet リレーションの生成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 テーブルの列間のリレーションを作成するために使用する XML スキーマの要素について説明します、**データセット**します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
