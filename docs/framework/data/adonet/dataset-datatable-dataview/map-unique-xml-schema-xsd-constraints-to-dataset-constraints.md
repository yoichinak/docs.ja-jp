---
title: XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 56da90bf-21d3-4d1a-8bb8-de908866b78d
ms.openlocfilehash: 650cd6b8b8149529f115f22a11d19178fbd6d302
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785374"
---
# <a name="map-unique-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML スキーマ (XSD) の UNIQUE 制約の DataSet 制約への割り当て
XML スキーマ定義言語 (XSD) スキーマで、**一意**要素が要素または属性に一意性制約を指定します。 XML スキーマをリレーショナル スキーマに変換する処理では、XML スキーマの要素または属性で指定した UNIQUE 制約が、生成される <xref:System.Data.DataTable> に対応する <xref:System.Data.DataSet> の UNIQUE 制約に割り当てられます。  
  
 次の表にアウトライン、 **msdata**属性で指定することができます、**一意**要素。  
  
|属性名|説明|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|この属性を指定した場合、その値が制約名として使用されます。 それ以外の場合、**名前**属性は、制約の名前の値を提供します。|  
|**msdata:PrimaryKey**|場合`PrimaryKey="true"`に存在するが、**一意**要素、unique 制約が作成され、 **IsPrimaryKey**プロパティに設定**true**。|  
  
 次の例を使用する XML スキーマを示しています、**一意**一意性制約を指定する要素。  
  
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
  
 **一意**スキーマ内の要素を指定するすべての**顧客**ドキュメント内の要素のインスタンスの値、 **CustomerID**子要素は一意である必要があります。 ビル、**データセット**、マッピング プロセスがこのスキーマを読み取り、次の表を生成します。  
  
```  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 マッピング プロセスで unique 制約を作成することも、 **CustomerID**列では、次に示すように**データセット**します。 (わかりやすいように、関連するプロパティだけを示します)。  
  
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
  
 **データセット**、生成された、 **IsPrimaryKey**プロパティに設定されて**False**一意制約。 **一意**、列のプロパティを示す、 **CustomerID**列の値は一意である必要があります (で指定したとおり、null 参照になることができますが、 **AllowDBNull**列のプロパティ)。  
  
 スキーマを変更し、省略可能な**msdata:PrimaryKey**属性に値**True**、unique 制約をテーブルに作成します。 **AllowDBNull**列のプロパティに設定されて**False**、および**IsPrimaryKey**プロパティに設定する制約の**True**のため、**CustomerID**主キー列の列。  
  
 XML スキーマの要素や属性を組み合わせて UNIQUE 制約を指定できます。 次の例は、ことを指定する方法の組み合わせを示します**CustomerID**と**CompanyName**値はすべて一意である必要があります**顧客**任意のインスタンスで、追加する**xs:field**スキーマ内の要素。  
  
```xml  
      <xs:unique     
         msdata:ConstraintName="SomeName"    
         name="UniqueCustIDConstr" >   
  <xs:selector xpath=".//Customers" />   
  <xs:field xpath="CustomerID" />   
  <xs:field xpath="CompanyName" />   
</xs:unique>  
```  
  
 これは、その結果で作成される制約**データセット**します。  
  
```  
ConstraintName: SomeName  
  Table: Customers  
  Columns: CustomerID CompanyName   
  IsPrimaryKey: False  
```  
  
## <a name="see-also"></a>関連項目

- [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML スキーマ (XSD) からの DataSet リレーションの生成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
