---
title: XML スキーマ (XSD) のキー参照制約の DataSet 制約への割り当て
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: dcb295aef6d93222e682ef7f720c83963036e795
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229746"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a>XML スキーマ (XSD) のキー参照制約の DataSet 制約への割り当て
**Keyref**要素では、ドキュメント内の要素間のリンクを確立することができます。 これは、リレーショナル データベースの外部キーのリレーションシップと同様です。 スキーマが指定されている場合、 **keyref**要素で、要素の変換のテーブル内の列に対応する外部キー制約にスキーマのマッピング プロセス中に、<xref:System.Data.DataSet>します。 既定で、 **keyref**要素で、リレーションシップも生成されます、 **ParentTable**、 **ChildTable**、 **ParentColumn**、および**ChildColumn**リレーションの指定されたプロパティ。  
  
 次の表にアウトライン、 **msdata**属性で指定することができます、 **keyref**要素。  
  
|属性名|説明|  
|--------------------|-----------------|  
|**msdata:ConstraintOnly**|場合**ConstraintOnly ="true"** が指定されて、 **keyref**スキーマ内の要素、制約が作成されますが、リレーションシップは作成されません。 この属性が指定されていない場合 (またはに設定されている**False**)、制約とリレーションシップの両方に作成されます、**データセット**します。|  
|**msdata:ConstraintName**|場合、 **ConstraintName**属性を指定すると、その値、制約の名前として使用されます。 それ以外の場合、**名前**の属性、 **keyref**スキーマ内の要素で、制約の名前を提供します、**データセット**します。|  
|**msdata:UpdateRule**|場合、 **UpdateRule**属性が指定されて、 **keyref**スキーマ内の要素、その値に割り当てられている、 **UpdateRule**制約プロパティ、 **データセット**します。 それ以外の場合、 **UpdateRule**プロパティに設定されて**Cascade**します。|  
|**msdata:DeleteRule**|場合、 **DeleteRule**属性が指定されて、 **keyref**スキーマ内の要素、その値に割り当てられている、 **DeleteRule**制約プロパティ、 **データセット**します。 それ以外の場合、 **DeleteRule**プロパティに設定されて**Cascade**します。|  
|**msdata:AcceptRejectRule**|場合、 **AcceptRejectRule**属性が指定されて、 **keyref**スキーマ内の要素、その値に割り当てられている、 **AcceptRejectRule** 制約プロパティ**データセット**します。 それ以外の場合、 **AcceptRejectRule**プロパティに設定されて**None**します。|  
  
 次の例に示すスキーマが含まれています、**キー**と**keyref**間のリレーションシップ、 **OrderNumber**の子要素、**順序**要素と**OrderNo**の子要素、 **OrderDetail**要素。  
  
 例では、 **OrderNumber**の子要素、 **OrderDetail**要素が参照する、 **OrderNo**のキーの子要素、**順序**要素。  
  
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
  
 結果は次の XML スキーマ定義言語 (XSD) スキーマの割り当て処理**データセット**2 つのテーブル。  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 さらに、**データセット**次の制約を定義します。  
  
-   Unique 制約、**順序**テーブル。  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   間のリレーションシップ、**順序**と**OrderDetail**テーブル。 **入れ子になった**プロパティに設定されて**False**スキーマの 2 つの要素が入れ子にされていないためです。  
  
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
  
-   外部キー制約、 **OrderDetail**テーブル。  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a>関連項目

- [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [XML スキーマ (XSD) からの DataSet リレーションの生成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
