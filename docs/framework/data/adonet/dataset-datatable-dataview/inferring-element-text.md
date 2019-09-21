---
title: 要素のテキストの推論
ms.date: 03/30/2017
ms.assetid: 789799e5-716f-459f-a168-76c5cf22178b
ms.openlocfilehash: 3fdd110a14ddfd6065ed552171a8d76ef64e2fb5
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784539"
---
# <a name="inferring-element-text"></a>要素のテキストの推論
要素にテキストが含まれており、テーブルとして推論される子要素がない場合 (属性を持つ要素や要素が繰り返される場合など)、 **TableName_Text**という名前の新しい列が、要素に対して推論されるテーブルに追加されます。 要素に含まれているテキストはテーブルの行に追加され、新しい列に格納されます。 新しい列の**ColumnMapping**プロパティは、 **Mappingtype. SimpleContent**に設定されます。  
  
 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1">Text1</Element1>  
</DocumentElement>  
```  
  
 推論プロセスでは、 **attr1**と**Element1_Text**の2つの列を持つ**Element1**という名前のテーブルが生成されます。 **Attr1**列の**ColumnMapping**プロパティは、 **mappingtype. Attribute**に設定されます。 **Element1_Text**列の**ColumnMapping**プロパティは、 **mappingtype. SimpleContent**に設定されます。  
  
 **セット**DocumentElement  
  
 **一覧**Element1  
  
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
  
 推論プロセスでは、 **ChildElement1**という名前の1つの列を持つ**Element1**という名前のテーブルが生成されます。 **ChildElement1**要素のテキストは、テーブルの行に含まれます。 その他のテキストは無視されます。 **ChildElement1**列の**ColumnMapping**プロパティは、 **mappingtype. Element**に設定されます。  
  
 **セット**DocumentElement  
  
 **一覧**Element1  
  
|ChildElement1|  
|-------------------|  
|Text2|  
  
## <a name="see-also"></a>関連項目

- [XML からの DataSet リレーショナル構造の推論](inferring-dataset-relational-structure-from-xml.md)
- [XML からの DataSet の読み込み](loading-a-dataset-from-xml.md)
- [XML の DataSet スキーマ情報の読み込み](loading-dataset-schema-information-from-xml.md)
- [DataSet での XML の使用](using-xml-in-a-dataset.md)
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET の概要](../ado-net-overview.md)
