---
title: XML スキーマ制約およびリレーションシップ
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 2388d7c277ba1f01bea8d419e5aedf487b843ed7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150715"
---
# <a name="xml-schema-constraints-and-relationships"></a>XML スキーマ制約およびリレーションシップ
XML スキーマ定義言語 (XSD) スキーマでは、制約 (一意制約、キー制約、およびキー参照制約) とリレーションシップ **(msdata:Relationship**アノテーションを使用) を指定できます。 このトピックでは、XML スキーマで指定した制約およびリレーションシップを解釈して <xref:System.Data.DataSet> を生成する方法について説明します。  
  
 一般に、XML スキーマでは、 **DataSet**でリレーションシップのみを生成する場合は **、 msdata:Relationship**アノテーションを指定します。 詳細については、「 [XML スキーマからのデータセット関係の生成 (XSD)」](generating-dataset-relations-from-xml-schema-xsd.md)を参照してください。 制約 (一意性、キー、およびキー参照) を指定するには、 **DataSet**で制約を生成します。 このトピックの後に説明されているように、リレーションシップを生成するにはキー制約とキー参照制約も使用するので注意してください。  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a>キー制約およびキー参照制約によるリレーションシップの生成  
 **msdata:Relationship**アノテーションを指定する代わりに、XML スキーママッピングプロセスで使用されるキー制約とキー参照制約を指定して、制約だけでなく**DataSet**内の関係も生成できます。 ただし **、keyref** `msdata:ConstraintOnly="true"`要素で指定した場合 **、DataSet**には制約のみが含まれ、リレーションシップは含まれません。  
  
 次の例は、入れ子になっていない**Order**要素と**OrderDetail**要素を含む XML スキーマを示しています。 スキーマでは、キー制約とキー参照制約も指定します。  
  
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
  
 XML スキーマ マッピング プロセス中に生成される**データセット**には **、Order**テーブルと**OrderDetail**テーブルが含まれます。 さらに、**データセット**にはリレーションシップと制約が含まれています。 そのリレーションシップと制約の例を次に示します。 スキーマは**msdata:リレーションシップ**アノテーションを指定しないことに注意してください。代わりに、キーとキー参照の拘束を使用してリレーションを生成します。  
  
```text
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 前のスキーマの例では **、Order**要素と**OrderDetail**要素は入れ子になっていません。 入れ子になっている Order 要素と OrderDetail 要素を含むスキーマの例を次に示します。 ただし **、msdata:リレーションシップ**の注釈が指定されていません。したがって、暗黙のリレーションが想定されます。 詳細については、「[入れ子になったスキーマ要素間の暗黙的な関係のマップ](map-implicit-relations-between-nested-schema-elements.md)」を参照してください。 スキーマでは、キー制約とキー参照制約も指定します。  
  
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
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
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
  
 XML スキーマ マッピング プロセスの結果として得られる**DataSet**には、次の 2 つのテーブルが含まれます。  
  
```text  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 **DataSet**には、2 つのリレーションシップ **(msdata: リレーションシップ**アノテーションに基づくものと、キー制約とキー参照制約に基づくリレーションシップ) とさまざまな制約も含まれています。 リレーションおよび制約の例を次に示します。  
  
```text
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 入れ子になったテーブルを参照するキー参照制約に**msdata:IsNested="true"** 注釈が含まれている場合 **、DataSet**は keyref 制約と関連する一意/キー制約に基づいて単一のネストされたリレーションシップを作成します。  
  
## <a name="see-also"></a>関連項目

- [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [ADO.NET の概要](../ado-net-overview.md)
