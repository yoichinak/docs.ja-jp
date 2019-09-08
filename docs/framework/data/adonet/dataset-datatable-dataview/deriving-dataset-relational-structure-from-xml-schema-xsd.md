---
title: XML スキーマ (XSD) からの DataSet リレーショナル構造の派生
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d15aa02b41b9a34b00298aeb32d2e3998de8feba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786341"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>XML スキーマ (XSD) からの DataSet リレーショナル構造の派生
ここでは、XML スキーマ定義言語 (XSD) スキーマ ドキュメントから `DataSet` のリレーショナル スキーマを生成する方法についての概要を説明します。 一般に、スキーマ要素`complexType`の各子要素に対して`DataSet`、でテーブルが生成されます。 テーブル構造は、複合型の定義に基づいて決定されます。 テーブルは、スキーマ内`DataSet`の最上位の要素に対して、で作成されます。 ただし、 `complexType`要素が別`complexType` `complexType`の要素の内部に入れ子になっている場合は、最上位レベルの要素に対してのみ`complexType`テーブルが作成され`DataTable` `DataSet`ます。この場合、入れ子になった要素は内のにマップされます。  
  
 XSD の詳細については、次を参照して[ください。 World Wide Web コンソーシアム (W3C) XML スキーマパート 0:入門勧告](https://www.w3.org/TR/xmlschema-0/) [、XML スキーマパート 1:構造に](https://www.w3.org/TR/xmlschema-1/)関する推奨事項[、および XML スキーマ第2部:Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/)」 (XML スキーマ第 2 部: データ型の推奨事項) を参照してください。  
  
 次の例は、XML スキーマ`customers`を示しています。は、 `MyDataSet`要素の子要素であり、 **DataSet**要素です。  
  
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
> 要素`customers`が**integer**のような単純な XML スキーマデータ型の場合、テーブルは生成されません。 テーブルが作成されるのは、複合型のトップレベル要素に対してだけです。  
  
 次の XML スキーマでは、**スキーマ**要素に`InStateCustomers`とと`OutOfStateCustomers`いう2つの子要素があります。  
  
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
  
 `InStateCustomers` と `OutOfStateCustomers` の 2 つの子要素は、複合型の要素です (`customerType`)。 したがって、マッピングプロセスでは、 `DataSet`で次の2つの同一のテーブルが生成されます。  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 で unique および foreign key 制約を作成するために使用される XML `DataSet`スキーマ要素について説明します。  
  
 [XML スキーマ (XSD) からの DataSet リレーションの生成](generating-dataset-relations-from-xml-schema-xsd.md)  
 のテーブル列`DataSet`間のリレーションを作成するために使用される XML スキーマ要素について説明します。  
  
 [XML スキーマ制約およびリレーションシップ](xml-schema-constraints-and-relationships.md)  
 XML スキーマ要素を使用してで制約を作成するときに、 `DataSet`暗黙的にリレーションシップを作成する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [DataSet での XML の使用](using-xml-in-a-dataset.md)  
 のリレーショナル構造とデータ`DataSet`を XML データとして読み込んで永続化する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../ado-net-overview.md)
