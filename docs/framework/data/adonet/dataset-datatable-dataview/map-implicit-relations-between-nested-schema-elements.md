---
title: 入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 25fc2c427727273038f7b4267376d6ba6446b811
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040382"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て
XML スキーマ言語定義 (XSD) スキーマでは、複数の複合型を入れ子にして指定できます。 この場合、割り当て処理には既定の割り当てが適用されます。その際、<xref:System.Data.DataSet> に作成される内容を次に示します。  
  
- 複合型 (親および子) それぞれに対して 1 つのテーブル。  
  
- 親に unique 制約が存在しない場合は、 *tablename*_Id という名前のテーブル定義ごとに主キー列が1つ追加されます。 *tablename*は親テーブルの名前です。  
  
- 親テーブルの primary key 制約で、追加の列を主キーとして識別します ( **IsPrimaryKey**プロパティを**True**に設定します)。 制約には、Constraint\# (\# は、1、2、3 など) という名前が付けられます。 たとえば、最初の制約の既定の名前は Constraint1 となります。  
  
- 子テーブルの外部キー制約により、追加された列が親テーブルの主キーを参照する外部キーとして認識されます。 制約には*ParentTable_ChildTable*という名前が付けられます。 *parenttable*は親テーブルの名前、 *childtable*は子テーブルの名前です。  
  
- その結果、親テーブルと子テーブル間のデータが関連付けられます。  
  
 次の例は、 **Orderdetail**が**Order**の子要素であるスキーマを示しています。  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
   <xs:complexType>  
     <xs:choice maxOccurs="unbounded">  
       <xs:element name="Order">  
         <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 XML スキーマの割り当て処理では、**データセット**に次のものが作成されます。  
  
- **Order**および**orderdetail**テーブル。  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- **Order**テーブルに対する unique 制約です。 **IsPrimaryKey**プロパティが**True**に設定されていることに注意してください。  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
- **Orderdetail**テーブルの foreign key 制約。  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
- **Order**テーブルと**orderdetail**テーブル間のリレーションシップ。 **Order**および**orderdetail**要素がスキーマで入れ子になっているため、このリレーションシップの**nested**プロパティは**True**に設定されています。  
  
    ```text  
    ParentTable: Order  
    ParentColumns: Order_Id   
    ChildTable: OrderDetail  
    ChildColumns: Order_Id   
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a>関連項目

- [XML スキーマ (XSD) からの DataSet リレーションの生成](generating-dataset-relations-from-xml-schema-xsd.md)
- [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET の概要](../ado-net-overview.md)
