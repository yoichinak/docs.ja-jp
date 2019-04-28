---
title: XSD としての DataSet スキーマ情報の書き込み
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e530831-695e-49ff-8f0b-e5b0c526b8eb
ms.openlocfilehash: 8403f9d9be88f34e473fd3512f5499193245d227
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607050"
---
# <a name="writing-dataset-schema-information-as-xsd"></a>XSD としての DataSet スキーマ情報の書き込み
<xref:System.Data.DataSet> のスキーマを XML スキーマ定義言語 (XSD) スキーマとして書き込むと、このスキーマを XML ドキュメントに転送できます。このとき関連データを含む定義、または関連データを含まない定義ができます。 XML スキーマは、ファイル、ストリームに書き込むことが、 <xref:System.Xml.XmlWriter>、または文字列が厳密に型を生成するために役立ちます**データセット**します。 詳細については厳密に型指定**データセット**、オブジェクトを参照してください[型指定されたデータセット](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)します。  
  
 XML スキーマでテーブルの列を表現する方法を指定することができますを使用して、 **ColumnMapping**のプロパティ、<xref:System.Data.DataColumn>オブジェクト。 詳細については、「XML 要素属性、およびテキストを列の割り当て」を参照してください[書き込み DataSet の内容を XML データとして](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)します。  
  
 スキーマを記述する、**データセット**ファイルに、XML スキーマとしてストリーム、または**XmlWriter**を使用して、 **WriteXmlSchema**のメソッド、**データセット**します。 **WriteXmlSchema**結果の XML スキーマの変換先を指定する 1 つのパラメーターを受け取ります。 次のコード例の XML スキーマを記述する方法を示します、**データセット**ファイル ファイル名を含む文字列を渡すことによって、<xref:System.IO.StreamWriter>オブジェクト。  
  
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
  
 スキーマを取得する、**データセット**、XML スキーマ文字列として書き込むには、使用、 **GetXmlSchema**メソッドを次の例に示すようにします。  
  
```vb  
Dim schemaString As String = dataSet.GetXmlSchema()  
```  
  
```csharp  
string schemaString = dataSet.GetXmlSchema();  
```  
  
## <a name="see-also"></a>関連項目

- [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)
- [DataSet 内容の XML データとしての書き込み](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)
- [型指定されたデータセット](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/typed-datasets.md)
- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
