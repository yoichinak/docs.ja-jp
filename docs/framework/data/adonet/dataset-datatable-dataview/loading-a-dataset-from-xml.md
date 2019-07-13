---
title: XML からの DataSet の読み込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 49c083b7-a5ed-41cf-aabc-5aaba96f00e6
ms.openlocfilehash: 0c53e3a15bcbe61db7da1edb31ecd3fd562603f5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785464"
---
# <a name="loading-a-dataset-from-xml"></a>XML からの DataSet の読み込み
ADO.NET では、XML ストリームまたは XML ドキュメントから <xref:System.Data.DataSet> の内容を作成できます。 また、.NET Framework では、XML から読み込まれる情報と <xref:System.Data.DataSet> のスキーマまたはリレーショナル構造の作成方法を柔軟に変更できます。  
  
 入力する、 <xref:System.Data.DataSet> 、XML からデータを使用して、 **ReadXml**のメソッド、<xref:System.Data.DataSet>オブジェクト。 **ReadXml**メソッドは、ファイル、ストリームから読み取りますまたは**XmlReader**、XML と省略可能なソースを引数として受け取ります**XmlReadMode**引数。 詳細については、 **XmlReader**を参照してください[XmlTextReader による XML データの読み取り](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tfz3cz6w(v=vs.100))します。 **ReadXml**メソッドは、XML ストリームまたはドキュメントと負荷の内容を読み取り、<xref:System.Data.DataSet>データ。 リレーショナル スキーマは作成も、<xref:System.Data.DataSet>に応じて、 **XmlReadMode**指定し、リレーショナル スキーマが既に存在するかどうか。  
  
 次の表のオプション、 **XmlReadMode**引数。  
  
|オプション|説明|  
|------------|-----------------|  
|**Auto**|既定値です。 XML を調べ、次の順序で最適なオプションを選択します。<br /><br /> 場合、XML が DiffGram、 **DiffGram**使用されます。<br />If、<xref:System.Data.DataSet>スキーマを含むまたは XML にインライン スキーマが含まれている**ReadSchema**使用されます。<br />If、<xref:System.Data.DataSet>スキーマが含まれていない XML にインライン スキーマが含まれていない**InferSchema**使用されます。<br /><br /> 読み取られる XML の形式がわかっている場合最適なパフォーマンスは勧めを明示的に設定すること**XmlReadMode**ではなく、そのまま使用よりも、**自動**既定。|  
|**ReadSchema**|インライン スキーマを読み取り、データとスキーマを読み込みます。<br /><br /> <xref:System.Data.DataSet> に既にスキーマが含まれている場合には、読み取るインライン スキーマの新しいテーブルが <xref:System.Data.DataSet> の既存のスキーマに追加されます。 インライン スキーマのテーブルが既に <xref:System.Data.DataSet> に存在している場合には、例外がスローされます。 使用して既存のテーブルのスキーマを変更することはできません**XmlReadMode.ReadSchema**します。<br /><br /> <xref:System.Data.DataSet> にスキーマが含まれておらず、インライン スキーマが存在しない場合には、データは読み取られません。<br /><br /> インライン スキーマを定義するには、XML スキーマ定義言語 (XSD) スキーマを使用します。 XML スキーマとしてのインライン スキーマを書き込む方法の詳細については、次を参照してください。[派生 DataSet リレーショナル構造の XML スキーマ (XSD) から](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)します。|  
|**IgnoreSchema**|インライン スキーマを無視し、データを既存の <xref:System.Data.DataSet> スキーマへ読み込みます。 既存のスキーマに一致しないデータは破棄されます。 <xref:System.Data.DataSet> にスキーマがない場合には、データは読み込まれません。<br /><br /> 場合は、データが DiffGram、 **IgnoreSchema**と同じ機能を持つ**DiffGram** *します。*|  
|**InferSchema**|インライン スキーマを無視し、XML データ構造ごとにスキーマを推論し、データを読み込みます。<br /><br /> <xref:System.Data.DataSet> に既にスキーマが含まれている場合、既存のテーブルに列を追加することによって現在のスキーマが拡張されます。 既存のテーブルが存在しない場合、余分なテーブルは追加されません。 推論されたテーブルが他の名前空間に既に存在している場合、または推論された列と既存の列が矛盾する場合には、例外がスローされます。<br /><br /> 方法の詳細について**ReadXmlSchema**スキーマの推論、XML ドキュメントから、次を参照してください。[への推論からの DataSet リレーショナル構造 XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)します。|  
|**DiffGram**|DiffGram を読み取り、現在のスキーマへデータを追加します。 **DiffGram**一意識別子値が一致する既存の行を含む新しい行をマージします。 このトピックの最後にある「XML のデータの結合」の説明を参照してください。 Diffgram の詳細については、次を参照してください。 [Diffgram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)します。|  
|**フラグメント**|ストリームの終わりに達するまで、複数 XML フラグメントの読み取りを続行します。 <xref:System.Data.DataSet> スキーマに一致するフラグメントが適切なテーブルに追加されます。 <xref:System.Data.DataSet> スキーマに一致しないフラグメントは破棄されます。|  
  
