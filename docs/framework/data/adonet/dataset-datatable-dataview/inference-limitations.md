---
title: 推論の制限事項
ms.date: 03/30/2017
ms.assetid: 78517994-5d57-44f8-9d20-38812977de09
ms.openlocfilehash: 10347abc5b01edb4ec6fbf97221d44f4bfb88f54
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784581"
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
  
 "文書作成" の場合、"Element1" は繰り返し要素であるため、"DocumentElement" という名前の**データセット**と "Element1" という名前のテーブルが生成されます。  
  
 **セット**DocumentElement  
  
 **一覧**Element1  
  
|Element1_Text|  
|--------------------|  
|Text1|  
|Text2|  
  
 ただし、"文書セット" については、推論プロセスによって "NewDataSet" という名前の**データセット**と "documentelement" という名前のテーブルが生成されます。 この場合、属性も子要素も持たない "Element1" は列として推論されます。  
  
 **セット**NewDataSet  
  
 **一覧**DocumentElement  
  
|Element1|  
|--------------|  
|Text1|  
  
 これらの 2 つの XML ドキュメントは、同じスキーマを生成することを意図して記述されていますが、推論プロセスでは、各ドキュメントに含まれる要素を基にまったく異なるスキーマが生成されてしまいます。  
  
 Xml ドキュメントからスキーマを生成するときに発生する可能性がある不整合を回避するために、xml から**データセット**を読み込むときに、xml スキーマ定義言語 (XSD) または Xml データ削減 (XDR) を使用して、スキーマを明示的に指定することをお勧めします。 XML スキーマを使用して**データセット**スキーマを明示的に指定する方法の詳細については、「 [XML スキーマ (XSD) からの dataset リレーショナル構造の派生](deriving-dataset-relational-structure-from-xml-schema-xsd.md)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [XML からの DataSet リレーショナル構造の推論](inferring-dataset-relational-structure-from-xml.md)
- [XML からの DataSet の読み込み](loading-a-dataset-from-xml.md)
- [XML の DataSet スキーマ情報の読み込み](loading-dataset-schema-information-from-xml.md)
- [DataSet での XML の使用](using-xml-in-a-dataset.md)
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET の概要](../ado-net-overview.md)
