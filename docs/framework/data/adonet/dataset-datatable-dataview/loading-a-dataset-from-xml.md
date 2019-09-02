---
title: XML からの DataSet の読み込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 77f25e1c52f10a1724bf81a3fa533739e15085c4
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204712"
---
# <a name="loading-a-dataset-from-xml"></a>XML からの DataSet の読み込み
ADO.NET では、XML ストリームまたは XML ドキュメントから <xref:System.Data.DataSet> の内容を作成できます。 また、.NET Framework では、XML から読み込まれる情報と <xref:System.Data.DataSet> のスキーマまたはリレーショナル構造の作成方法を柔軟に変更できます。  
  
 に XML の<xref:System.Data.DataSet>データを格納するには、 <xref:System.Data.DataSet>オブジェクトの ReadXml メソッドを使用します。 **ReadXml**メソッドは、ファイル、ストリーム、または**XmlReader**から読み取り、XML のソースと省略可能な**XmlReadMode**引数を引数として受け取ります。 **XmlReader**の詳細については、「 [XmlTextReader を使用した XML データの読み取り](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100))」を参照してください。 **ReadXml**メソッドは、XML ストリームまたはドキュメントの内容を読み取り、データ<xref:System.Data.DataSet>を使用してを読み込みます。 また、指定された**XmlReadMode**と、 <xref:System.Data.DataSet>リレーショナルスキーマが既に存在するかどうかに応じて、のリレーショナルスキーマも作成されます。  
  
 次の表では、 **XmlReadMode**引数のオプションについて説明します。  
  
|オプション|説明|  
|------------|-----------------|  
|**Auto**|既定値です。 XML を調べ、次の順序で最適なオプションを選択します。<br /><br /> -XML が DiffGram の場合は、 **diffgram**が使用されます。<br />-に<xref:System.Data.DataSet>スキーマが含まれている場合、または XML にインラインスキーマが含まれている場合は、 **readschema**が使用されます。<br />-に<xref:System.Data.DataSet>スキーマが含まれておらず、XML にインラインスキーマが含まれていない場合は、 **InferSchema**が使用されます。<br /><br /> 読み取り中の XML の形式がわかっている場合は、最適なパフォーマンスを得るために、**自動**既定値をそのまま使用するのではなく、明示的な**XmlReadMode**を設定することをお勧めします。|  
|**ReadSchema**|インライン スキーマを読み取り、データとスキーマを読み込みます。<br /><br /> <xref:System.Data.DataSet> に既にスキーマが含まれている場合には、読み取るインライン スキーマの新しいテーブルが <xref:System.Data.DataSet> の既存のスキーマに追加されます。 インライン スキーマのテーブルが既に <xref:System.Data.DataSet> に存在している場合には、例外がスローされます。 **XmlReadMode**を使用して、既存のテーブルのスキーマを変更することはできません。<br /><br /> <xref:System.Data.DataSet> にスキーマが含まれておらず、インライン スキーマが存在しない場合には、データは読み取られません。<br /><br /> インライン スキーマを定義するには、XML スキーマ定義言語 (XSD) スキーマを使用します。 インラインスキーマを XML スキーマとして記述する方法の詳細については、「 [Xml スキーマ (XSD) からの DataSet リレーショナル構造の派生](deriving-dataset-relational-structure-from-xml-schema-xsd.md)」を参照してください。|  
|**IgnoreSchema**|インライン スキーマを無視し、データを既存の <xref:System.Data.DataSet> スキーマへ読み込みます。 既存のスキーマに一致しないデータは破棄されます。 <xref:System.Data.DataSet> にスキーマがない場合には、データは読み込まれません。<br /><br /> データが DiffGram の場合、 **IgnoreSchema**には**diffgram**と同じ機能があり*ます。*|  
|**InferSchema**|インライン スキーマを無視し、XML データ構造ごとにスキーマを推論し、データを読み込みます。<br /><br /> <xref:System.Data.DataSet> に既にスキーマが含まれている場合、既存のテーブルに列を追加することによって現在のスキーマが拡張されます。 既存のテーブルが存在しない場合、余分なテーブルは追加されません。 推論されたテーブルが他の名前空間に既に存在している場合、または推論された列と既存の列が矛盾する場合には、例外がスローされます。<br /><br /> **Readxmlschema**が xml ドキュメントからスキーマを推論する方法の詳細については、「 [Xml からの DataSet リレーショナル構造の推論](inferring-dataset-relational-structure-from-xml.md)」を参照してください。|  
|**DiffGram**|DiffGram を読み取り、現在のスキーマへデータを追加します。 **DiffGram**では、一意の識別子の値が一致する既存の行と新しい行がマージされます。 このトピックの最後にある「XML のデータの結合」の説明を参照してください。 Diffgram の詳細については、「 [Diffgram グラム](diffgrams.md)」を参照してください。|  
|**抜粋**|ストリームの終わりに達するまで、複数 XML フラグメントの読み取りを続行します。 <xref:System.Data.DataSet> スキーマに一致するフラグメントが適切なテーブルに追加されます。 <xref:System.Data.DataSet> スキーマに一致しないフラグメントは破棄されます。|  
  