> [!NOTE]
>  渡す場合、 **XmlReader**に**ReadXml** 、XML ドキュメントに配置されている一部である**ReadXml**は次の要素ノードに読み取りし、ルートとして扱うことこの要素では、要素ノードのみが終わるまで読み取り。 指定した場合は当てはまりません**XmlReadMode.Fragment**します。  
  
## <a name="dtd-entities"></a>DTD エンティティ  
 読み込もうとした場合、例外がスローされます、XML にドキュメント型定義 (DTD) スキーマで定義されたエンティティが含まれている場合、<xref:System.Data.DataSet>ファイルを渡すことによって名、ストリーム、または非検証**XmlReader**に**ReadXml**します。 代わりに、作成する必要があります、 **XmlValidatingReader**で**EntityHandling**に設定**EntityHandling.ExpandEntities**を渡すと、 **XmlValidatingReader**に**ReadXml**します。 **XmlValidatingReader**によって読み取られる前にエンティティを拡張し、<xref:System.Data.DataSet>します。  
  
 XML ストリームから <xref:System.Data.DataSet> を読み込むコード サンプルを次に示します。 最初の例に渡されたファイル名、 **ReadXml**メソッド。 2 番目の例では、XML が含まれている文字列が <xref:System.IO.StringReader> によって読み込まれます。  
  
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
>  呼び出す場合**ReadXml**非常に大きなファイルを読み込むには、パフォーマンスの低下が発生する可能性があります。 最適なパフォーマンスを確保する**ReadXml**、大きなファイルの場合は、呼び出し、<xref:System.Data.DataTable.BeginLoadData%2A>メソッド内の各テーブルに対して、<xref:System.Data.DataSet>を呼び出して**ReadXml**します。 最後に、次の例に示すように、<xref:System.Data.DataTable.EndLoadData%2A> のテーブルごとに <xref:System.Data.DataSet> を呼び出します。  
  
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
>  場合の XSD スキーマ、<xref:System.Data.DataSet>が含まれています、 **targetNamespace**データが読み取られず、呼び出し時に、例外が発生する可能性があります**ReadXml**を読み込む、<xref:System.Data.DataSet>を含む xml修飾名前空間のない要素。 この場合、修飾されていない要素を読み取り、次のように設定します。 **elementFormDefault**を"qualified"に XSD スキーマ内のと同じです。 例:  
  
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
 既に、<xref:System.Data.DataSet> にデータが含まれている場合には、<xref:System.Data.DataSet> の既存のデータに XML の新しいデータが追加されます。 **ReadXml**に XML からマージされない、<xref:System.Data.DataSet>行の主キーが一致する情報。 XML から新しい情報で既存の行情報を上書きするには使用**ReadXml**新たに作成する<xref:System.Data.DataSet>、し<xref:System.Data.DataSet.Merge%2A>新しい<xref:System.Data.DataSet>既存<xref:System.Data.DataSet>します。 使用して DiffGram を読み込む**ReadXML**で、 **XmlReadMode**の**DiffGram**を同じ一意の識別子を持つ行が結合されます。  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataSet.Merge%2A?displayProperty=nameWithType>
- [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DiffGrams](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)
- [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [XML からの DataSet リレーショナル構造の推論](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/inferring-dataset-relational-structure-from-xml.md)
- [XML の DataSet スキーマ情報の読み込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-dataset-schema-information-from-xml.md)
- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
