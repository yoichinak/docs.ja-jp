---
title: DataAdapter DataTable と DataColumn のマップ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 357812aa95ea731fe86fbe49b2cb1b2806e3915a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784867"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter DataTable と DataColumn のマップ
**DataAdapter**には、その**TableMappings**プロパティ内の<xref:System.Data.Common.DataTableMapping> 0 個以上のオブジェクトのコレクションが含まれています。 **DataTableMapping**は、データソースに対するクエリから返されたデータとの<xref:System.Data.DataTable>間のマスターマッピングを提供します。 **DataTableMapping**名は、 **DataAdapter**の**Fill**メソッドに**DataTable**名の代わりに渡すことができます。 次の例では、 **Authorsmapping**という名前の **Authors**テーブルを作成します。  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 **DataTableMapping**を使用すると、データベース内の列名とは異なる列名を**DataTable**で使用できます。 **DataAdapter**は、テーブルが更新されたときに、マッピングを使用して列を照合します。  
  
 **Dataadapter**の**Fill**または**Update**メソッドを呼び出すときに**TableName**または**DataTableMapping**名を指定しない場合、 **dataadapter**は "Table" という名前の**DataTableMapping**を検索します。 この**DataTableMapping**が存在しない場合、 **DataTable**の**TableName**は "Table" になります。 既定の**DataTableMapping**を指定するには、"Table" という名前の**DataTableMapping**を作成します。  
  
 次のコード例では 、( <xref:System.Data.Common>名前空間から) DataTableMapping を作成し、"Table" という名前を付けて、指定した**DataAdapter**の既定のマッピングにします。 この例では、クエリ結果の最初のテーブル ( **northwind**データベースの**Customers**テーブル) の列を、の<xref:System.Data.DataSet> **northwind Customers**テーブルのユーザーフレンドリ名のセットにマップします。 割り当てられない列には、データ ソースの列名が使用されます。  
  
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
  
 より高度な状況では、同じ**DataAdapter**で異なるマッピングを持つ異なるテーブルの読み込みをサポートするように設定できます。 これを行うには、単に追加の**DataTableMapping**オブジェクトを追加します。  
  
 **Fill**メソッドに**DataSet**のインスタンスと**DataTableMapping**名が渡されたときに、その名前を持つマッピングが存在する場合は、その名前が使用されます。それ以外の場合は、その名前の**DataTable**が使用されます。  
  
 次の例では、 **customers**という名前の**DataTableMapping**と、**スキーマ**の**DataTable**名を作成します。 次に、SELECT ステートメントによって返された行を **、** **データテーブル**にマップします。  
  
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
> 列マップにソースの列名を指定しなかった場合、またはテーブル マップにソース テーブル名を指定しなかった場合は、自動的に既定の名前が生成されます。 列マッピングにソース列が指定されていない場合、列マッピングには**SourceColumn1**で始まる**SourceColumn** *N*という増分の既定の名前が付けられます。 テーブルマッピングにソーステーブル名が指定されていない場合、テーブルマッピングには、 **SourceTable1**で始まる**SourceTable** *N*という増分の既定の名前が与えられます。  
  
> [!NOTE]
> 列マッピングの場合は、 **SourceColumn** *n*の名前付け規則を使用しないことをお勧めします。また、指定した名前がの **既存の既定の列マッピング名と競合する可能性があるため、テーブルマッピングの場合は SourceTable n を使用することをお勧めします。使用の ColumnMappingCollection**またはテーブルマッピング名。 指定した名前が既に存在する場合は、例外がスローされます。  
  
## <a name="handling-multiple-result-sets"></a>複数の結果セットの処理  
 **SelectCommand**が複数のテーブルを返す場合、 **Fill**は、**データセット**内のテーブルの増分値を使用してテーブル名を自動的に生成します。指定されたテーブル名から始まり、その後に**TableName**という形式で続きます。*N*、 **TableName1**で始まります。 テーブルマッピングを使用すると、自動的に生成されたテーブル名を、**データセット**内のテーブルに対して指定した名前にマップできます。 たとえば、 **Customers**および**Orders**という2つのテーブルを返す**SelectCommand**の場合、 **Fill**の次の呼び出しを発行します。  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 **データセット**には、次の2つのテーブルが作成されます。**お客様**と**Customers1**。 テーブルマッピングを使用すると、2番目のテーブルに**Customers1**の代わりに**Orders**という名前が付けられるようにすることができます。 これを行うには、次の例に示すように、 **Customers1**のソーステーブルを**データセット**テーブルの**Orders**にマップします。  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>関連項目

- [DataAdapter と DataReader](dataadapters-and-datareaders.md)
- [ADO.NET でのデータの取得および変更](retrieving-and-modifying-data.md)
- [ADO.NET の概要](ado-net-overview.md)
