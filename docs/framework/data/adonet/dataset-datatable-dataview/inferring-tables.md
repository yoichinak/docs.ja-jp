---
title: テーブルの推論
ms.date: 03/30/2017
ms.assetid: 74a288d4-b8e9-4f1a-b2cd-10df92c1ed1f
ms.openlocfilehash: 174d305688c7090c163df60a11e233aea24b8f79
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587361"
---
# <a name="inferring-tables"></a>テーブルの推論
XML ドキュメントから <xref:System.Data.DataSet> のスキーマを推論するときには、ADO.NET では、テーブルを表す XML 要素を最初に決定します。 次の XML 構造の結果のテーブルに、**データセット**スキーマ。  
  
- 属性を持つ要素  
  
- 子要素を持つ要素  
  
- 繰り返し出現する要素  
  
## <a name="elements-with-attributes"></a>属性を持つ要素  
 要素に属性が指定されている場合は、それらの要素はテーブルとして推論されます。 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1"/>  
  <Element1 attr1="value2">Text1</Element1>  
</DocumentElement>  
```  
  
 推論プロセスにより、"Element1" という名前のテーブルが生成されます。  
  
 **データセット:** DocumentElement  
  
 **テーブル:** Element1  
  
|attr1|Element1_Text|  
|-----------|--------------------|  
|value1||  
|value2|Text1|  
  
## <a name="elements-with-child-elements"></a>子要素を持つ要素  
 子要素を持つ要素は、テーブルとして推論されます。 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
  </Element1>  
</DocumentElement>  
```  
  
 推論プロセスにより、"Element1" という名前のテーブルが生成されます。  
  
 **データセット:** DocumentElement  
  
 **テーブル:** Element1  
  
|ChildElement1|  
|-------------------|  
|Text1|  
  
 ドキュメント (ルート) 要素に属性または子要素があり、それらが列として推論される場合には、そのドキュメント要素はテーブルとして推論されます。 ドキュメント要素の属性も列として推論される子要素はありませんが、要素として推論されます、**データセット**します。 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element2>Text2</Element2>  
</DocumentElement>  
```  
  
 推論プロセスにより、"DocumentElement" という名前のテーブルが生成されます。  
  
 **データセット:** NewDataSet  
  
 **テーブル:** DocumentElement  
  
|Element1|Element2|  
|--------------|--------------|  
|Text1|Text2|  
  
 または、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 推論プロセスによって生成される、**データセット**"Element1"という名前のテーブルを含む"DocumentElement"という名前  
  
 **データセット:** DocumentElement  
  
 **テーブル:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="repeating-elements"></a>繰り返し出現する要素  
 繰り返し出現する要素は、単一のテーブルとして推論されます。 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 推論プロセスにより、"Element1" という名前のテーブルが生成されます。  
  
 **データセット:** DocumentElement  
  
 **テーブル:** Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
## <a name="see-also"></a>関連項目

- [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
