---
title: XML スキーマ (XSD) からの DataSet リレーションの生成
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: d00f07ee3338941b7de1bb890f71cd3c2d120246
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784646"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a>XML スキーマ (XSD) からの DataSet リレーションの生成
<xref:System.Data.DataSet> では、親子のリレーションを作成することにより、2 つ以上の列間の関連付けを行います。 XML スキーマ定義言語 (XSD) スキーマ内の**データセット**の関係を表すには、次の3つの方法があります。  
  
- 入れ子になった複合型を指定する方法  
  
- **Msdata: Relationship**注釈を使用します。  
  
- **Msdata: ConstraintOnly**注釈を付けずに**xs: keyref**を指定します。  
  
## <a name="nested-complex-types"></a>入れ子になった複合型  
 スキーマ内で複数の複合型の定義が入れ子になっている場合は、それらの入れ子状の要素間に親子のリレーションシップがあります。 次の XML スキーマフラグメントは、 **Orderdetail**が**Order**要素の子要素であることを示しています。  
  
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
  
 XML スキーマの割り当て処理により、スキーマ内の入れ子になった複合型に対応するテーブルが**データセット**に作成されます。 また、生成されたテーブルの親 **-** 子列として使用される追加の列も作成されます。 これらの親子 **-** 列ではリレーションシップが指定されていることに注意してください。これは、primary key 制約または foreign key 制約を指定するのと同じではありません。  
  
## <a name="msdatarelationship-annotation"></a>msdata:Relationship 注釈  
 **Msdata: Relationship**注釈を使用すると、入れ子になっていないスキーマ内の要素間の親子リレーションシップを明示的に指定できます。 次の例は、**リレーションシップ**要素の構造を示しています。  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 **Msdata: relationship**注釈の属性は、リレーションシップに関係する**parentkey**要素と**childkey**要素および属性に加えて、親子リレーションシップに関係する要素を識別します。 このマッピングプロセスでは、この情報を使用して、**データセット**内のテーブルを生成し、これらのテーブル間に主キー/外部キーのリレーションシップを作成します。  
  
 たとえば、次のスキーマフラグメントでは、 **Order**および**orderdetail**要素が同じレベル (入れ子になっていない) で指定されています。 スキーマでは、これら2つの要素間の親子リレーションシップを指定する**msdata: Relationship**注釈を指定します。 この場合は、 **msdata: relationship**注釈を使用して明示的なリレーションシップを指定する必要があります。  
  
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
  
 マッピングプロセスでは、**リレーションシップ**要素を使用して、 **Order**テーブルの**Ordernumber**列と**データセット**の**ordernumber**テーブルの**ordernumber**列の間に親子リレーションシップを作成します。 割り当て処理で指定されるのはリレーションシップだけで、リレーショナル データベースにおける主キー制約や外部キー制約の場合とは異なり、該当する列の値に対する制約が自動的に指定されることはありません。  
  
### <a name="in-this-section"></a>このセクションの内容  
 [入れ子になっているスキーマ要素間の暗黙的なリレーションの割り当て](map-implicit-relations-between-nested-schema-elements.md)  
 XML スキーマで入れ子になった要素が検出された場合に、**データセット**に暗黙的に作成される制約とリレーションシップについて説明します。  
  
 [入れ子になっている要素に指定したリレーションシップの割り当て](map-relations-specified-for-nested-elements.md)  
 XML スキーマの入れ子になった要素に対して、**データセット**内のリレーションを明示的に設定する方法について説明します。  
  
 [入れ子になっていない要素間のリレーションの指定](specify-relations-between-elements-with-no-nesting.md)  
 入れ子になっていない XML スキーマ要素間の**データセット**内のリレーションを作成する方法について説明します。  
  
### <a name="related-sections"></a>関連項目  
 [XML スキーマ (XSD) からの DataSet リレーショナル構造の派生](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 XML スキーマ定義言語 (XSD) スキーマから作成される**データセット**のリレーショナル構造 (スキーマ) について説明します。  
  
 [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 **DataSet**で unique および foreign key 制約を作成するために使用される XML スキーマ要素について説明します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../ado-net-overview.md)
