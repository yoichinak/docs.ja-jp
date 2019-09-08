---
title: XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 4aa94dfaf088a2a934c8901e2720f166d3a38dae
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784412"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て
XML スキーマ定義言語 (XSD) スキーマでは、 **unique**要素は要素または属性の一意性制約を指定します。 XML スキーマをリレーショナル スキーマに変換する処理では、XML スキーマの要素または属性で指定した UNIQUE 制約が、生成される <xref:System.Data.DataTable> に対応する <xref:System.Data.DataSet> の UNIQUE 制約に割り当てられます。  
  
 次の表は、 **unique**要素で指定できる**msdata**属性の概要を示しています。  
  
|属性名|説明|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|この属性を指定した場合、その値が制約名として使用されます。 それ以外の場合、 **name**属性は制約名の値を提供します。|  
|**msdata:PrimaryKey**|Unique `PrimaryKey="true"`要素にが存在する場合は、 **IsPrimaryKey**プロパティを**true**に設定して unique 制約が作成されます。|  
  
 Unique 制約を指定するために**unique**要素を使用する XML スキーマの例を次に示します。  
  
```xml  
<xs:schema id="SampleDataSet"   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:integer"   
           minOccurs="0"/>  
        <xs:element name="CompanyName" type="xs:string"   
           minOccurs="0"/>  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
  
 <xs:element name="SampleDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:unique     msdata:ConstraintName="UCustID"     name="UniqueCustIDConstr" >       <xs:selector xpath=".//Customers" />       <xs:field xpath="CustomerID" />     </xs:unique>  
</xs:element>  
</xs:schema>  
```  
  
 スキーマ内の**unique**要素は、ドキュメントインスタンス内のすべての**Customers**要素について、 **CustomerID**子要素の値が一意である必要があることを指定します。 **データセット**の構築では、マッピングプロセスによってこのスキーマが読み取られ、次のテーブルが生成されます。  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 また、次の**データセット**に示すように、マッピングプロセスによって**CustomerID**列に unique 制約が作成されます。 (わかりやすいように、関連するプロパティだけを示します)。  
  
```  
      DataSetName: MyDataSet  
TableName: Customers  
  ColumnName: CustomerID  
      AllowDBNull: True  
      Unique: True  
  ConstraintName: UcustID       Type: UniqueConstraint  
      Table: Customers  
      Columns: CustomerID   
      IsPrimaryKey: False  
```  
  
 生成された**データセット**では、unique 制約に対して**IsPrimaryKey**プロパティが**False**に設定されています。 列の**unique**プロパティは、 **CustomerID**列の値が一意である必要があることを示します (ただし、列の**allowdbnull**プロパティで指定されているように、null 参照にすることができます)。  
  
 スキーマを変更し、オプションの**msdata: PrimaryKey**属性値を**True**に設定すると、unique 制約がテーブルに作成されます。 **Allowdbnull**列のプロパティが**False**に設定され、制約の**IsPrimaryKey**プロパティが**True**に設定されているため、 **CustomerID**列が主キー列になります。  
  
 XML スキーマの要素や属性を組み合わせて UNIQUE 制約を指定できます。 次の例では、スキーマに別の**xs: field**要素を追加することにより、 **CustomerID**値と**CompanyName**値の組み合わせを任意のインスタンスのすべての**顧客**に対して一意にする必要があることを指定する方法を示します。  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 これは、結果の**データセット**で作成される制約です。  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>関連項目

- [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML スキーマ (XSD) からの DataSet リレーションの生成](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET の概要](../ado-net-overview.md)
