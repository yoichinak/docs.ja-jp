---
title: DataAdapter DataTable と DataColumn のマップ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d023260a-a66a-4c39-b8f4-090cd130e730
ms.openlocfilehash: 54af7c2f449f8eb289841fb3eca357c6916404aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201209"
---
# <a name="dataadapter-datatable-and-datacolumn-mappings"></a>DataAdapter DataTable と DataColumn のマップ
A **DataAdapter** 0 個以上のコレクションを含む<xref:System.Data.Common.DataTableMapping>オブジェクトでその**TableMappings**プロパティ。 A **DataTableMapping** 、データ ソースに対するクエリから返されるデータ間のマスター マップを提供し、<xref:System.Data.DataTable>します。 **DataTableMapping**の代わりに名前を渡すことができます、 **DataTable**名、**入力**のメソッド、 **DataAdapter**します。 次の例では、作成、 **DataTableMapping**という**AuthorsMapping**の**作成者**テーブル。  
  
```vb  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors")  
```  
  
```csharp  
workAdapter.TableMappings.Add("AuthorsMapping", "Authors");  
```  
  
 A **DataTableMapping**で列名を使用することができます、 **DataTable**データベースと異なります。 **DataAdapter**テーブルが更新されたときに、列を一致するように、マップを使用します。  
  
 指定しない場合、 **TableName**または**DataTableMapping**名前を呼び出すときに、**入力**または**Update**のメソッド、 **DataAdapter**、 **DataAdapter**探し、 **DataTableMapping** "Table"という名前です。 その場合**DataTableMapping**が存在しない、 **TableName**の**DataTable** 「テーブル」です。 既定値を指定する**DataTableMapping**を作成して、 **DataTableMapping** "Table"の名前に置き換えます。  
  
 次のコード例を作成、 **DataTableMapping** (から、<xref:System.Data.Common>名前空間) になり、指定された既定のマッピング**DataAdapter** "Table"名前を付けて、します。 例では、クエリ結果の最初のテーブルから列をマップし、(、**顧客**のテーブル、 **Northwind**データベース) でよりわかりやすい名前のセットに、 **Northwind の Customers**テーブルに、<xref:System.Data.DataSet>します。 割り当てられない列には、データ ソースの列名が使用されます。  
  
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
  
 高度な状況は、同じすることを決めることがあります**DataAdapter**異なるマッピングに別のテーブルの読み込みをサポートするためにします。 これを行うには、追加**DataTableMapping**オブジェクト。  
  
 ときに、**入力**メソッドのインスタンスに渡されます、**データセット**と**DataTableMapping**名、その名前の割り当てが存在する場合はそれ以外を **。DataTable**名を使用するとします。  
  
 次の例では、作成、 **DataTableMapping**という名前の**顧客**と**DataTable**の名前**BizTalkSchema**します。 例では、SELECT ステートメントによって返される行をマップし、 **BizTalkSchema** **DataTable**します。  
  
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
>  列マップにソースの列名を指定しなかった場合、またはテーブル マップにソース テーブル名を指定しなかった場合は、自動的に既定の名前が生成されます。 列マッピングの基になる列が指定されていない場合、列マッピングが指定されたインクリメンタル既定名**SourceColumn** *N、* 以降**SourceColumn1**します。 テーブル マップにソース テーブル名が指定されていない場合、テーブル マッピングが指定されたインクリメンタル既定名**SourceTable** *N*以降の**SourceTable1**します。  
  
> [!NOTE]
>  名前付け規則を回避することをお勧めします**SourceColumn** *N*列マッピング、または**SourceTable** *N*テーブル。マッピングを指定した名前の既存の既定の列マッピング名と競合する可能性があるため、 **ColumnMappingCollection**またはテーブル マッピング名、 **DataTableMappingCollection**. 指定した名前が既に存在する場合は、例外がスローされます。  
  
## <a name="handling-multiple-result-sets"></a>複数の結果セットの処理  
 場合、 **SelectCommand**複数のテーブルを返します**入力**内のテーブルの増分値を持つテーブル名を自動的に生成、**データセット**以降のテーブルの名前と続行の形式で指定**TableName** *N*以降の**TableName1**します。 内のテーブルに指定名前に自動的に生成されたテーブル名をマップするテーブルのマッピングを使用することができます、**データセット**します。 たとえば、 **SelectCommand** 2 つのテーブルを返す**顧客**と**注文**、に対する次の呼び出しを発行**入力**します。  
  
```  
adapter.Fill(customersDataSet, "Customers")  
```  
  
 2 つのテーブルに作成されます、**データセット**:**顧客**と**Customers1**します。 テーブル マッピングを使用するには 2 つ目のテーブルの名前がいることを確認する**注文**の代わりに**Customers1**します。 これを行うには、マップのソース テーブル**Customers1**を**データセット**テーブル**注文**次の例のようにします。  
  
```  
adapter.TableMappings.Add("Customers1", "Orders")  
adapter.Fill(customersDataSet, "Customers")  
```  
  
## <a name="see-also"></a>関連項目

- [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
