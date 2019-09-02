---
title: XSD としての DataSet スキーマ情報の書き込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: f9664d8e7bc221da68492140f30419ea8fb0d316
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70204366"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>XSD としての DataSet スキーマ情報の書き込み
<xref:System.Data.DataSet> のスキーマを XML スキーマ定義言語 (XSD) スキーマとして書き込むと、このスキーマを XML ドキュメントに転送できます。このとき関連データを含む定義、または関連データを含まない定義ができます。 XML スキーマは、ファイル、ストリーム、 <xref:System.Xml.XmlWriter>、または文字列に書き込むことができます。厳密に型指定された**データセット**を生成する場合に便利です。 厳密に型指定された**dataset**オブジェクトの詳細については、「[型付き dataset](typed-datasets.md)」を参照してください。  
  
 テーブルの列を XML スキーマで表す方法は、 <xref:System.Data.DataColumn>オブジェクトの**ColumnMapping**プロパティを使用して指定できます。 詳細については、「 [DataSet の内容を Xml データとして書き込む](writing-dataset-contents-as-xml-data.md)」の「xml 要素、属性、およびテキストへの列のマッピング」を参照してください。  
  
 **Dataset**のスキーマを XML スキーマとして、ファイル、ストリーム、または**XmlWriter**に書き込むには、**データセット**の**WriteXmlSchema**メソッドを使用します。 **WriteXmlSchema**は、結果の XML スキーマの出力先を指定するパラメーターを1つ受け取ります。 次のコード例では、ファイル名と<xref:System.IO.StreamWriter>オブジェクトを含む文字列を渡すことによって、**データセット**の XML スキーマをファイルに書き込む方法を示します。  
  
```vb  
dataSet.WriteXmlSchema("Customers.xsd")  
```  
  
```csharp  
dataSet.WriteXmlSchema("Customers.xsd");  
```  
  
```vb  
Dim writer As System.IO.StreamWriter = New System.IO.StreamWriter("Customers.xsd")  
dataSet.WriteXmlSchema(writer)  
writer.Close()  
```  
  
```csharp  
System.IO.StreamWriter writer = new System.IO.StreamWriter("Customers.xsd");  
dataSet.WriteXmlSchema(writer);  
writer.Close();  
```  
  
 **DataSet**のスキーマを取得し、XML スキーマ文字列として書き込むには、次の例に示すように、 **getxmlschema**メソッドを使用します。  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>関連項目

- [DataSet での XML の使用](using-xml-in-a-dataset.md)
- [DataSet 内容の XML データとしての書き込み](writing-dataset-contents-as-xml-data.md)
- [型指定されたデータセット](typed-datasets.md)
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
