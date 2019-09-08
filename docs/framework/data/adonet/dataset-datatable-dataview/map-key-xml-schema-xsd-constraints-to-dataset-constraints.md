---
title: XML スキーマ (XSD) のキー制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 22664196-f270-4ebc-a169-70e16a83dfa1
ms.openlocfilehash: 8543f5b34ee2a80ff0154897cf7678b244a8d357
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786106"
---
# <a name="map-key-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML スキーマ (XSD) のキー制約の DataSet 制約への割り当て
スキーマでは、 **key**要素を使用して、要素または属性に対してキー制約を指定できます。 キー制約を指定する要素または属性の値は、スキーマ インスタンス内で一意になる必要があります。また、null 値にすることはできません。  
  
 キー制約を定義する列の値を null 値にできない点を除くと、キー制約は UNIQUE 制約と同じです。  
  
 次の表は、 **key**要素で指定できる**msdata**属性の概要を示しています。  
  
|属性名|説明|  
|--------------------|-----------------|  
|**msdata:ConstraintName**|この属性を指定した場合、その値が制約名として使用されます。 それ以外の場合、 **name**属性は制約名の値を提供します。|  
|**msdata:PrimaryKey**|が`PrimaryKey="true"`存在する場合、 **IsPrimaryKey** constraint プロパティは**true**に設定されるため、主キーになります。 プライマリキーは null 値を持つことができないため、 **Allowdbnull**列プロパティは**false**に設定されています。|  
  
 キー制約が指定されているスキーマの変換では、制約の各列に対して**Allowdbnull** column プロパティを**false**に設定して、テーブルに unique 制約を作成します。 **Key**要素でを指定`msdata:PrimaryKey="true"`しない限り、unique 制約の**IsPrimaryKey**プロパティも**false**に設定されます。 これは、スキーマに `PrimaryKey="true"` が指定される UNIQUE 制約と同じです。  
  
 次のスキーマ例では、 **key**要素は**CustomerID**要素のキー制約を指定します。  
  
```xml  
<xs:schema id="cod"  
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  <xs:element name="Customers">  
    <xs:complexType>  
      <xs:sequence>  
        <xs:element name="CustomerID" type="xs:string" minOccurs="0" />  
        <xs:element name="CompanyName" type="xs:string" minOccurs="0" />  
       <xs:element name="Phone" type="xs:string" />  
     </xs:sequence>  
   </xs:complexType>  
 </xs:element>  
<xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element ref="Customers" />  
    </xs:choice>  
  </xs:complexType>  
   <xs:key  msdata:PrimaryKey="true"  
       msdata:ConstraintName="KeyCustID"  
          name="KeyConstCustomerID" >  
     <xs:selector xpath=".//Customers" />  
     <xs:field xpath="CustomerID" />  
    </xs:key>  
 </xs:element>  
</xs:schema>   
```  
  
 **Key**要素は、 **Customers**要素の**CustomerID**子要素の値が一意の値を持つ必要があり、null 値を持つことができないことを指定します。 XML スキーマ定義言語 (XSD) スキーマの変換では、割り当て処理によって次のテーブルが作成されます。  
  
```  
Customers(CustomerID, CompanyName, Phone)  
```  
  
 また、次<xref:System.Data.DataSet>に示すように、XML スキーママッピングによって**CustomerID**列に**UniqueConstraint**が作成されます。 (わかりやすいように、関連するプロパティだけを示します)。  
  
```  
      DataSetName: MyDataSet  
TableName: customers  
  ColumnName: CustomerID  
      AllowDBNull: False  
      Unique: True  
  ConstraintName: KeyCustID  
      Table: customers  
      Columns: CustomerID   
      IsPrimaryKey: True  
```  
  
 生成された**データセット**では、 **UniqueConstraint**の**IsPrimaryKey**プロパティが**true**に設定されてい`msdata:PrimaryKey="true"`ます。これは、スキーマで**key**要素が指定されているためです。  
  
 **データセット**内の**UniqueConstraint**の**ConstraintName**プロパティの値は、スキーマの**key**要素で指定されている**msdata: ConstraintName**属性の値です。  
  
## <a name="see-also"></a>関連項目

- [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML スキーマ (XSD) からの DataSet リレーションの生成](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET の概要](../ado-net-overview.md)
