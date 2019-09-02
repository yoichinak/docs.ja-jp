---
title: XML スキーマ (XSD) のキー参照制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 611322065a4df53d1a3149ef4e1ca5592f149081
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203442"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML スキーマ (XSD) のキー参照制約の DataSet 制約への割り当て
**Keyref**要素を使用すると、ドキュメント内の要素間のリンクを確立できます。 これは、リレーショナル データベースの外部キーのリレーションシップと同様です。 スキーマで**keyref**要素が指定されている場合、要素はスキーママッピングプロセス中に、 <xref:System.Data.DataSet>のテーブル内の列に対応する外部キー制約に変換されます。 既定では、 **keyref**要素は、リレーションシップに対して指定されている**parenttable**、 **childtable**、 **parenttable**、および**childtable**プロパティを使用して、リレーションシップも生成します。  
  
 次の表は、 **keyref**要素で指定できる**msdata**属性の概要を示しています。  
  
|属性名|説明|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|スキーマの**keyref**要素で**ConstraintOnly = "true"** が指定されている場合、制約が作成されますが、リレーションシップは作成されません。 この属性が指定されていない場合 (または**False**に設定されている場合) は、制約とリレーションシップの両方が**DataSet**に作成されます。|  
|**msdata:ConstraintName**|**ConstraintName**属性が指定されている場合、その値は制約の名前として使用されます。 それ以外の場合は、スキーマの**keyref**要素の**name**属性によって、**データセット**内の制約名が提供されます。|  
|**msdata:UpdateRule**|スキーマの**keyref**要素に**UpdateRule**属性が指定されている場合、その値は**データセット**の**UpdateRule** constraint プロパティに割り当てられます。 それ以外の場合、 **UpdateRule**プロパティは**Cascade**に設定されます。|  
|**msdata:DeleteRule**|スキーマの**keyref**要素に**DeleteRule**属性が指定されている場合、その値は**データセット**の**DeleteRule** constraint プロパティに割り当てられます。 それ以外の場合、 **DeleteRule**プロパティは**Cascade**に設定されます。|  
|**msdata:AcceptRejectRule**|スキーマの**keyref**要素に**AcceptRejectRule**属性が指定されている場合、その値は**データセット**の**AcceptRejectRule** constraint プロパティに割り当てられます。 それ以外の場合、 **AcceptRejectRule**プロパティは**None**に設定されます。|  
  
 次の例には、 **Order**要素の**ordernumber**子要素と**ordernumber**の**ordernumber**子要素間の**キー**および**keyref**リレーションシップを指定するスキーマが含まれています。element.  
  
 この例では、 **Ordernumber**要素の**ordernumber**子要素は、 **Order**要素の**ordernumber**キー子要素を参照します。  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 XML スキーマ定義言語 (XSD) スキーマのマッピングプロセスでは、次の2つのテーブルを含む**データセット**が生成されます。  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 また、**データセット**は、次の制約を定義します。  
  
- **Order**テーブルに対する unique 制約です。  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- **Order**テーブルと**orderdetail**テーブル間のリレーションシップ。 2つの要素がスキーマで入れ子になっていないため、 **nested**プロパティは**False**に設定されています。  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- **Orderdetail**テーブルの foreign key 制約。  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a>関連項目

- [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML スキーマ (XSD) からの DataSet リレーションの生成](generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
