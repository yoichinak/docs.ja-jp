---
title: XML スキーマ (XSD) からの DataSet リレーショナル構造の派生
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: ef77030b4e847f91fea074b68e223ac622539048
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040100"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>XML スキーマ (XSD) からの DataSet リレーショナル構造の派生
ここでは、XML スキーマ定義言語 (XSD) スキーマ ドキュメントから `DataSet` のリレーショナル スキーマを生成する方法についての概要を説明します。 一般に、スキーマ要素の各 `complexType` 子要素に対して、テーブルが `DataSet`に生成されます。 テーブル構造は、複合型の定義に基づいて決定されます。 テーブルは、スキーマの最上位レベルの要素の `DataSet` に作成されます。 ただし、テーブルは、最上位の `complexType` 要素に対してのみ作成されます。この場合、`complexType` 要素が別の `complexType` 要素の中に入れ子になっていると、入れ子になった `complexType` 要素が `DataTable` 内の `DataSet`にマップされます。  
  
 XSD の詳細については、World Wide Web コンソーシアム (W3C) 『 [Xml Schema part 0: 入門勧告』](https://www.w3.org/TR/xmlschema-0/)、『 [xml schema Part 1: 構造](https://www.w3.org/TR/xmlschema-1/)に関する推奨事項」、および「 [Xml Schema part 2: データ型の推奨事項](https://www.w3.org/TR/xmlschema-2/)」を参照してください。  
  
 次の例は、XML スキーマを示しています。 `customers` は、 **DataSet**要素である `MyDataSet` 要素の子要素です。  
  
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
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 テーブルの各列のデータ型は、それに対応する指定された要素または属性の XML スキーマ型から派生します。  
  
> [!NOTE]
> 要素 `customers` が**整数**などの単純な XML スキーマデータ型である場合、テーブルは生成されません。 テーブルが作成されるのは、複合型のトップレベル要素に対してだけです。  
  
 次の XML スキーマでは、 **Schema**要素に2つの子要素 `InStateCustomers` と `OutOfStateCustomers`があります。  
  
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
  
 `InStateCustomers` と `OutOfStateCustomers` の 2 つの子要素は、複合型の要素です (`customerType`)。 そのため、マッピングプロセスでは、`DataSet`内に次の2つの同一のテーブルが生成されます。  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 `DataSet`で unique および foreign key 制約を作成するために使用される XML スキーマ要素について説明します。  
  
 [XML スキーマ (XSD) からの DataSet リレーションの生成](generating-dataset-relations-from-xml-schema-xsd.md)  
 `DataSet`内のテーブル列間のリレーションを作成するために使用される XML スキーマ要素について説明します。  
  
 [XML スキーマ制約およびリレーションシップ](xml-schema-constraints-and-relationships.md)  
 XML スキーマ要素を使用して `DataSet`に制約を作成するときに、暗黙的にリレーションシップを作成する方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [DataSet での XML の使用](using-xml-in-a-dataset.md)  
 リレーショナル構造とデータを XML データとして `DataSet` に読み込んで永続化する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../ado-net-overview.md)
