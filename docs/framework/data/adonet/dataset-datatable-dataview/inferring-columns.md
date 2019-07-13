---
title: 列の推論
ms.date: 03/30/2017
ms.assetid: 0e022699-c922-454c-93e2-957dd7e7247a
ms.openlocfilehash: 53e77f624c5af8f61a32d5b1399d2728f32011a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62034282"
---
# <a name="inferring-columns"></a>列の推論
ADO.NET は、<xref:System.Data.DataSet> のテーブルとして推論する要素を、XML ドキュメントから決定した後、それらのテーブルの列を推論します。 ADO.NET 2.0 にはそれぞれの厳密に型指定されたデータ型を推論する新しいスキーマ推論エンジンが導入された**simpleType**要素。 以前のバージョンで、データ型の推論される**simpleType**要素が常に**xsd:string**します。  
  
## <a name="migration-and-backward-compatibility"></a>移行および下位互換性  
 **ReadXml**メソッドは、型の引数を受け取る**InferSchema**します。 この引数を使用することにより、以前のバージョンと互換性のある推論方法を指定することができます。 使用できる値、 **InferSchema**列挙体は、次の表に表示されます。  
  
 <xref:System.Data.XmlReadMode.InferSchema>  
 単純型を <xref:System.String> として常に推論することで下位互換性を提供します。  
  
 <xref:System.Data.XmlReadMode.InferTypedSchema>  
 厳密に型指定されたデータ型を推論します。 <xref:System.Data.DataTable> で使用した場合、例外をスローします。  
  
 <xref:System.Data.XmlReadMode.IgnoreSchema>  
 インライン スキーマを無視し、データを既存の <xref:System.Data.DataSet> スキーマに読み取ります。  
  
## <a name="attributes"></a>属性  
 定義されている[テーブルの推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-tables.md)属性を持つ要素はテーブルとして推論されます。 その要素の属性は、そのテーブルの列として推論されます。 **ColumnMapping**列のプロパティに設定する**MappingType.Attribute**スキーマが XML に書き戻す場合に列名の属性として記述することを確認するためです。 属性の値は、テーブルの行に格納されます。 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1 attr1="value1" attr2="value2"/>  
</DocumentElement>  
```  
  
 推論プロセスという名前のテーブルが生成されます**Element1** 、2 つの列を持つ**attr1**と**attr2**します。 **ColumnMapping**両方の列のプロパティに設定する**MappingType.Attribute**します。  
  
 **データセット:** DocumentElement  
  
 **テーブル:** Element1  
  
|attr1|attr2|  
|-----------|-----------|  
|value1|value2|  
  
## <a name="elements-without-attributes-or-child-elements"></a>属性または子の要素を持たない要素  
 要素に子の要素または属性がない場合、その要素は列として推論されます。 **ColumnMapping**列のプロパティに設定する**MappingType.Element**します。 子の要素のテキストは、テーブルの行に格納されます。 たとえば、次のような XML があるとします。  
  
```xml  
<DocumentElement>  
  <Element1>  
    <ChildElement1>Text1</ChildElement1>  
    <ChildElement2>Text2</ChildElement2>  
  </Element1>  
</DocumentElement>  
```  
  
 推論プロセスという名前のテーブルが生成されます**Element1** 、2 つの列を持つ**ChildElement1**と**ChildElement2**します。 **ColumnMapping**両方の列のプロパティに設定する**MappingType.Element**します。  
  
 **データセット:** DocumentElement  
  
 **テーブル:** Element1  
  
|ChildElement1|ChildElement2|  
|-------------------|-------------------|  
|Text1|Text2|  
  
## <a name="see-also"></a>関連項目

- [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
