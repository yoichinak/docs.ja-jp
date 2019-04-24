---
title: 推論の制限事項
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 308d2ffdd9e2cb16626861e25613657f341a4ccb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076244"
---
# <a name="inference-limitations"></a>推論の制限事項
各ドキュメントに含まれている XML 要素によっては、XML から <xref:System.Data.DataSet> のスキーマを推論するプロセスにより、異なるスキーマが生成される可能性があります。 たとえば、次のような XML ドキュメントがあるとします。  
  
 Document1:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
  <Element1>Text2</Element1>  
</DocumentElement>  
```  
  
 Document2:  
  
```xml  
<DocumentElement>  
  <Element1>Text1</Element1>  
</DocumentElement>  
```  
  
 "Document1"推論プロセスによって、**データセット**"Element1"が繰り返し要素であるために、"DocumentElement"と"Element1、"という名前のテーブルの名前します。  
  
 **データセット:** DocumentElement  
  
 **テーブル:** Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
 ただし、「document2"について、」推論プロセス生成、**データセット**"NewDataSet"と"DocumentElement"という名前のテーブルの名前。 この場合、属性も子要素も持たない "Element1" は列として推論されます。  
  
 **データセット:** NewDataSet  
  
 **テーブル:** DocumentElement  
  
|Element1|  
|--------------|  
|Text1|  
  
 これらの 2 つの XML ドキュメントは、同じスキーマを生成することを意図して記述されていますが、推論プロセスでは、各ドキュメントに含まれる要素を基にまったく異なるスキーマが生成されてしまいます。  
  
 XML ドキュメントからスキーマを生成するときに発生する不整合を避けるためには、お勧めの読み込み時に、XML スキーマ定義言語 (XSD) または Xml-data Reduced (XDR) を使用してスキーマを明示的に指定すること、**データセット**からXML です。 明示的に指定の詳細については、**データセット**スキーマと XML のスキーマを参照してください[派生 DataSet リレーショナル構造の XML スキーマ (XSD) から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)します。  
  
## <a name="see-also"></a>関連項目

- [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
