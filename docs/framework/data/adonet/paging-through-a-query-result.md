---
title: クエリ結果のページング
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fa360c46-e5f8-411e-a711-46997771133d
ms.openlocfilehash: 023efcc15d7080afc1583f4ad8984e152b86cf23
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140323"
---
# <a name="paging-through-a-query-result"></a>クエリ結果のページング
クエリ結果のページングとは、クエリ結果をデータの小さなサブセット、つまりページに分けて返すプロセスです。 クエリ結果のページングは、結果を管理しやすい小さな単位でユーザーに表示するために行われる一般的な処理です。  
  
 **DataAdapter**のオーバー ロードによって、データのページのみを返す機能が提供、**入力**メソッド。 ただし、このできない可能性がありますので、大規模なクエリ結果のページングの最適な選択肢ですが、 **DataAdapter**ターゲットを塗りつぶします<xref:System.Data.DataTable>または<xref:System.Data.DataSet>のみ、要求されたレコードを返すリソースで、クエリ全体は引き続き使用されます。 クエリ全体を返す必要があるリソースを使用せずにデータ ソースから 1 ページ分のデータを返すには、必要な行だけ返すように限定する抽出条件をクエリに追加します。  
  
 使用する、**入力**、データのページを返す方法を指定する、 **startRecord**パラメーター、データのページの最初のレコードと**maxRecords**パラメーターの数データのページのレコード。  
  
 次のコード例を使用する方法を示しています、**入力**ページ サイズが 5 つのレコードをクエリ結果の最初のページを返します。  
  
```vb  
Dim currentIndex As Integer = 0  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT * FROM dbo.Orders ORDER BY OrderID"  
' Assumes that connection is a valid SqlConnection object.  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
int currentIndex = 0;  
int pageSize = 5;  
  
string orderSQL = "SELECT * FROM Orders ORDER BY OrderID";  
// Assumes that connection is a valid SqlConnection object.  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 前の例では、**データセット**だけが 5 つのレコードが全体に格納されます**注文**テーブルが返されます。 入力する、**データセット**それら同じ 5 つのレコードが、5 つのレコードだけを返すと、TOP を使用して、次のコード例のように、SQL ステートメントの WHERE 句。  
  
```vb  
Dim pageSize As Integer = 5  
  
Dim orderSQL As String = "SELECT TOP " & pageSize & _  
  " * FROM Orders ORDER BY OrderID"  
Dim adapter As SqlDataAdapter = _  
  New SqlDataAdapter(orderSQL, connection)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Orders")   
```  
  
```csharp  
int pageSize = 5;  
  
string orderSQL = "SELECT TOP " + pageSize +   
  " * FROM Orders ORDER BY OrderID";  
SqlDataAdapter adapter = new SqlDataAdapter(orderSQL, connection);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Orders");  
```  
  
 この方法でクエリ結果をページングするときは、次のレコード ページを返すコマンドに一意の ID を渡すために、行を順序付けする固有の識別子を保存する必要があります。次のコード サンプルで示します。  
  
```vb  
Dim lastRecord As String = _  
  dataSet.Tables("Orders").Rows(pageSize - 1)("OrderID").ToString()  
```  
  
```csharp  
string lastRecord =   
  dataSet.Tables["Orders"].Rows[pageSize - 1]["OrderID"].ToString();  
```  
  
 オーバー ロードを使用してレコードの次のページを返す、**入力**を受け取るメソッド、 **startRecord**と**maxRecords**パラメーターによって、現在のレコード インデックスをインクリメントします。ページ サイズと塗りつぶしテーブル。 レコードの 1 つだけのページが追加された場合でも、データベース サーバーで全体のクエリ結果を返すことに注意してください、**データセット**します。 次のデータ ページを格納する前にテーブル行をクリアするコード サンプルを次に示します。 データベース サーバーとのやり取りを減らすために、ローカルのキャッシュに、返された一定数の行を保存することもできます。  
  
```vb  
currentIndex = currentIndex + pageSize  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders")  
```  
  
```csharp  
currentIndex += pageSize;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, currentIndex, pageSize, "Orders");  
```  
  
 データベース サーバーによってクエリ全体を返さずに次のレコード ページを返すには、SELECT ステートメントに限定的な抽出条件を指定します。 上の例では最後に返されたレコードが保存されますが、次のコード サンプルに示すようにそのレコードを WHERE 句で使用するとクエリの開始点を指定できます。  
  
```vb  
orderSQL = "SELECT TOP " & pageSize & _  
  " * FROM Orders WHERE OrderID > " & lastRecord & " ORDER BY OrderID"  
adapter.SelectCommand.CommandText = orderSQL  
  
dataSet.Tables("Orders").Rows.Clear()  
  
adapter.Fill(dataSet, "Orders")  
```  
  
```csharp  
orderSQL = "SELECT TOP " + pageSize +   
  " * FROM Orders WHERE OrderID > " + lastRecord + " ORDER BY OrderID";  
adapter.SelectCommand.CommandText = orderSQL;  
  
dataSet.Tables["Orders"].Rows.Clear();  
  
adapter.Fill(dataSet, "Orders");  
```  
  
## <a name="see-also"></a>関連項目

- [DataAdapter と DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
