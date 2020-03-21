---
title: 入れ子になっている要素に指定したリレーションシップの割り当て
ms.date: 03/30/2017
ms.assetid: 24a2d3e5-4af7-4f9a-ab7a-fe6684c9e4fe
ms.openlocfilehash: cd652f51f01dcfa16a8b707f35c658043c20670d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150897"
---
# <a name="map-relations-specified-for-nested-elements"></a>入れ子になっている要素に指定したリレーションシップの割り当て
スキーマには **、msdata:Relationship**アノテーションを含めることができるので、スキーマ内の任意の 2 つの要素間のマッピングを明示的に指定できます。 **msdata:リレーションシップ**で指定された 2 つの要素は、スキーマ内で入れ子にできますが、必要はありません。 マッピング プロセスでは、スキーマ内で**msdata:Relationship**を使用して、2 つの列間の主キー/外部キーリレーションシップを生成します。  
  
 次の例は **、OrderDetail**要素が**Order**の子要素である XML スキーマを示しています。 **msdata:リレーションシップ**は、この親子リレーションシップを識別し、結果の**Order**テーブルの **[受注番号**] 列が、結果の**OrderDetail**テーブルの**OrderNo**列に関連付けられていることを指定します。  
  
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
          <xs:annotation>  
           <xs:appinfo>  
            <msdata:Relationship name="OrdODRelation"
                                msdata:parent="Order"
                                msdata:child="OrderDetail"
                                msdata:parentkey="OrderNumber"
                                msdata:childkey="OrderNo"/>  
           </xs:appinfo>  
          </xs:annotation>  
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
  
 XML スキーマの割り当て処理によって <xref:System.Data.DataSet> に作成される内容は、次のとおりです。  
  
- **注文テーブル**と**注文明細**テーブル。  
  
    ```text  
    Order(OrderNumber, EmpNumber)  
    OrderDetail(OrderNo, ItemNo)  
    ```  
  
- **Order**テーブルと**OrderDetail**テーブルの間のリレーションシップ。 このリレーションシップの**入れ子になった**プロパティは **、Order**要素と**OrderDetail**要素がスキーマ内で入れ子になっているため **、True**に設定されます。  
  
    ```text  
    ParentTable: Order  
    ParentColumns: OrderNumber
    ChildTable: OrderDetail  
    ChildColumns: OrderNo
    RelationName: OrdODRelation  
    Nested: True  
    ```  
  
 割り当て処理によって制約は作成されません。  
  
## <a name="see-also"></a>関連項目

- [XML スキーマ (XSD) からの DataSet リレーションの生成](generating-dataset-relations-from-xml-schema-xsd.md)
- [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [ADO.NET の概要](../ado-net-overview.md)
