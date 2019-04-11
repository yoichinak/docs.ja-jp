---
title: DataSet への既存の制約の追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 307d2809-208b-4cf8-b6a9-5d16f15fc16c
ms.openlocfilehash: 18c391e97baa170b78dcfe0165fb38b6c6d739f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210556"
---
# <a name="adding-existing-constraints-to-a-dataset"></a>DataSet への既存の制約の追加
**入力**のメソッド、 **DataAdapter**塗りつぶします、<xref:System.Data.DataSet>では、テーブルの列と、データ ソースからの行のみが制約は一般設定、データ ソースによって、 **の塗りつぶし**メソッドにこのスキーマ情報を追加できません、**データセット**既定。 設定する、**データセット**いずれかの呼び出しでは、データ ソースから既存の主キー制約情報できます、 **FillSchema**のメソッド、 **DataAdapter**、設定や、**MissingSchemaAction**のプロパティ、 **DataAdapter**に**AddWithKey**呼び出す前に**入力**します。 これにより、その主キー制約、**データセット**データ ソースに反映します。 外部キー制約情報が含まれていないのように、明示的に作成する必要があります[DataTable の制約](../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatable-constraints.md)します。  
  
 スキーマ情報を追加、**データセット**主キー制約に含まれているデータで塗りつぶすことにより、前に、<xref:System.Data.DataTable>内のオブジェクト、**データセット**します。 その結果、追加時に入力への呼び出し、**データセット**が終わったら、プライマリ キー列の情報がそれぞれ現在の行のデータ ソースから新しい行を一致させる**DataTable**と現在のデータをテーブルは、データ ソースのデータで上書きされます。 スキーマ情報がないデータ ソースからの新しい行の追加、**データセット**、重複する行の結果として得られる。  
  
> [!NOTE]
>  データ ソース内の列が自動インクリメントとして識別された場合、 **FillSchema**メソッド、または**入力**メソッドを**MissingSchemaAction**の**AddWithKey**、作成、 **DataColumn**で、 **AutoIncrement**プロパティに設定`true`します。 ただし、設定する必要がありますには、 **AutoIncrementStep**と**AutoIncrementSeed**値します。 自動インクリメント列の詳細については、次を参照してください。 [AutoIncrement 列の作成](../../../../docs/framework/data/adonet/dataset-datatable-dataview/creating-autoincrement-columns.md)です。  
  
 使用して**FillSchema**またはの設定、 **MissingSchemaAction**に**AddWithKey**主キー列情報を確認するデータ ソースで余分な処理が必要です。 この追加の処理によりパフォーマンスが低下する場合があります。 デザイン時に主キー情報がわかっている場合は、最適のパフォーマンスを得るために主キー列 (複数の場合もある) を明示的に指定することをお勧めします。 テーブルの主キーの情報を明示的に設定する方法については、次を参照してください。[主キーを定義する](../../../../docs/framework/data/adonet/dataset-datatable-dataview/defining-primary-keys.md)します。  
  
 次のコード例は、スキーマ情報を追加する方法を示しています、**データセット**を使用して**FillSchema**します。  
  
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
  
 次のコード例は、スキーマ情報を追加する方法を示しています、**データセット**を使用して、 **MissingSchemaAction.AddWithKey**のプロパティ、**入力**メソッド。  
  
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
 場合、 **DataAdapter**から返された複数の結果セットが発生した、 **SelectCommand**、複数のテーブルが作成されます、**データセット**します。 テーブルの 0 から始まるインクリメンタル既定名が与えられます**テーブル** *N*以降の**テーブル**したがって"Table0"ではなく。 テーブル名がへの引数として渡されたかどうか、 **FillSchema**メソッドでは、テーブルがあるの 0 から始まるインクリメンタル名**TableName** *N*以降の**TableName** "TableName0"ではなく。  
  
> [!NOTE]
>  場合、 **FillSchema**のメソッド、 **OleDbDataAdapter**オブジェクトが複数の結果セットを返すコマンドに対して呼び出されると、最初の結果セットからスキーマ情報のみが返されます。 設定した場合の複数の結果のスキーマ情報を返すを使用して、 **OleDbDataAdapter**を指定することをお勧め、 **MissingSchemaAction**の**AddWithKey**呼び出すときに、スキーマ情報を取得し、**入力**メソッド。  
  
## <a name="see-also"></a>関連項目

- [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [DataSet、DataTable、および DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