> [!NOTE]
> XML ドキュメントに配置されている**readxml**に**XmlReader**を渡すと、 **readxml**は次の要素ノードを読み取り、それをルート要素として扱い、要素ノードの最後まで読み取ります。 **XmlReadMode**を指定した場合、この設定は適用されません。  
  
## <a name="dtd-entities"></a>DTD エンティティ  
 XML にドキュメント型定義 (DTD) スキーマで定義されているエンティティが含まれている場合、ファイル名、ストリーム<xref:System.Data.DataSet> 、または非検証**XmlReader**を**ReadXml**に渡すことによってを読み込もうとすると、例外がスローされます。 代わりに、 **Entityhandling**を**Entityhandling. expandentities**に設定して、 **XmlValidatingReader**を**ReadXml**に渡す必要があります。 **XmlValidatingReader**は、 <xref:System.Data.DataSet>によって読み取られる前にエンティティを拡張します。  
  
 XML ストリームから <xref:System.Data.DataSet> を読み込むコード サンプルを次に示します。 最初の例は、 **ReadXml**メソッドに渡されるファイル名を示しています。 2 番目の例では、XML が含まれている文字列が <xref:System.IO.StringReader> によって読み込まれます。  
  
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
> **ReadXml**を呼び出して非常に大きなファイルを読み込むと、パフォーマンスが低下する可能性があります。 **Readxml**で最適なパフォーマンスを得るには、大きなファイルで、 <xref:System.Data.DataTable.BeginLoadData%2A>の<xref:System.Data.DataSet>各テーブルに対してメソッドを呼び出し、 **readxml**を呼び出します。 最後に、次の例に示すように、<xref:System.Data.DataTable.EndLoadData%2A> のテーブルごとに <xref:System.Data.DataSet> を呼び出します。  
  
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
> の<xref:System.Data.DataSet> XSD スキーマに**targetNamespace**が含まれている場合は、 **ReadXml**を呼び出して、 <xref:System.Data.DataSet>修飾された名前空間を持たない要素を含む XML を読み込むと、データが読み取られず、例外が発生する可能性があります。 この場合、修飾されていない要素を読み取るには、XSD スキーマで**elementFormDefault**を "qualified" に設定します。 例:  
  
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
 既に、<xref:System.Data.DataSet> にデータが含まれている場合には、<xref:System.Data.DataSet> の既存のデータに XML の新しいデータが追加されます。 **ReadXml**では、XML から、一致する<xref:System.Data.DataSet>主キーを持つ行情報にはマージされません。 既存の行情報を XML の新しい情報で上書きするには、 **ReadXml**を<xref:System.Data.DataSet>使用して<xref:System.Data.DataSet.Merge%2A>新しいを作成した<xref:System.Data.DataSet>後、 <xref:System.Data.DataSet>既存のに新しいを作成します。 **XmlReadMode**が**diffgram**の**ReadXML**を使用して diffgram を読み込むと、同じ一意の識別子を持つ行がマージされることに注意してください。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [DataSet での XML の使用](using-xml-in-a-dataset.md)
- [DiffGrams](diffgrams.md)
- [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [XML からの DataSet リレーショナル構造の推論](inferring-dataset-relational-structure-from-xml.md)
- [XML の DataSet スキーマ情報の読み込み](loading-dataset-schema-information-from-xml.md)
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
