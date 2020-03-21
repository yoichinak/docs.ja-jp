---
title: XML からの DataSet の読み込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: c21ed3bb31add285d64272040680433fff4e16fd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151066"
---
# <a name="loading-a-dataset-from-xml"></a>XML からの DataSet の読み込み
ADO.NET では、XML ストリームまたは XML ドキュメントから <xref:System.Data.DataSet> の内容を作成できます。 また、.NET Framework では、XML から読み込まれる情報と <xref:System.Data.DataSet> のスキーマまたはリレーショナル構造の作成方法を柔軟に変更できます。  
  
 XML の<xref:System.Data.DataSet>データを格納するには、オブジェクトの**ReadXml**メソッド<xref:System.Data.DataSet>を使用します。 **ReadXml**メソッドは、ファイル、ストリーム、または**XmlReader**から読み取り、XML のソースとオプションの**XmlReadMode**引数を引数として受け取ります。 **XmlReader**の詳細については、「 XML データを[XmlTextReader で読み込む](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100))」を参照してください。 **ReadXml**メソッドは、XML ストリームまたはドキュメントの内容を読み<xref:System.Data.DataSet>取り、データを読み込みます。 また、指定された**XmlReadMode** <xref:System.Data.DataSet>に応じて、リレーショナル スキーマが既に存在するかどうかによって、リレーショナル スキーマが作成されます。  
  
 次の表では、**引数のオプション**について説明します。  
  
|オプション|説明|  
|------------|-----------------|  
|**自動**|これは既定値です。 XML を調べ、次の順序で最適なオプションを選択します。<br /><br /> - XML が DiffGram の場合は **、DiffGram**が使用されます。<br />- スキーマ<xref:System.Data.DataSet>が含まれている場合、または XML にインライン スキーマが含まれている場合は **、ReadSchema**が使用されます。<br />- スキーマ<xref:System.Data.DataSet>が含まれておらず、XML にインライン スキーマが含まれていない場合は **、InferSchema が**使用されます。<br /><br /> 読み取り中の XML の形式がわかっている場合は、最適なパフォーマンスを得るため、**自動**既定値を受け入れるのではなく、明示的な**XmlReadMode**を設定することをお勧めします。|  
|**ReadSchema**|インライン スキーマを読み取り、データとスキーマを読み込みます。<br /><br /> <xref:System.Data.DataSet> に既にスキーマが含まれている場合には、読み取るインライン スキーマの新しいテーブルが <xref:System.Data.DataSet> の既存のスキーマに追加されます。 インライン スキーマのテーブルが既に <xref:System.Data.DataSet> に存在している場合には、例外がスローされます。 既存のテーブルのスキーマを変更**することはできません。**<br /><br /> <xref:System.Data.DataSet> にスキーマが含まれておらず、インライン スキーマが存在しない場合には、データは読み取られません。<br /><br /> インライン スキーマを定義するには、XML スキーマ定義言語 (XSD) スキーマを使用します。 XML スキーマとしてのインライン スキーマの作成の詳細については、「 [XML スキーマ (XSD) からのデータセット リレーショナル構造の派生](deriving-dataset-relational-structure-from-xml-schema-xsd.md)」を参照してください。|  
|**IgnoreSchema**|インライン スキーマを無視し、データを既存の <xref:System.Data.DataSet> スキーマへ読み込みます。 既存のスキーマに一致しないデータは破棄されます。 <xref:System.Data.DataSet> にスキーマがない場合には、データは読み込まれません。<br /><br /> データが DiffGram の場合 **、IgnoreSchema**は**DiffGram**と同じ機能を持ちます *。*|  
|**InferSchema**|インライン スキーマを無視し、XML データ構造ごとにスキーマを推論し、データを読み込みます。<br /><br /> <xref:System.Data.DataSet> に既にスキーマが含まれている場合、既存のテーブルに列を追加することによって現在のスキーマが拡張されます。 既存のテーブルが存在しない場合、余分なテーブルは追加されません。 推論されたテーブルが他の名前空間に既に存在している場合、または推論された列と既存の列が矛盾する場合には、例外がスローされます。<br /><br /> **ReadXmlSchema**が XML ドキュメントからスキーマを推論する方法の詳細については、「 [XML からのデータセット リレーショナル構造の推論](inferring-dataset-relational-structure-from-xml.md)」を参照してください。|  
|**Diffgram**|DiffGram を読み取り、現在のスキーマへデータを追加します。 **DiffGram は**、一意の識別子の値が一致する既存の行と新しい行をマージします。 このトピックの最後にある「XML のデータの結合」の説明を参照してください。 DiffGrams の詳細については[、「DiffGrams」](diffgrams.md)を参照してください。|  
|**フラグメント**|ストリームの終わりに達するまで、複数 XML フラグメントの読み取りを続行します。 <xref:System.Data.DataSet> スキーマに一致するフラグメントが適切なテーブルに追加されます。 <xref:System.Data.DataSet> スキーマに一致しないフラグメントは破棄されます。|  
  
