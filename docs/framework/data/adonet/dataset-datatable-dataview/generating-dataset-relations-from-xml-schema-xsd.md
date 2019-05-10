---
title: XML スキーマ (XSD) からの DataSet リレーションの生成
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: 2cf6d2ed949a3efa39c0f1c049bc03e7a5b0eb0b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621080"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>XML スキーマ (XSD) からの DataSet リレーションの生成
<xref:System.Data.DataSet> では、親子のリレーションを作成することにより、2 つ以上の列間の関連付けを行います。 3 つの方法を表す、**データセット**XML スキーマ定義言語 (XSD) スキーマ内の関係。  
  
- 入れ子になった複合型を指定する方法  
  
- 使用して、 **msdata:Relationship**注釈。  
  
- 指定、 **xs:keyref**せず、 **msdata:ConstraintOnly**注釈。  
  
## <a name="nested-complex-types"></a>入れ子になった複合型  
 スキーマ内で複数の複合型の定義が入れ子になっている場合は、それらの入れ子状の要素間に親子のリレーションシップがあります。 次の XML スキーマ フラグメントことを示しています**OrderDetail**の子要素には、**順序**要素。  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>          
       <xs:element name="OrderDetail" />  
           <xs:complexType>               
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 XML スキーマのマッピング プロセス内のテーブルの作成、**データセット**スキーマで入れ子になった複合型に対応しています。 親として使用されるその他の列も作成**-** 生成されたテーブルの子列。 これらの親注**-** 子列はリレーションシップが指定される主キー/外部キー制約を指定すると同じです。  
  
## <a name="msdatarelationship-annotation"></a>msdata:Relationship 注釈  
 **Msdata:Relationship**注釈では、スキーマ内の入れ子になっていない要素間の親子リレーションシップを明示的に指定できます。 次の例の構造を示しています、**リレーションシップ**要素。  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 属性、 **msdata:Relationship**注釈としても、親子リレーションシップに関連する要素を識別する、 **parentkey**と**childkey**要素と属性、リレーションシップに関係します。 マッピング プロセスでは、この情報を使用して、内のテーブルを生成する、**データセット**とこれらのテーブル間の主キー/外部キー リレーションシップを作成します。  
  
 たとえば、次のスキーマ フラグメントを指定します**順序**と**OrderDetail**同じレベルの要素 (入れ子になっていない)。 スキーマを指定します、 **msdata:Relationship**注釈で、これら 2 つの要素間の親子リレーションシップを指定します。 使用して、明示的なリレーションシップを指定する必要があります、ここで、 **msdata:Relationship**注釈。  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"   
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 マッピング プロセスを使用して、**リレーションシップ**要素間の親子リレーションシップを作成する、 **OrderNumber**内の列、**順序**テーブルと、 **OrderNo**内の列、 **OrderDetail**テーブルに、**データセット**します。 割り当て処理で指定されるのはリレーションシップだけで、リレーショナル データベースにおける主キー制約や外部キー制約の場合とは異なり、該当する列の値に対する制約が自動的に指定されることはありません。  
  
### <a name="in-this-section"></a>このセクションの内容  
 [入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 制約およびリレーションで暗黙的に作成された説明を**データセット**XML スキーマで入れ子になった要素が発生した場合。  
  
 [入れ子になっている要素に指定したリレーションシップの割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 リレーションを明示的に設定する方法について説明します、**データセット**XML スキーマで入れ子になった要素。  
  
 [入れ子になっていない要素間のリレーションの指定](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 リレーションシップを作成する方法について説明します、**データセット**入れ子にされていない XML スキーマ要素間。  
  
### <a name="related-sections"></a>関連項目  
 [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 リレーショナル構造体、またはスキーマをについて説明します、**データセット**XML スキーマ定義言語 (XSD) スキーマから作成されました。  
  
 [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 一意であり、外部キー制約を作成するために使用する XML スキーマの要素について説明します、**データセット**します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
