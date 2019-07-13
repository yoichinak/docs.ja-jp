---
title: 要素のテキストの推論
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 6ffe8f2fbf01fbe8dfa9d78f3dfb9e39b6e80b16
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61879633"
---
# <a name="inferring-element-text"></a>要素のテキストの推論
要素がテキストを含む、名前の新しい列 (属性を持つ要素) などに繰り返される要素は、テーブルとして推論される子要素がない場合**TableName_Text**要素に対して推論されるテーブルに追加されます。 要素に含まれているテキストはテーブルの行に追加され、新しい列に格納されます。 **ColumnMapping**新しい列のプロパティに設定する**MappingType.SimpleContent**します。  
  
 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 推論プロセスという名前のテーブルが生成されます**Element1** 2 つの列: **attr1**と**Element1_Text**します。 **ColumnMapping**のプロパティ、 **attr1**列に設定する**MappingType.Attribute**します。 **ColumnMapping**のプロパティ、 **Element1_Text**列に設定する**MappingType.SimpleContent**します。  
  
 **データセット:** DocumentElement  
  
 **テーブル:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1|Text1|  
  
 要素にテキストだけでなく、テキストを含む子の要素も含まれている場合は、その要素に含まれているテキストを格納するための列はテーブルに追加されません。 要素に含まれるテキストは無視されますが、子の要素のテキストはテーブルの行に追加されます。 たとえば、次のような XML があるとします。  
  
```xml  
<Element1>  
  Text1  
  <ChildElement1>Text2</ChildElement1>  
  Text3  
</Element1>  
```  
  
 推論プロセスという名前のテーブルが生成されます**Element1**という 1 つの列を持つ**ChildElement1**します。 テキスト、 **ChildElement1**要素は、テーブルの行に含まれます。 その他のテキストは無視されます。 **ColumnMapping**のプロパティ、 **ChildElement1**列に設定する**MappingType.Element**します。  
  
 **データセット:** DocumentElement  
  
 **テーブル:** Element1  
  
|ChildElement1|  
|-------------------|  
|Text2|  
  
## <a name="see-also"></a>関連項目

- [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