> [!NOTE]
> Xml ドキュメントに配置された**XmlReader**を**ReadXml**に渡すと **、ReadXml**は次の要素ノードに読み込まれ、要素ノードの終わりまで読み取るルート要素として扱われます。 これは **、XmlReadMode.Fragment**を指定した場合には適用されません。  
  
## <a name="dtd-entities"></a>DTD エンティティ  
 XML にドキュメント型定義 (DTD) スキーマで定義されているエンティティが含まれている場合、ファイル名、ストリーム、または<xref:System.Data.DataSet>検証されていない**XmlReader**を**ReadXml**に渡してを読み込もうとすると、例外がスローされます。 代わりに、**エンティティ処理をエンティティ処理**.**展開エンティティ**に設定して**XmlValidatingReader**を作成し **、XmlValidatingReader**を**ReadXml**に渡す必要があります。 **によって読み**取られる前にエンティティを展開します。 <xref:System.Data.DataSet>  
  
 XML ストリームから <xref:System.Data.DataSet> を読み込むコード サンプルを次に示します。 最初の例は **、ReadXml**メソッドに渡されるファイル名を示しています。 2 番目の例では、XML が含まれている文字列が <xref:System.IO.StringReader> によって読み込まれます。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXml("input.xml", XmlReadMode.ReadSchema);  
```  
  
```vb  
Dim dataSet As DataSet = New DataSet  
Dim dataTable As DataTable = New DataTable("table1")  
dataTable.Columns.Add("col1", Type.GetType("System.String"))  
dataSet.Tables.Add(dataTable)  
  
Dim xmlData As String = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>"  
  
Dim xmlSR As System.IO.StringReader = New System.IO.StringReader(xmlData)  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema)  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
DataTable dataTable = new DataTable("table1");  
dataTable.Columns.Add("col1", typeof(string));  
dataSet.Tables.Add(dataTable);  
  
string xmlData = "<XmlDS><table1><col1>Value1</col1></table1><table1><col1>Value2</col1></table1></XmlDS>";  
  
System.IO.StringReader xmlSR = new System.IO.StringReader(xmlData);  
  
dataSet.ReadXml(xmlSR, XmlReadMode.IgnoreSchema);  
```  
  
> [!NOTE]
> **ReadXml**を呼び出して非常に大きなファイルを読み込むと、パフォーマンスが低下することがあります。 **ReadXml**のパフォーマンスを最大限に高めるには、 の大<xref:System.Data.DataTable.BeginLoadData%2A>きなファイルで、 の<xref:System.Data.DataSet>各テーブルのメソッドを呼び出し、 **ReadXml**を呼び出します。 最後に、次の例に示すように、<xref:System.Data.DataTable.EndLoadData%2A> のテーブルごとに <xref:System.Data.DataSet> を呼び出します。  
  
```vb  
Dim dataTable As DataTable  
  
For Each dataTable In dataSet.Tables  
   dataTable.BeginLoadData()  
Next  
  
dataSet.ReadXml("file.xml")  
  
For Each dataTable in dataSet.Tables  
   dataTable.EndLoadData()  
Next  
```  
  
```csharp  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.BeginLoadData();  
  
dataSet.ReadXml("file.xml");
  
foreach (DataTable dataTable in dataSet.Tables)  
   dataTable.EndLoadData();  
```  
  
> [!NOTE]
> の<xref:System.Data.DataSet>XSD スキーマに**targetNamespace**が含まれている場合、データが読み取られず、例外が**ReadXml**<xref:System.Data.DataSet>発生する可能性があります。 この場合、修飾されていない要素を読み取るために、XSD スキーマで**要素フォームの既定値**を "修飾" に設定します。 次に例を示します。  
  
```xml  
<xsd:schema id="customDataSet"
  elementFormDefault="qualified"  
  targetNamespace="http://www.tempuri.org/customDataSet.xsd"
  xmlns="http://www.tempuri.org/customDataSet.xsd"
  xmlns:xsd="http://www.w3.org/2001/XMLSchema"
  xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
</xsd:schema>  
```  
  
## <a name="merging-data-from-xml"></a>XML のデータの結合  
 既に、<xref:System.Data.DataSet> にデータが含まれている場合には、<xref:System.Data.DataSet> の既存のデータに XML の新しいデータが追加されます。 **ReadXml**は、XML から、一<xref:System.Data.DataSet>致する主キーを持つ行情報にマージしません。 既存の行情報を XML の新しい情報で上書きするには **、ReadXml** <xref:System.Data.DataSet.Merge%2A>を使用<xref:System.Data.DataSet>して 新<xref:System.Data.DataSet><xref:System.Data.DataSet>しい を作成し、次に新しい を既存の . **ReadXML**を使用して**DiffGram**を**XmlReadMode**読み込むと、同じ一意の識別子を持つ行がマージされることに注意してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [DataSet での XML の使用](using-xml-in-a-dataset.md)
- [DiffGrams](diffgrams.md)
- [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [XML からの DataSet リレーショナル構造の推論](inferring-dataset-relational-structure-from-xml.md)
- [XML の DataSet スキーマ情報の読み込み](loading-dataset-schema-information-from-xml.md)
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET の概要](../ado-net-overview.md)
