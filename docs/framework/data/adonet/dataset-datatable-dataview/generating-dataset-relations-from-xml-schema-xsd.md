---
title: XML スキーマ (XSD) からの DataSet リレーションの生成
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: feb0be7f66bf0f407e54ef0830c13f0c4a8a6418
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151131"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>XML スキーマ (XSD) からの DataSet リレーションの生成
<xref:System.Data.DataSet> では、親子のリレーションを作成することにより、2 つ以上の列間の関連付けを行います。 XML スキーマ定義言語 (XSD) スキーマ内の**DataSet**リレーションシップを表す方法は 3 つあります。  
  
- 入れ子になった複合型を指定する方法  
  
- **msdata:リレーションシップ**アノテーションを使用します。  
  
- **msdata:制約のみ**注釈を指定せずに**xs:keyref**を指定します。  
  
## <a name="nested-complex-types"></a>入れ子になった複合型  
 スキーマ内で複数の複合型の定義が入れ子になっている場合は、それらの入れ子状の要素間に親子のリレーションシップがあります。 次の XML スキーマ フラグメントは **、OrderDetail**が**Order**要素の子要素であることを示しています。  
  
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
  
 XML スキーマ マッピング プロセスでは、スキーマ内の入れ子になった複合型に対応するテーブルが**DataSet**に作成されます。 また、生成されたテーブルの親**-** 子列として使用される追加の列も作成されます。 これらの親**-** 子列は、主キー/外部キー制約を指定することとは異なりますが、リレーションシップを指定します。  
  
## <a name="msdatarelationship-annotation"></a>msdata:Relationship 注釈  
 **msdata:Relationship**アノテーションを使用すると、ネストされていないスキーマ内の要素間の親子関係を明示的に指定できます。 次の例は、**リレーションシップ**要素の構造を示しています。  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 **msdata:Relationship**アノテーションの属性は、親子関係に関係する要素、およびリレーションシップに関連する**親キー**要素および**子キー**要素および属性を識別します。 マッピング プロセスでは、この情報を使用して**DataSet**内にテーブルを生成し、これらのテーブル間の主キー/外部キー リレーションシップを作成します。  
  
 たとえば、次のスキーマ フラグメントは、同じレベル (入れ子になっていない) で**Order**要素と**OrderDetail**要素を指定します。 スキーマは、これら 2 つの要素間の親子関係を指定する**msdata:Relationship**アノテーションを指定します。 この場合、明示的な関係は **、msdata:Relationship**アノテーションを使用して指定する必要があります。  
  
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
  
 マッピング プロセスでは、**リレーションシップ**要素を使用して **、Order**テーブルの**OrderNumber**列と **、データセット**の**OrderDetail**テーブルの**OrderNo**列との間に親子リレーションシップを作成します。 割り当て処理で指定されるのはリレーションシップだけで、リレーショナル データベースにおける主キー制約や外部キー制約の場合とは異なり、該当する列の値に対する制約が自動的に指定されることはありません。  
  
### <a name="in-this-section"></a>このセクションの内容  
 [入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て](map-implicit-relations-between-nested-schema-elements.md)  
 XML スキーマで入れ子になった要素が検出されたときに **、DataSet**で暗黙的に作成される制約と関係について説明します。  
  
 [入れ子になっている要素に指定したリレーションシップの割り当て](map-relations-specified-for-nested-elements.md)  
 XML スキーマ内の入れ子になった要素に対して **、DataSet**で明示的にリレーションシップを設定する方法について説明します。  
  
 [入れ子になっていない要素間のリレーションの指定](specify-relations-between-elements-with-no-nesting.md)  
 入れ子になっていない XML スキーマ要素間の**DataSet**のリレーションシップを作成する方法について説明します。  
  
### <a name="related-sections"></a>関連項目  
 [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 XML スキーマ定義言語 (XSD) スキーマから作成される**DataSet**のリレーショナル構造 (スキーマ) について説明します。  
  
 [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 **DataSet**で一意キーおよび外部キー制約を作成するために使用する XML スキーマ要素について説明します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../ado-net-overview.md)
