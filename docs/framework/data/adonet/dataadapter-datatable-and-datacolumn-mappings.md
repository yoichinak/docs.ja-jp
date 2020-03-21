---
title: DataAdapter DataTable と DataColumn のマップ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 6380dd0512bd7834f50b87f90f445cb01b7a8b95
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151560"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter DataTable と DataColumn のマップ
**データ アダプター**には、その<xref:System.Data.Common.DataTableMapping>**TableMappings**プロパティに 0 個以上のオブジェクトのコレクションが含まれています。 **DataTableMapping**は、クエリから返されたデータとデータ ソースとの間のマスター マッピング<xref:System.Data.DataTable>を提供します。 **名前**は **、データ**テーブル名の代わりにデータ**アダプター**の**Fill**メソッドに渡すことができます。 次の例では、Authors テーブルの**AuthorsMapping**という名前の**データテーブル**マッピングを**作成**します。  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 **データ テーブル マッピング**を使用すると、データベース内の列とは異なる列名をデータ**テーブル**で使用できます。 **DataAdapter は**、テーブルが更新されたときに、列を一致させるためにマッピングを使用します。  
  
 **データアダプタ**の**Fill**メソッドまたは**Update**メソッドを呼び出すときに**テーブル名**または**データ テーブル マッピング**名を指定しない場合、**データアダプター**は "テーブル" という名前の**データ テーブル マッピング**を検索します。 その**データ テーブル マッピング**が存在しない場合、データ**テーブル**の**テーブル名**は "テーブル" です。 "テーブル" という名前の**データ**テーブル**マッピング**を作成することで、既定のデータ テーブル マッピングを指定できます。  
  
 次のコード例では、<xref:System.Data.Common>名前空間から**DataTableMapping**を作成し、"テーブル" という名前を付けて指定した**DataAdapter**の既定のマッピングにします。 次に、クエリ結果の最初のテーブル **(Northwind**データベースの**Customers**テーブル) の列を、 の**Northwind Customers**テーブル内のわかりやすい名前のセット<xref:System.Data.DataSet>にマップします。 割り当てられない列には、データ ソースの列名が使用されます。  
  
```vb  
Dim mapping As DataTableMapping = _  
  adapter.TableMappings.Add("Table", "NorthwindCustomers")  
mapping.ColumnMappings.Add("CompanyName", "Company")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode")  
  
adapter.Fill(custDS)  
```  
  
```csharp  
DataTableMapping mapping =
  adapter.TableMappings.Add("Table", "NorthwindCustomers");  
mapping.ColumnMappings.Add("CompanyName", "Company");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIPCode");  
  
adapter.Fill(custDS);  
```  
  
 より高度な状況では、同じ**DataAdapter**で異なるマッピングを持つ異なるテーブルの読み込みをサポートするように設定できます。 これを行うには、単に追加**のデータテーブルマッピングオブジェクトを**追加します。  
  
 **Fill**メソッドに**DataSet**のインスタンスと**DataTableMapping**名が渡されると、その名前のマッピングが使用されます。それ以外の場合は、その名前の**DataTable**が使用されます。  
  
 次の例では、**顧客**の名前と**BizTalkSchema**の**データ テーブル**名を使用してデータ テーブル**マッピング**を作成します。 次に、SELECT ステートメントによって返された行を**BizTalk スキーマ****データ テーブル**にマップします。  
  
```vb  
Dim mapping As ITableMapping = _  
  adapter.TableMappings.Add("Customers", "BizTalkSchema")  
mapping.ColumnMappings.Add("CustomerID", "ClientID")  
mapping.ColumnMappings.Add("CompanyName", "ClientName")  
mapping.ColumnMappings.Add("ContactName", "Contact")  
mapping.ColumnMappings.Add("PostalCode", "ZIP")  
  
adapter.Fill(custDS, "Customers")  
```  
  
```csharp  
ITableMapping mapping =
  adapter.TableMappings.Add("Customers", "BizTalkSchema");  
mapping.ColumnMappings.Add("CustomerID", "ClientID");  
mapping.ColumnMappings.Add("CompanyName", "ClientName");  
mapping.ColumnMappings.Add("ContactName", "Contact");  
mapping.ColumnMappings.Add("PostalCode", "ZIP");  
  
adapter.Fill(custDS, "Customers");  
```  
  
> [!NOTE]
> 列マップにソースの列名を指定しなかった場合、またはテーブル マップにソース テーブル名を指定しなかった場合は、自動的に既定の名前が生成されます。 列マッピングにソース列が指定されていない場合、列マッピングには、ソース**列 1**から始まる増分デフォルト名の**SourceColumn** *N*が付けられます。 テーブル マッピングにソース テーブル名が指定されていない場合、テーブル マッピングには **、SourceTable** *N*の増分デフォルト名が**SourceTable1**から始まります。  
  
> [!NOTE]
> 指定する名前は**ColumnMappingCollection**の既存の既定の列マッピング名または**DataTableMappingCollection**のテーブル マッピング名と競合する可能性があるため、列マッピングの場合は**SourceColumn** *N、* テーブル マッピングの**SourceTable** *N*という名前付け規則を使用しないようにすることをお勧めします。 指定した名前が既に存在する場合は、例外がスローされます。  
  
## <a name="handling-multiple-result-sets"></a>複数の結果セットの処理  
 **SelectCommand が**複数のテーブルを返す場合 **、Fill**は指定されたテーブル名から始まり、TableNameN という形式で**続***N*く**DataSet**のテーブルの増分値を持**TableName1**つテーブル名を自動的に生成します。 テーブル マッピングを使用して、自動的に生成されたテーブル名を**DataSet**内のテーブルに指定する名前にマップできます。 たとえば **、"得意先"** と **"受注"** という 2 つのテーブルを返す**SelectCommand**の場合は、次の呼び出しを**Fill**に発行します。  
  
```vb  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.Fill(customersDataSet, "Customers");  
```  

 2 つのテーブルが**データセット**に作成されます:**顧客**と**得意先1**。 テーブル マッピングを使用して、2 番目のテーブルが**Customers1**ではなく**Orders**という名前であることを確認できます。 これを行うには、次の例に示すように **、Customers1**のソース テーブルを**DataSet**テーブル**Orders**にマップします。  
  
```vb  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  

```csharp  
adapter.TableMappings.Add("Customers1", "Orders");  
adapter.Fill(customersDataSet, "Customers");  
```
  
## <a name="see-also"></a>関連項目

- [DataAdapter と DataReader](dataadapters-and-datareaders.md)
- [ADO.NET でのデータの取得および変更](retrieving-and-modifying-data.md)
- [ADO.NET の概要](ado-net-overview.md)
