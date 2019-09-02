---
title: 列の推論
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 651d132fd76ba9015d4730a5e519bc679608e275
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203593"
---
# <a name="inferring-columns"></a>列の推論
ADO.NET は、<xref:System.Data.DataSet> のテーブルとして推論する要素を、XML ドキュメントから決定した後、それらのテーブルの列を推論します。 ADO.NET 2.0 では、 **simpleType**の各要素に対して厳密に型指定されたデータ型を推論する新しいスキーマ推論エンジンが導入されました。 以前のバージョンでは、推論された**simpleType**要素のデータ型は常に**xsd: string**でした。  
  
## <a name="migration-and-backward-compatibility"></a>移行および下位互換性  
 **ReadXml**メソッドは、 **InferSchema**型の引数を受け取ります。 この引数を使用することにより、以前のバージョンと互換性のある推論方法を指定することができます。 次の表に、 **InferSchema**列挙体で使用できる値を示します。  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 単純型を <xref:System.String> として常に推論することで下位互換性を提供します。  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 厳密に型指定されたデータ型を推論します。 <xref:System.Data.DataTable> で使用した場合、例外をスローします。  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 インライン スキーマを無視し、データを既存の <xref:System.Data.DataSet> スキーマに読み取ります。  
  
## <a name="attributes"></a>属性  
 「テーブルの[推論](inferring-tables.md)」で定義されているように、属性を持つ要素はテーブルとして推論されます。 その要素の属性は、そのテーブルの列として推論されます。 列の**ColumnMapping**プロパティは、スキーマが XML に書き戻される場合に列名が属性として書き込まれるように、 **Mappingtype. 属性**に設定されます。 属性の値は、テーブルの行に格納されます。 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 推論プロセスでは、 **attr1**と**attr2**という2つの列を持つ**Element1**という名前のテーブルが生成されます。 両方の列の**ColumnMapping**プロパティは、 **Mappingtype. Attribute**に設定されます。  
  
 **セット**DocumentElement  
  
 **一覧**Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>属性または子の要素を持たない要素  
 要素に子の要素または属性がない場合、その要素は列として推論されます。 列の**ColumnMapping**プロパティは、 **Mappingtype. 要素**に設定されます。 子の要素のテキストは、テーブルの行に格納されます。 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推論プロセスでは、 **ChildElement1**と**ChildElement2**という2つの列を持つ**Element1**という名前のテーブルが生成されます。 両方の列の**ColumnMapping**プロパティは、 **Mappingtype. Element**に設定されます。  
  
 **セット**DocumentElement  
  
 **一覧**Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Text2|  
  
## <a name="see-also"></a>関連項目

- [XML からの DataSet リレーショナル構造の推論](inferring-dataset-relational-structure-from-xml.md)
- [XML からの DataSet の読み込み](loading-a-dataset-from-xml.md)
- [XML の DataSet スキーマ情報の読み込み](loading-dataset-schema-information-from-xml.md)
- [DataSet での XML の使用](using-xml-in-a-dataset.md)
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
