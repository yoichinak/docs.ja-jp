---
title: XML スキーマ (XSD) のキー参照制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 902b79b73f494ced0f54b29babff1b2e767bd47a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150884"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML スキーマ (XSD) のキー参照制約の DataSet 制約への割り当て
**keyref**要素を使用すると、ドキュメント内の要素間のリンクを確立できます。 これは、リレーショナル データベースの外部キーのリレーションシップと同様です。 スキーマが**keyref**要素を指定している場合、要素はスキーマ マッピングプロセス中に、 のテーブルの列に対する対応する外部<xref:System.Data.DataSet>キー制約に変換されます。 既定では **、keyref**要素は、リレーションシップに指定された**親テーブル**、**子テーブル**、**親列**、**および子列**のプロパティを持つリレーションシップも生成します。  
  
 次の表に **、keyref**要素で指定できる**msdata**属性の概要を示します。  
  
|属性名|説明|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|スキーマの**keyref**要素に**制約のみ="true" が**指定されている場合、制約は作成されますが、リレーションシップは作成されません。 この属性が指定されていない (または**False**に設定されている) 場合、制約とリレーションの両方が**DataSet**に作成されます。|  
|**msdata:ConstraintName**|**制約名**属性を指定すると、その値が制約の名前として使用されます。 それ以外の場合は、スキーマ内の**keyref**要素の**name**属性が **、DataSet**に制約名を提供します。|  
|**msdata:UpdateRule**|**スキーマ**の**keyref**要素で属性が指定されている場合、その値は**DataSet**の**UpdateRule**制約プロパティに割り当てられます。 それ以外の場合は、**プロパティ**が**カスケード**に設定されます。|  
|**msdata:DeleteRule**|スキーマの**keyref**要素で**DeleteRule**属性が指定されている場合、その値は**DataSet**の**DeleteRule**制約プロパティに割り当てられます。 それ以外の場合は **、DeleteRule**プロパティがカスケードに設定**されます**。|  
|**msdata:AcceptRejectRule**|属性が**スキーマ**の**キー参照**要素で指定されている場合、その値は**データセット**の**AcceptRejectRule**制約プロパティに割り当てられます。 それ以外の場合は **、"拒否拒否ルールの受け入れ"** プロパティが **[なし]** に設定されます。|  
  
 次の例には **、Order**要素の OrderNumber 子要素と**OrderDetail**要素の**OrderNo** **OrderNo**子要素との間の**キー**と**キー参照**の関係を指定するスキーマが含まれています。  
  
 この例では **、OrderDetail**要素の **"OrderNumber/受注番号**" 子要素は **、Order**要素の **"OrderNo/順序**なし" キーの子要素を参照しています。  
  
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
  
 XML スキーマ定義言語 (XSD) スキーマ マッピング プロセスでは、次の**DataSet**が 2 つのテーブルで生成されます。  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 さらに、**データセットは**次の制約を定義します。  
  
- **Order**テーブルの一意性制約。  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- **Order**テーブルと**OrderDetail**テーブルの間のリレーションシップ。 2 つの要素がスキーマ内で入れ子になっていないため **、Nested**プロパティは**False**に設定されます。  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- **OrderDetail**テーブルの外部キー制約。  
  
    ```text  
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
- [ADO.NET の概要](../ado-net-overview.md)
