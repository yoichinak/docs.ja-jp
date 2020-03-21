---
title: XML スキーマ (XSD) からの DataSet リレーショナル構造の派生
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d32b5cb86bc5a138f9a5f438629d8e231be4ba94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151170"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a>XML スキーマ (XSD) からの DataSet リレーショナル構造の派生
ここでは、XML スキーマ定義言語 (XSD) スキーマ ドキュメントから `DataSet` のリレーショナル スキーマを生成する方法についての概要を説明します。 一般に、スキーマ`complexType`要素の子要素ごとに、テーブルが`DataSet`. テーブル構造は、複合型の定義に基づいて決定されます。 テーブルは、スキーマの`DataSet`最上位要素で作成されます。 `complexType`ただし、最上位の要素に対してのみテーブルが作成されるのは、`complexType``complexType``complexType`要素が別の要素内に入れ子になっている場合`DataTable`です。 `DataSet`  
  
 XSD の詳細については、「 WWW (W3C) [XML スキーマ パート 0: 入門勧告](https://www.w3.org/TR/xmlschema-0/) [、XML スキーマパート 1: 構造体の推奨](https://www.w3.org/TR/xmlschema-1/)」、および[「XML スキーマパート 2: データ型の推奨事項](https://www.w3.org/TR/xmlschema-2/)」を参照してください。  
  
 次の例は、**要素**の子要素`customers``MyDataSet`である XML スキーマを示しています。  
  
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
> 要素`customers`が**整数**などの単純な XML スキーマ データ型の場合、テーブルは生成されません。 テーブルが作成されるのは、複合型のトップレベル要素に対してだけです。  
  
 次の XML スキーマでは **、Schema**要素には 2 `InStateCustomers` `OutOfStateCustomers`つの要素子と .  
  
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
  
 `InStateCustomers` と `OutOfStateCustomers` の 2 つの子要素は、複合型の要素です (`customerType`)。 したがって、マッピング プロセスでは、次の 2 つの同`DataSet`一テーブルが で生成されます。  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a>このセクションの内容  
 [XML スキーマ (XSD) 制約の DataSet 制約への割り当て](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 で一意キー制約と外部キー制約を作成するために使用する XML`DataSet`スキーマ要素について説明します。  
  
 [XML スキーマ (XSD) からの DataSet リレーションの生成](generating-dataset-relations-from-xml-schema-xsd.md)  
 テーブルの列間のリレーションシップを作成するために使用する XML スキーマ`DataSet`要素について説明します。  
  
 [XML スキーマ制約およびリレーションシップ](xml-schema-constraints-and-relationships.md)  
 XML スキーマ要素を使用して 制約を作成する場合に、リレーションが暗黙的`DataSet`に作成される方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [DataSet での XML の使用](using-xml-in-a-dataset.md)  
 リレーショナル構造およびデータを XML データとして読み込んで`DataSet`保持する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [ADO.NET の概要](../ado-net-overview.md)
