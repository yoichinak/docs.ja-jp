---
title: XML の DataSet スキーマ情報の読み込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 43dfb23b-5cef-46f2-8d87-78f0fba1eb8c
ms.openlocfilehash: 69994c546fea842ffef1c8c43d6d6f5bc35e0629
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151053"
---
# <a name="loading-dataset-schema-information-from-xml"></a>XML の DataSet スキーマ情報の読み込み
の<xref:System.Data.DataSet>スキーマ (テーブル、列、リレーション、および制約) は、プログラムで定義するか<xref:System.Data.Common.DataAdapter>、または**の Fill**メソッドまたは**FillSchema**メソッドによって作成するか、XML ドキュメントから読み込むことができます。 XML ドキュメントから**データセット**スキーマ情報を読み込むには、データセットの**ReadXml スキーマ**または**メソッド****を使用**できます。 **ReadXmlSchema**を使用すると、XML スキーマ定義言語 (XSD) スキーマを含むドキュメント、またはインライン XML スキーマを持つ XML ドキュメントから**DataSet**スキーマ情報を読み込んだり、推論したりできます。 **InferXmlSchema**を使用すると、指定した特定の XML 名前空間を無視しながら、XML ドキュメントからスキーマを推論できます。  
  
> [!NOTE]
> Web サービスまたは XML シリアル化を使用して、XSD 構成要素 (入れ子になった関係など) を使用してメモリ内で作成された**DataSet**を転送する場合 **、DataSet**内のテーブルの順序が保持されない場合があります。 したがって **、DataSet**の受信者は、この場合、テーブルの順序に依存しないでください。 ただし、転送される**DataSet**のスキーマが XSD ファイルから読み取られた場合、テーブルの順序は常に保持されます。  
  
## <a name="readxmlschema"></a>ReadXmlSchema  
 データを読み込まずに XML ドキュメントから**データセット**のスキーマを読み込むには、 **DataSet**の**ReadXmlSchema**メソッドを使用できます。 **XML スキーマ定義**言語 (XSD) スキーマを使用して定義された**データセット**スキーマを作成します。  
  
 **ReadXmlSchema**メソッドは、読み込まれる XML ドキュメントを含むファイル名、ストリーム、または**XmlReader**の引数を 1 つ受け取ります。 この XML ドキュメントには、スキーマだけが含まれているか、またはデータのある XML 要素と共にスキーマがインラインで含まれています。 XML スキーマとしてのインライン スキーマの作成の詳細については、「 [XML スキーマ (XSD) からのデータセット リレーショナル構造の派生](deriving-dataset-relational-structure-from-xml-schema-xsd.md)」を参照してください。  
  
 **ReadXmlSchema**に渡された XML ドキュメントにインライン スキーマ情報が含まれている場合 **、Xml**ドキュメント内の要素からスキーマが推論されます。 **DataSet**にスキーマが既に含まれている場合、現在のスキーマは、存在しない場合は新しいテーブルを追加して拡張されます。 既存のテーブルには新しい列は追加されません。 追加される列が**DataSet**に既に存在するが、XML 内で見つかった列と互換性のない型を持つ場合は、例外がスローされます。 **ReadXmlSchema**が XML ドキュメントからスキーマを推論する方法の詳細については、「 [XML からのデータセット リレーショナル構造の推論](inferring-dataset-relational-structure-from-xml.md)」を参照してください。  
  
 **読み**込むか、**データセット**のスキーマのみを推論するが、**データセット**の**ReadXml**メソッドは、スキーマと XML ドキュメントに含まれるデータの両方を読み込むか推論します。 詳細については、「 [XML からのデータセットの読み込み](loading-a-dataset-from-xml.md)」を参照してください。  
  
 次のコード例は、XML ドキュメントまたはストリームから**DataSet**スキーマを読み込む方法を示しています。 最初の例では、**メソッド**に渡される XML スキーマ ファイル名を示します。 2 番目の例は **、System.IO.StreamReader**を示しています。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.ReadXmlSchema("schema.xsd")  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.ReadXmlSchema("schema.xsd");  
```  
  
```vb  
Dim xmlStream As New System.IO.StreamReader("schema.xsd")
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
 また、**データセット**のメソッドを使用して、XML ドキュメントから**スキーマを推論**するように**DataSet に**指示することもできます。 **InferXmlSchema 関数**は、読み取り対象のドキュメントにインライン**スキーマ****ReadXmlSchema**が含まれていなくても **、ReadXml**と同じです。 **XmlReadMode** ただし **、InferXmlSchema**には、スキーマが推論されるときに無視する特定の XML 名前空間を指定できる追加機能が用意されています。 **InferXmlSchema は**、ファイル名、ストリーム、または**XmlReader**で指定された XML ドキュメントの場所という 2 つの必須引数を受け取ります。XML 名前空間の文字列配列を操作によって無視します。  
  
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
  
 前の XML ドキュメントの要素に指定された属性のため **、ReadXmlSchema**メソッドと**ProductID****InferSchema**の**CategoryName****XmlReadMode**を持つ**ReadXml**メソッドの両方**が、ドキュメント**内のすべての要素**CategoryID**に対してテーブルを作成**Description****します**。 **Products** **Discontinued** (詳細については[、「XML からのデータセットリレーショナル構造の推論](inferring-dataset-relational-structure-from-xml.md)」を参照してください。ただし、より適切な構造としては、[**商品] テーブル**と [**商品**] テーブルのみを作成し、[商品] テーブルに **[カテゴリ** **ID]、[****カテゴリ名**]、および **[説明**] 列、および **[商品**] テーブルの [**商品]** 列 、[**受注レベル]** 列、[中止 **]** 列を作成します。 推論されたスキーマが XML 要素で指定された属性を確実に無視するようにするには、次の例に示すように **、InferXmlSchema**メソッドを使用して、無視する**office データ**の XML 名前空間を指定します。  
  
```vb  
Dim dataSet As DataSet = New DataSet  
dataSet.InferXmlSchema("input_od.xml", New String() {"urn:schemas-microsoft-com:officedata"})  
```  
  
```csharp  
DataSet dataSet = new DataSet();  
dataSet.InferXmlSchema("input_od.xml", new string[] "urn:schemas-microsoft-com:officedata");  
```  
  
## <a name="see-also"></a>関連項目

- [DataSet での XML の使用](using-xml-in-a-dataset.md)
- [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [XML からの DataSet リレーショナル構造の推論](inferring-dataset-relational-structure-from-xml.md)
- [XML からの DataSet の読み込み](loading-a-dataset-from-xml.md)
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET の概要](../ado-net-overview.md)
