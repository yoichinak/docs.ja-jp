---
title: XML の DataSet スキーマ情報の読み込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 06dcbbedf8c1533b3da52b447c121746ce705083
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785451"
---
# <a name="loading-dataset-schema-information-from-xml"></a>XML の DataSet スキーマ情報の読み込み
スキーマを<xref:System.Data.DataSet>(そのテーブル、列、リレーション、および制約) はプログラムによって作成された、**入力**または**FillSchema**のメソッド、<xref:System.Data.Common.DataAdapter>から読み込まれたまたは、XML ドキュメントです。 読み込めません**データセット**スキーマ情報を XML ドキュメントから、いずれかを使用できます、 **ReadXmlSchema**または**InferXmlSchema**のメソッド、**データセット**. **ReadXmlSchema**を使用すると、読み込みまたは推論**データセット**XML スキーマ定義言語 (XSD) スキーマ、またはインライン XML スキーマを持つ XML ドキュメントを含むドキュメントからスキーマ情報。 **InferXmlSchema**指定した特定の XML 名前空間を無視しているときに、XML ドキュメントからスキーマを推論することができます。  
  
> [!NOTE]
>  テーブルの順序で、**データセット**を転送する Web サービスまたは XML シリアル化を使用する場合は保持されませんが、**データセット**インメモリ (入れ子になったリレーション) などの XSD コンス トラクターを使用して作成されました。 そのための受信者、**データセット**ここでのテーブルの順序に依存しないようにします。 ただし、テーブルの順序は常に保持される場合のスキーマ、**データセット**メモリ内に作成されているのではなく、XSD ファイルから読み取られた転送されています。  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 スキーマを読み込む、**データセット**任意のデータを読み込むことがなく、XML ドキュメントから使用することができます、 **ReadXmlSchema**のメソッド、**データセット**します。 **ReadXmlSchema**作成**データセット**XML スキーマ定義言語 (XSD) スキーマを使用して定義されているスキーマ。  
  
 **ReadXmlSchema**メソッドは、ストリーム、ファイル名の 1 つの引数または**XmlReader**読み込む XML ドキュメントを格納しています。 この XML ドキュメントには、スキーマだけが含まれているか、またはデータのある XML 要素と共にスキーマがインラインで含まれています。 XML スキーマとしてのインライン スキーマを書き込む方法の詳細については、次を参照してください。[派生 DataSet リレーショナル構造の XML スキーマ (XSD) から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)します。  
  
 XML ドキュメントが渡された場合**ReadXmlSchema**インライン スキーマの情報が含まれていない**ReadXmlSchema**は XML ドキュメント内の要素からスキーマを推論します。 場合、**データセット**既にスキーマを含む現在のスキーマがまだ存在しない場合は、新しいテーブルを追加することによって拡張されます。 既存のテーブルには新しい列は追加されません。 既に追加されている列が存在する場合、**データセット**が互換性のない型の列が見つかりません、XML で例外がスローされます。 方法の詳細について**ReadXmlSchema**スキーマの推論、XML ドキュメントから、次を参照してください。[への推論からの DataSet リレーショナル構造 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)します。  
  
 **ReadXmlSchema**読み込みまたは推論のスキーマのみ、**データセット**、 **ReadXml**のメソッド、**データセット**読み込まれるかまたは両方の推論スキーマと XML ドキュメントに含まれるデータ。 詳細については、次を参照してください。 [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)します。  
  
 次のコード例を読み込む方法を表示する、**データセット**を XML ドキュメントまたはストリームからのスキーマ。 最初の例に渡される XML スキーマ ファイル名、 **ReadXmlSchema**メソッド。 2 番目の例を示します、 **System.IO.StreamReader**します。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As System.IO.StreamReader = New System.IO.StreamReader ("schema.xsd");  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema(xmlStream)  
xmlStream.Close()  
```  
  
```csharp  
System.IO.StreamReader xmlStream = new System.IO.StreamReader("schema.xsd");  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema(xmlStream);  
xmlStream.Close();  
```  
  
## <a name="inferxmlschema"></a>InferXmlSchema  
 指示することも、**データセット**による XML ドキュメントからスキーマを推論する、 **InferXmlSchema**のメソッド、**データセット**します。 **InferXmlSchema**両方を行うと、同じように機能**ReadXml**で、 **XmlReadMode**の**InferSchema** (データを読み込むし、スキーマを推論)、および**ReadXmlSchema**読み取られるドキュメントにインライン スキーマが含まれていない場合。 ただし、 **InferXmlSchema**スキーマを推論するときに無視する特定の XML 名前空間を指定できる追加機能を提供します。 **InferXmlSchema**は 2 つの必須引数を受け取ります。 ファイル名、ストリーム、で指定された、XML ドキュメントの場所または**XmlReader**; と操作によって無視される XML 名前空間の文字列配列。  
  
 たとえば、次のような XML があるとします。  
  
```xml  
<NewDataSet xmlns:od="urn:schemas-microsoft-com:officedata">  
<Categories>  
  <CategoryID od:adotype="3">1</CategoryID>   
  <CategoryName od:maxLength="15" od:adotype="130">Beverages</CategoryName>   
  <Description od:adotype="203">Soft drinks and teas</Description>   
</Categories>  
<Products>  
  <ProductID od:adotype="20">1</ProductID>   
  <ReorderLevel od:adotype="3">10</ReorderLevel>   
  <Discontinued od:adotype="11">0</Discontinued>   
</Products>  
</NewDataSet>  
```  
  
 上記の XML ドキュメント内の要素に指定された属性のため両方、 **ReadXmlSchema**メソッドと**ReadXml**メソッドを**XmlReadMode**の**InferSchema**テーブルのすべての要素のドキュメントを作成します。**カテゴリ**、 **CategoryID**、 **CategoryName**、**説明**、**製品**、 **ProductID**、 **ReorderLevel**、および**廃止**します。 (詳細については、次を参照してください[推論 DataSet リレーショナル構造の XML から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)。)ただしより適切な構造は、のみを作成すると、**カテゴリ**と**製品**テーブルを作成し、 **CategoryID**、 **CategoryName**、および**説明**内の列、**カテゴリ**テーブル、および**ProductID**、 **ReorderLevel**と**Discontinued**内の列、**製品**テーブル。 推論されたスキーマが XML 要素で指定された属性を無視することを確認するを使用して、 **InferXmlSchema**メソッドの XML 名前空間を指定して**officedata**が無視されるように、次の例です。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>関連項目

- [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [XML からの DataSet の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)
- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
