---
title: リレーションシップの推論
ms.date: 03/30/2017
ms.assetid: 8fa86a9d-6545-4a9d-b1f5-58d9742179c7
ms.openlocfilehash: 92a4953dc7f5119ffbf171ff2a7bf5b58e896638
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204772"
---
# <a name="inferring-relationships"></a>リレーションシップの推論
テーブルとして推論される要素に、同じくテーブルとして推論される子の要素が含まれている場合には、2 つのテーブル間に <xref:System.Data.DataRelation> が作成されます。 **ParentTableName_Id**という名前の新しい列が、親要素用に作成されたテーブルと、子要素に対して作成されたテーブルの両方に追加されます。 この id 列の**ColumnMapping**プロパティは、 **Mappingtype. Hidden**に設定されます。 この列は、親テーブルの自動インクリメント主キーになり、2つのテーブル間の**DataRelation**に使用されます。 追加された id 列のデータ型は、他のすべての推定列 (system.string) のデータ型とは異なり、 **system.string**になります。 **DeleteRule** <xref:System.Data.ForeignKeyConstraint> Cascade = を指定したは、親テーブルと子テーブルの両方で新しい列を使用して作成されます。  
  
 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1 attr1="value1" attr2="value2"/>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推論プロセスでは、次の2つのテーブルが生成されます。**Element1**と**ChildElement1**。  
  
 **Element1**テーブルには、次の2つの列があります。**Element1_Id**と**ChildElement2**。 **Element1_Id**列の**ColumnMapping**プロパティは、 **mappingtype. Hidden**に設定されます。 **ChildElement2**列の**ColumnMapping**プロパティは、 **mappingtype. Element**に設定されます。 **Element1_Id**列は、 **Element1**テーブルの主キーとして設定されます。  
  
 **ChildElement1**テーブルには、 **attr1**、 **attr2** 、 **Element1_Id**の3つの列があります。 **Attr1**列と**Attr2**列の**ColumnMapping**プロパティは、 **mappingtype. Attribute**に設定されます。 **Element1_Id**列の**ColumnMapping**プロパティは、 **mappingtype. Hidden**に設定されます。  
  
 両方のテーブルの**Element1_Id**列を使用して、 **DataRelation**と**ForeignKeyConstraint**が作成されます。  
  
 **セット**DocumentElement  
  
 **一覧**Element1  
  
|Element1_Id|ChildElement2|  
|------------------|-------------------|  
|0|Text2|  
  
 **一覧**ChildElement1  
  
|attr1|attr2|Element1_Id|  
|-----------|-----------|------------------|  
|value1|value2|0|  
  
 **DataRelation**Element1_ChildElement1  
  
 **Parentcolumn**Element1  
  
 **ParentColumn:** Element1_Id  
  
 **ChildTable**ChildElement1  
  
 **ChildColumn:** Element1_Id  
  
 **複合**True  
  
 **ForeignKeyConstraint**Element1_ChildElement1  
  
 **項目**Element1_Id  
  
 **Parentcolumn**Element1  
  
 **ChildTable**ChildElement1  
  
 **DeleteRule**Cascade  
  
 **AcceptRejectRule**なし  
  
## <a name="see-also"></a>関連項目

- [XML からの DataSet リレーショナル構造の推論](inferring-dataset-relational-structure-from-xml.md)
- [XML からの DataSet の読み込み](loading-a-dataset-from-xml.md)
- [XML の DataSet スキーマ情報の読み込み](loading-dataset-schema-information-from-xml.md)
- [DataRelation の入れ子化](nesting-datarelations.md)
- [DataSet での XML の使用](using-xml-in-a-dataset.md)
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
