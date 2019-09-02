---
title: 厳密に型指定された DataSet の生成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 54333cbf-bb43-4314-a7d4-6dc1dd1c44b3
ms.openlocfilehash: 9bff69e28aa17da87da7e94d4e110c0375f043ae
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203706"
---
# <a name="generating-strongly-typed-datasets"></a>厳密に型指定された DataSet の生成
Xml スキーマ定義言語 (xsd) 標準に準拠した xml スキーマを使用すると、Windows ソフトウェア開発キット<xref:System.Data.DataSet> (SDK) に付属している xsd.exe ツールを使用して、厳密に型指定されたを生成できます。  
  
 (データベーステーブルから xsd を作成するには<xref:System.Data.DataSet.WriteXmlSchema%2A> 、「」または「 [Visual Studio でのデータセットの操作](/visualstudio/data-tools/dataset-tools-in-visual-studio)」を参照してください)。  
  
 次のコードは、このツールを使用して**データセット**を生成するための構文を示しています。  
  
```  
xsd.exe /d /l:CS XSDSchemaFileName.xsd /eld /n:XSDSchema.Namespace  
```  
  
 この構文では、 `/d`ディレクティブは**データセット**を生成するようにツールに`/l:`指示し、は、使用する言語 (たとえば、 C#または Visual Basic .net) をツールに指示します。 省略可能`/eld`なディレクティブは、LINQ to DataSet を使用して、生成されたデータセットに対してクエリを実行できることを指定し**ます。** このオプションは、`/d` オプションと組み合わせて指定します。 詳細については、「[型指定](../querying-typed-datasets.md)された Dataset のクエリ」を参照してください。 省略可能`/n:`なディレクティブは、 **xsdschema**という名前の**データセット**の名前空間も生成するようにツールに指示します。 コマンドの出力は XSDSchemaFileName.cs で、ADO.NET アプリケーションでコンパイルおよび使用できます。 生成されたコードをライブラリまたはモジュールとしてコンパイルできます。  
  
 C# コンパイラ (csc.exe) を使用して、生成されたコードをライブラリとしてコンパイルする構文を次のコードで示します。  
  
```  
csc.exe /t:library XSDSchemaFileName.cs /r:System.dll /r:System.Data.dll  
```  
  
 `/t:` ディレクティブはライブラリとしてコンパイルすることをツールに知らせ、`/r:` ディレクティブはコンパイルに必要な依存ライブラリを指定します。 コマンドの出力は XSDSchemaFileName.dll で、`/r:` ディレクティブによる ADO.NET アプリケーションのコンパイル時にコンパイラに渡すことができます。  
  
 ADO.NET アプリケーションの XSD.exe に渡された名前空間にアクセスする構文を次のコードで示します。  
  
```vb  
Imports XSDSchema.Namespace  
```  
  
```csharp  
using XSDSchema.Namespace;  
```  
  
 次のコード例では、顧客**データセット**という名前の型指定された**データセット**を使用して、 **Northwind**データベースから顧客のリストを読み込みます。 **Fill**メソッドを使用してデータが読み込まれると、この例では、型指定された Customer **srow** (**DataRow**) オブジェクトを使用して**Customers**テーブルの各顧客をループします。 これにより、 **DataColumnCollection**を介してではなく、 **CustomerID**列に直接アクセスできます。  
  
```vb  
Dim customers As CustomerDataSet= New CustomerDataSet()  
Dim adapter As SqlDataAdapter New SqlDataAdapter( _  
  "SELECT * FROM dbo.Customers;", _  
  "Data Source=(local);Integrated " & _  
  "Security=SSPI;Initial Catalog=Northwind")  
  
adapter.Fill(customers, "Customers")  
  
Dim customerRow As CustomerDataSet.CustomersRow  
For Each customerRow In customers.Customers  
  Console.WriteLine(customerRow.CustomerID)  
Next  
```  
  
```csharp  
CustomerDataSet customers = new CustomerDataSet();  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT * FROM dbo.Customers;",  
  "Data Source=(local);Integrated " +  
  "Security=SSPI;Initial Catalog=Northwind");  
  
adapter.Fill(customers, "Customers");  
  
foreach(CustomerDataSet.CustomersRow customerRow in customers.Customers)  
  Console.WriteLine(customerRow.CustomerID);  
```  
  
 例に使用された XML スキーマを次に示します。  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<xs:schema id="CustomerDataSet" xmlns="" xmlns:xs="http://www.w3.org/2001/XMLSchema" xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="CustomerDataSet" msdata:IsDataSet="true">  
    <xs:complexType>  
      <xs:choice maxOccurs="unbounded">  
        <xs:element name="Customers">  
          <xs:complexType>  
            <xs:sequence>  
              <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
            </xs:sequence>  
          </xs:complexType>  
        </xs:element>  
      </xs:choice>  
    </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataColumnCollection>
- <xref:System.Data.DataSet>
- [型指定されたデータセット](typed-datasets.md)
- [DataSet、DataTable、および DataView](index.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
