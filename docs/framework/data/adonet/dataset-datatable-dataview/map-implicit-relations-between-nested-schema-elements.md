---
title: 入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: dc5b81fd06f2860283c8c5fa028af4b945e2b1e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150964"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a>入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て
XML スキーマ言語定義 (XSD) スキーマでは、複数の複合型を入れ子にして指定できます。 この場合、割り当て処理には既定の割り当てが適用されます。その際、<xref:System.Data.DataSet> に作成される内容を次に示します。  
  
- 複合型 (親および子) それぞれに対して 1 つのテーブル。  
  
- 親に UNIQUE 制約が存在しない場合は *、TableName*という名前のテーブル定義ごとに 1 つの追加の主キー列_Id *TableName*が親テーブルの名前になります。  
  
- 追加の列を主キーとして識別する親テーブルの主キー制約 ( **IsPrimaryKey**プロパティを**True**に設定して ) 制約には、Constraint\# (\# は、1、2、3 など) という名前が付けられます。 たとえば、最初の制約の既定の名前は Constraint1 となります。  
  
- 子テーブルの外部キー制約により、追加された列が親テーブルの主キーを参照する外部キーとして認識されます。 制約は、*親テーブル*の名前が親テーブルの名前、子テーブルの名前である*場合**、ParentTable_ChildTable*名前が付けられます。  
  
- その結果、親テーブルと子テーブル間のデータが関連付けられます。  
  
 次の例は **、OrderDetail**が**Order**の子要素であるスキーマを示しています。  
  
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
  
 XML スキーマ マッピング プロセスでは **、DataSet**に次の情報が作成されます。  
  
- **注文テーブル**と**注文明細**テーブル。  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- **Order**テーブルの一意性制約。 **プロパティが** **True**に設定されていることを確認します。  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- **OrderDetail**テーブルの外部キー制約。  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- **Order**テーブルと**OrderDetail**テーブルの間のリレーションシップ。 このリレーションシップの**入れ子になった**プロパティは **、Order**要素と**OrderDetail**要素がスキーマ内で入れ子になっているため **、True**に設定されます。  
  
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
