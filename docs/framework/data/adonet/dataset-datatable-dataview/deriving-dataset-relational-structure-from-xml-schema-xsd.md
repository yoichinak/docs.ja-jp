---
title: XML スキーマ (XSD) からの DataSet リレーショナル構造の派生
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 549579fca0179994191987097c12b6085ee91756
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119692"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>XML スキーマ (XSD) からの DataSet リレーショナル構造の派生
ここでは、XML スキーマ定義言語 (XSD) スキーマ ドキュメントから `DataSet` のリレーショナル スキーマを生成する方法についての概要を説明します。 一般の各`complexType`スキーマ要素の子要素で、テーブルが生成、`DataSet`します。 テーブル構造は、複合型の定義に基づいて決定されます。 作成されるテーブル、`DataSet`のスキーマの最上位の要素。 ただし、テーブルを最上位レベルの作成のみ`complexType`要素と、`complexType`要素が別の内部で入れ子になった`complexType`を要素は、入れ子になった場合`complexType`要素にマップされます、`DataTable`内、`DataSet`します。  
  
 XSD の詳細については、World Wide Web Consortium (W3C) を参照してください。 [XML Schema Part 0。Primer Recommendation](https://www.w3.org/TR/xmlschema-0/)、 [XML Schema Part 1。構造体の推奨事項](https://www.w3.org/TR/xmlschema-1/)、および[XML Schema Part 2。Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/)します。  
  
 次の例では、XML スキーマ、`customers`の子要素です、`MyDataSet`要素、**データセット**要素。  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >   
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"   
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"   
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 上記の例では、`customers` 要素は複合型の要素です。 したがって、複合型の定義が解析され、割り当て処理によって次のテーブルが作成されます。  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 テーブルの各列のデータ型は、それに対応する指定された要素または属性の XML スキーマ型から派生します。  
  
> [!NOTE]
>  場合、要素`customers`などの単純な XML スキーマ データ型は**整数**テーブルは生成されません。 テーブルが作成されるのは、複合型のトップレベル要素に対してだけです。  
  
 次の XML スキーマで、**スキーマ**要素が 2 つの要素の子`InStateCustomers`と`OutOfStateCustomers`します。  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 `InStateCustomers` と `OutOfStateCustomers` の 2 つの子要素は、複合型の要素です (`customerType`)。 したがって、マッピング プロセスを生成で次の 2 つの同一テーブル、`DataSet`します。  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 一意であり、外部キー制約を作成するために使用する XML スキーマの要素について説明します、`DataSet`します。  
  
 [XML スキーマ (XSD) からの DataSet リレーションの生成](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 テーブルの列間のリレーションを作成するために使用する XML スキーマの要素について説明します、`DataSet`します。  
  
 [XML スキーマ制約およびリレーションシップ](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 XML スキーマの要素を使用して制約を作成するときに、リレーションは暗黙的に作成される方法について説明します、`DataSet`します。  
  
## <a name="related-sections"></a>関連項目  
 [DataSet での XML の使用](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 読み込んで、リレーショナル構造とデータを永続化する方法について説明します、 `DataSet` XML データとして。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
