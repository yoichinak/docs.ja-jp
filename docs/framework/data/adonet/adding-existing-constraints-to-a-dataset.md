---
title: DataSet への既存の制約の追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: db072692eba4044e854f25ff2c7f8c9960714018
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785115"
---
# <a name="adding-existing-constraints-to-a-dataset"></a>DataSet への既存の制約の追加
**DataAdapter**の<xref:System.Data.DataSet> **Fill**メソッドは、データソースのテーブルの列と行だけを格納します。制約は通常、データソースによって設定されますが、このスキーマ情報 **は Fill メソッドによって**既定ではデータセットです。 データソースからの既存の primary key 制約情報を**DataSet**に設定するには、 **dataadapter**の**FillSchema**メソッドを呼び出すか、 **dataadapter**の**MissingSchemaAction**プロパティを設定します。**Fill**を呼び出す前に、 **addwithkey**に設定します。 これにより、データ**セット**内の primary key 制約がデータソースの主キー制約を反映するようになります。 外部キー制約情報は含まれていません。 [DataTable 制約](./dataset-datatable-dataview/datatable-constraints.md)に示すように、明示的に作成する必要があります。  
  
 データを格納する前に、データ**セット**にスキーマ情報を追加することで、主キー <xref:System.Data.DataTable>制約が**dataset**のオブジェクトに含まれるようになります。 その結果、データ**セット**への追加の呼び出しが行われたときに、主キー列の情報が使用され、データソースからの新しい行と各**DataTable**の現在の行が一致します。テーブル内の現在のデータは、データソース。 スキーマ情報がない場合、データソースからの新しい行がデータ**セット**に追加され、行が重複します。  
  
> [!NOTE]
> データソース内の列が自動インクリメントとして識別された場合、 **FillSchema**メソッド、または**MissingSchemaAction**が**Addwithkey**である**Fill**メソッドによって、 **autoincrement**プロパティを持つ**DataColumn**が作成されます。をに`true`設定します。 ただし、 **AutoIncrementStep**と**AutoIncrementSeed**の値を自分で設定する必要があります。 自動インクリメント列の詳細については、「自動[インクリメント列の作成](./dataset-datatable-dataview/creating-autoincrement-columns.md)」を参照してください。  
  
 **FillSchema**を使用するか、 **MissingSchemaAction**を**addwithkey**に設定するには、主キー列の情報を決定するためにデータソースで追加の処理が必要です。 この追加の処理によりパフォーマンスが低下する場合があります。 デザイン時に主キー情報がわかっている場合は、最適のパフォーマンスを得るために主キー列 (複数の場合もある) を明示的に指定することをお勧めします。 テーブルの主キー情報を明示的に設定する方法については、「[主キーの定義](./dataset-datatable-dataview/defining-primary-keys.md)」を参照してください。  
  
 次のコード例では、 **FillSchema**を使用して**データセット**にスキーマ情報を追加する方法を示します。  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers")  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.FillSchema(custDataSet, SchemaType.Source, "Customers");  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
 次のコード例では、 **Fill**メソッドの**MissingSchemaAction**プロパティを使用して、**データセット**にスキーマ情報を追加する方法を示します。  
  
```vb  
Dim custDataSet As DataSet = New DataSet()  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
custAdapter.Fill(custDataSet, "Customers")  
```  
  
```csharp  
DataSet custDataSet = new DataSet();  
  
custAdapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
custAdapter.Fill(custDataSet, "Customers");  
```  
  
## <a name="handling-multiple-result-sets"></a>複数の結果セットの処理  
 データ**アダプター**が**SelectCommand**から返された複数の結果セットを検出すると、**データセット**内に複数のテーブルが作成されます。 テーブルには、インデックス番号が0から始まる既定の**テーブル** *N*が割り当てられます。この名前は、"Table0" の代わりに**table**で始まります。 テーブル名が**FillSchema**メソッドに引数として渡された場合、テーブルには、"TableName0" ではなく**Tablename**で始まる**tablename** *N*の0から始まる増分名が割り当てられます。  
  
> [!NOTE]
> 複数の結果セットを返すコマンドに対して**OleDbDataAdapter**オブジェクトの**FillSchema**メソッドを呼び出すと、最初の結果セットのスキーマ情報のみが返されます。 **OleDbDataAdapter**を使用して複数の結果セットのスキーマ情報を返す場合は、 **addwithkey**の**MissingSchemaAction**を指定し、 **Fill**を呼び出すときにスキーマ情報を取得することをお勧めします。b.  
  
## <a name="see-also"></a>関連項目

- [DataAdapter と DataReader](dataadapters-and-datareaders.md)
- [DataSet、DataTable、および DataView](./dataset-datatable-dataview/index.md)
- [ADO.NET でのデータの取得および変更](retrieving-and-modifying-data.md)
- [ADO.NET の概要](ado-net-overview.md)
