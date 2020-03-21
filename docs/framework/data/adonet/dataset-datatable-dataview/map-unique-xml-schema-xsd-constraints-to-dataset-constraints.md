---
title: XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 8bcf705ce4415929e685be79f813846bbb40bb36
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150845"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て
XML スキーマ定義言語 (XSD) スキーマでは **、unique**要素は、要素または属性の一意性制約を指定します。 XML スキーマをリレーショナル スキーマに変換する処理では、XML スキーマの要素または属性で指定した UNIQUE 制約が、生成される <xref:System.Data.DataTable> に対応する <xref:System.Data.DataSet> の UNIQUE 制約に割り当てられます。  
  
 次の表は、**一意**の要素で指定できる**msdata**属性の概要を示しています。  
  
|属性名|説明|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|この属性を指定した場合、その値が制約名として使用されます。 それ以外の場合は **、name**属性によって制約名の値が指定されます。|  
|**msdata:PrimaryKey**|`PrimaryKey="true"`**一意**の要素に存在する場合は **、IsPrimaryKey**プロパティを true に設定して一意の制約が作成**されます**。|  
  
 UNIQUE 要素を使用して**一意**性制約を指定する XML スキーマの例を次に示します。  
  
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
  
 スキーマ内の**一意**の要素は、ドキュメント インスタンス内のすべての**Customers**要素に対して **、CustomerID**子要素の値が一意である必要があることを指定します。 **DataSet**を構築する場合、マッピング プロセスはこのスキーマを読み取り、次のテーブルを生成します。  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 マッピング プロセスでは、次の**DataSet**に示すように **、CustomerID**列に一意の制約も作成されます。 (わかりやすいように、関連するプロパティだけを示します)。  
  
```text  
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
  
 生成される**データセット**では、一意制約に対して**IsPrimaryKey**プロパティが**False**に設定されます。 列の**一意**のプロパティは **、CustomerID**列の値が一意である必要があることを示します (ただし、列の**AllowDBNull**プロパティで指定された null 参照を指定できます)。  
  
 スキーマを変更し、オプションの**msdata:PrimaryKey**属性値を**True**に設定すると、テーブルに UNIQUE 制約が作成されます。 **AllowDBNull**列プロパティは**False**に設定され、制約の**IsPrimaryKey**プロパティは**True**に設定されているため **、CustomerID**列は主キー列になります。  
  
 XML スキーマの要素や属性を組み合わせて UNIQUE 制約を指定できます。 次の例では、スキーマに別の**xs:field**要素を追加することによって **、CustomerID**と**CompanyName**の値の組み合わせが、任意のインスタンス内のすべての**顧客**に対して一意である必要があることを指定する方法を示します。  
  
```xml  
      <xs:unique
         msdata:ConstraintName="SomeName"
         name="UniqueCustIDConstr" >
  <xs:selector xpath=".//Customers" />
  <xs:field xpath="CustomerID" />
  <xs:field xpath="CompanyName" />
</xs:unique>  
```  
  
 これは、結果として得られる**DataSet**で作成される制約です。  
  
```text  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>関連項目

- [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML スキーマ (XSD) からの DataSet リレーションの生成](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET の概要](../ado-net-overview.md)
