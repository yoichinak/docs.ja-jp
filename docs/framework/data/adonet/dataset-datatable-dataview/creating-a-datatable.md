---
title: DataTable の作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: eecf9d78-60e3-4fdc-8de0-e56c13a89414
ms.openlocfilehash: 64ba7a8e6bd6361e14d1f16576e377575b088bbe
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205142"
---
# <a name="creating-a-datatable"></a>DataTable の作成
<xref:System.Data.DataTable> は 1 つのインメモリ リレーショナル データのテーブルを表します。DataTable は単独で作成および使用することも、他の .NET Framework オブジェクトから <xref:System.Data.DataSet> のメンバーとして使用することもできます。  
  
 **Datatable**オブジェクトを作成するには、適切な**datatable**コンストラクターを使用します。 これを**DataSet**に追加するには、 **add**メソッドを使用してそれを**DataTable**オブジェクトの**Tables**コレクションに追加します。  
  
 **データセット**内に**DataTable**オブジェクトを作成するには、 **DataAdapter**オブジェクトの**Fill**メソッドまたは**FillSchema**メソッドを使用するか、または、 **ReadXml**, readxmlschema を使用して、定義済みまたは推論された XML スキーマから作成することもできます。**データセット**の、、または**InferXmlSchema**メソッド。 DataTable を1つの**データセット**の**tables**コレクションのメンバーとして追加した後は、その**DataTable**を他の**データセット**のテーブルのコレクションに追加することはできないことに注意してください。  
  
 最初に**DataTable**を作成するときには、スキーマ (つまり構造体) はありません。 テーブルのスキーマを定義するには、テーブルの**Columns**コレクション<xref:System.Data.DataColumn>にオブジェクトを作成し、追加する必要があります。 テーブルの主キー列を定義し、テーブルの**制約**コレクションに**制約**オブジェクトを作成して追加することもできます。 **DataTable**のスキーマを定義した後は、 **DataRow**オブジェクトをテーブルの**rows**コレクションに追加することによって、データ行をテーブルに追加できます。  
  
 <xref:System.Data.DataTable.TableName%2A> **DataTable**を作成するときにプロパティの値を指定する必要はありません。プロパティを別の時点で指定することも、空のままにすることもできます。 ただし、 **TableName**値を持たないテーブルを**データセット**に追加すると、テーブルには、Table0 の "Table" で始まるテーブル*N*の増分既定の名前が与えられます。  
  
> [!NOTE]
> **TableName**値を指定するときは、"Table*N*" という名前付け規則を使用しないことをお勧めします。これは、指定した名前が**データセット**内の既存の既定のテーブル名と競合する可能性があるためです。 指定した名前が既に存在する場合は、例外がスローされます。  
  
 次の例では、 **DataTable**オブジェクトのインスタンスを作成し、"Customers" という名前を割り当てます。  
  
```vb  
Dim workTable as DataTable = New DataTable("Customers")  
```  
  
```csharp  
DataTable workTable = new DataTable("Customers");  
```  
  
 次の例では、**データセット**の**Tables**コレクションに追加することによって、 **DataTable**のインスタンスを作成します。  
  
```vb  
Dim customers As DataSet = New DataSet  
Dim customersTable As DataTable = _  
   customers.Tables.Add("CustomersTable")  
```  
  
```csharp  
DataSet customers = new DataSet();  
DataTable customersTable = customers.Tables.Add("CustomersTable");  
```  
  
## <a name="see-also"></a>関連項目

- <xref:System.Data.DataTable>
- <xref:System.Data.DataTableCollection>
- [DataTables](datatables.md)
- [DataAdapter からの DataSet の読み込み](../populating-a-dataset-from-a-dataadapter.md)
- [XML からの DataSet の読み込み](loading-a-dataset-from-xml.md)
- [XML の DataSet スキーマ情報の読み込み](loading-dataset-schema-information-from-xml.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
