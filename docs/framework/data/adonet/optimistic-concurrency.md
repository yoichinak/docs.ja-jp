---
title: オプティミスティック コンカレンシー
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e380edac-da67-4276-80a5-b64decae4947
ms.openlocfilehash: f2fc69867ae1659a342161b00dfd91852441fa5b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59126218"
---
# <a name="optimistic-concurrency"></a>オプティミスティック コンカレンシー
マルチユーザー環境には、データベースのデータを更新するための 2 つのモデルがあります。オプティミスティック コンカレンシーとペシミスティック コンカレンシーです。 <xref:System.Data.DataSet> オブジェクトは、データをリモート処理するときや、データと対話するときのように長時間にわたる利用状況では、オプティミスティック コンカレンシーの使用を奨励するように設計されています。  
  
 ペシミスティック同時実行制御では、他のユーザーが現在のユーザーに影響を与えるようなデータ変更を実行するのを防ぐために、データ ソースで行をロックする必要があります。 ペシミスティック モデルでは、あるユーザーがロックの適用される操作を実行すると、他のユーザーは、ロックが解除されるまで、競合する操作を実行できません。 このモデルは、同時実行の競合が発生するときに、トランザクションをロールバックするよりもデータをロックで保護する方が低コストに抑えられるため、データの競合が多い環境で主に使用されます。  
  
 したがって、ペシミスティック コンカレンシー モデルでは、行を更新するユーザーがロックを設定します。 更新を終了してロックを解除するまでは、他のユーザーはその行を変更できません。 そのため、ペシミスティック同時実行制御は、レコードをプログラムで処理する場合のようにロック時間が短いときの実装に適しています。 ペシミスティック同時実行制御は、ユーザーがデータと対話していてレコードが比較的長時間ロックされる場合には適していません。  
  
> [!NOTE]
>  同じ操作で複数の行を更新する必要がある場合は、ペシミスティック同時実行制御でロックするよりも、トランザクションを作成する方が有効です。  
  
 これに対して、オプティミスティック コンカレンシーを使用するユーザーは、行を読み取るときに行をロックしません。 ユーザーが行を更新するときは、行の読み取り後に別のユーザーがその行を変更したかどうかをアプリケーションで確認する必要があります。 オプティミスティック同時実行制御は、一般に、データの競合が少ない環境で使用されます。 オプティミスティック同時実行制御を使用すると、レコードをロックする必要がないためパフォーマンスが向上します。レコードをロックするには、サーバー リソースを追加する必要があります。 また、レコードのロックを管理するためにデータベース サーバーに永続的に接続している必要があります。 オプティミスティック同時実行制御モデルでは、サーバーとの接続が固定していないため、より短い時間で多数のクライアントを扱うことができます。  
  
 オプティミスティック コンカレンシー モデルでは、ユーザーがデータベースから値を受け取った後、その値を変更する前に別のユーザーがその値を変更した場合に、違反が発生したと見なされます。 サーバーがコンカレンシー違反を解決する方法がよくわかる例を次に示します。  
  
 オプティミスティック同時実行制御の例を次の表に示します。  
  
 午後 1 時に、User1 が、次の値を持つデータベースから行を読み取ります。  
  
 **CustID LastName FirstName**  
  
 101          Smith             Bob  
  
|列名|元の値|現在の値|データベース内の値|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Bob|Bob|  
  
 午後 1 時 1 分に、User2 が同じ行を読み取ります。  
  
 User2 の変更、午後 1時 03分**FirstName** "Robert"には、"Bob"から、データベースを更新します。  
  
|列名|元の値|現在の値|データベース内の値|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|Robert|Bob|  
  
 更新時のデータベース内の値は User2 が持つ元の値と一致しているため、更新は成功します。  
  
 午後 1 時 5 分に、User1 が "Bob" の名を "James" に変更し、行の更新を試みます。  
  
|列名|元の値|現在の値|データベース内の値|  
|-----------------|--------------------|-------------------|-----------------------|  
|CustID|101|101|101|  
|LastName|Smith|Smith|Smith|  
|FirstName|Bob|James|Robert|  
  
 この時点で、データベース内の値 ("Robert") は User1 が期待していた元の値 ("Bob") と一致していないため、User1 による更新はオプティミスティック同時実行制御違反となります。 コンカレンシー違反は、更新が失敗したことを通知するだけです。 ここで、User2 による変更を User1 による変更で上書きするか、または User1 による変更をキャンセルするかの決定が必要になります。  
  
## <a name="testing-for-optimistic-concurrency-violations"></a>オプティミスティック コンカレンシー違反テスト  
 オプティミスティック同時実行制御違反をテストするには、いくつか方法があります。 1 つは、テーブルにタイムスタンプ列を含める方法です。 一般に、データベースには、レコードを最後に更新した日付と時刻を識別するために使用するタイムスタンプ機能が用意されています。 この機能を使用すると、timestamp 列がテーブル定義に組み込まれます。 レコードが更新されると、タイムスタンプが更新されて現在の日付と時刻が反映されます。 オプティミスティック同時実行制御違反テストでは、テーブル内容についてのクエリによって timestamp 列が返されます。 更新しようとすると、データベースのタイムスタンプ値と、変更行に格納されている元のタイムスタンプ値が比較されます。 一致した場合、更新が実行され、timestamp 列が現在の時刻に更新されてその更新が反映されます。 一致しなかった場合は、オプティミスティック同時実行制御違反が発生します。  
  
 オプティミスティック コンカレンシー違反をテストするためのもう 1 つの方法は、行のすべての列の元の値が、データベース内の値とまだ一致しているかどうかを検証することです。 たとえば、次のクエリを見てみましょう。  
  
```  
SELECT Col1, Col2, Col3 FROM Table1  
```  
  
 内の行を更新するときに、オプティミスティック同時実行制御違反をテストする**Table1**、次の UPDATE ステートメントを実行します。  
  
```  
UPDATE Table1 Set Col1 = @NewCol1Value,  
              Set Col2 = @NewCol2Value,  
              Set Col3 = @NewCol3Value  
WHERE Col1 = @OldCol1Value AND  
      Col2 = @OldCol2Value AND  
      Col3 = @OldCol3Value  
```  
  
 元の値がデータベース内の値と一致する間は、更新が実行されます。 値が変更された場合は、WHERE 句の条件と一致する行を見つけることができないため更新できません。  
  
 クエリで、常に一意の主キー値を返すことをお勧めします。 一意の主キーを返さないと、UPDATE ステートメントによって複数の行が更新されることがあり、意図に反した結果となります。  
  
 データ ソースの列で null が使用できる場合は、ローカル テーブルおよびデータ ソースで一致する null 参照がないかどうかをチェックするように WHERE 句を拡張する必要があります。 たとえば、次の UPDATE ステートメントは、ローカル行の null 参照がデータ ソースの null 参照とまだ一致しているかどうか、つまり、ローカル行の値がデータ ソースの値とまだ一致しているかどうかをチェックします。  
  
```  
UPDATE Table1 Set Col1 = @NewVal1  
  WHERE (@OldVal1 IS NULL AND Col1 IS NULL) OR Col1 = @OldVal1  
```  
  
 オプティミスティック コンカレンシー モデルを使用するときは、より制限の少ない抽出条件を適用するように選択することもできます。 たとえば、WHERE 句で主キー列だけを使用すると、前回のクエリ実行後に主キー以外の列が更新されたかどうかに関係なく、データが上書きされます。 WHERE 句を特定の列だけに適用することもできます。特定の列だけに WHERE 句を適用した場合は、特定のフィールドが前回のクエリ実行後に更新されていない限りデータが上書きされます。  
  
### <a name="the-dataadapterrowupdated-event"></a>DataAdapter.RowUpdated イベント  
 **RowUpdated**のイベント、<xref:System.Data.Common.DataAdapter>オブジェクトは、オプティミスティック同時実行制御違反のアプリケーションに通知を提供する前に説明した手法と組み合わせて使用できます。 **RowUpdated**を更新するには、各再試行の後に発生、 **Modified**から行を**データセット**します。 これにより、例外発生時の処理、カスタム エラー情報の追加、再試行ロジックの追加などの特別の処理コードを追加できます。 <xref:System.Data.Common.RowUpdatedEventArgs>オブジェクトを返します、 **RecordsAffected**プロパティ テーブルで変更された行の特定の更新コマンドによって影響を受ける行の数を格納します。 オプティミスティック同時実行性をテストする更新コマンドを設定して、 **RecordsAffected**プロパティは、その結果の値を返す 0、オプティミスティック同時実行制御違反が発生したときにレコードが更新されないためです。 この場合、例外がスローされます。 **RowUpdated**イベントを使用すると、この状況の発生を処理し、適切な設定によって、例外を回避**RowUpdatedEventArgs.Status**などの値**UpdateStatus.SkipCurrentRow**します。 詳細については、 **RowUpdated**イベントを参照してください[DataAdapter イベントの処理](../../../../docs/framework/data/adonet/handling-dataadapter-events.md)します。  
  
 必要に応じて、設定することができます**DataAdapter.ContinueUpdateOnError**に**true**を呼び出す前に**Update**、に格納されているエラー情報および応答する**RowError**行の場合に、特定のプロパティ、 **Update**が完了します。 詳細については、次を参照してください。[行エラー情報](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)します。  
  
## <a name="optimistic-concurrency-example"></a>オプティミスティック コンカレンシーの例  
 設定する単純な例を次に、 **UpdateCommand**の**DataAdapter**をオプティミスティック同時実行性、テストし、使用して、 **RowUpdated**をテストするためのイベントオプティミスティック同時実行制御違反。 アプリケーションは、オプティミスティック同時実行制御違反が発生した場合に、設定、 **RowError**オプティミスティック同時実行制御違反を反映するように、更新が実行されている行のできます。  
  
 UPDATE コマンドの WHERE 句に渡されるパラメーターの値にマップされますが、**元**それぞれの列の値。  
  
```vb  
' Assumes connection is a valid SqlConnection.  
Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID", _  
  connection)  
  
' The Update command checks for optimistic concurrency violations  
' in the WHERE clause.  
adapter.UpdateCommand = New SqlCommand("UPDATE Customers " &  
  "(CustomerID, CompanyName) VALUES(@CustomerID, @CompanyName) " & _  
  "WHERE CustomerID = @oldCustomerID AND CompanyName = " &  
  "@oldCompanyName", connection)  
adapter.UpdateCommand.Parameters.Add( _  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
adapter.UpdateCommand.Parameters.Add( _  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
  
' Pass the original values to the WHERE clause parameters.  
Dim parameter As SqlParameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
parameter.SourceVersion = DataRowVersion.Original  
parameter = adapter.UpdateCommand.Parameters.Add( _  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName")  
parameter.SourceVersion = DataRowVersion.Original  
  
' Add the RowUpdated event handler.  
AddHandler adapter.RowUpdated, New SqlRowUpdatedEventHandler( _  
  AddressOf OnRowUpdated)  
  
Dim dataSet As DataSet = New DataSet()  
adapter.Fill(dataSet, "Customers")  
  
' Modify the DataSet contents.  
adapter.Update(dataSet, "Customers")  
  
Dim dataRow As DataRow  
  
For Each dataRow In dataSet.Tables("Customers").Rows  
    If dataRow.HasErrors Then   
       Console.WriteLine(dataRow (0) & vbCrLf & dataRow.RowError)  
    End If  
Next  
  
Private Shared Sub OnRowUpdated( _  
  sender As object, args As SqlRowUpdatedEventArgs)  
   If args.RecordsAffected = 0  
      args.Row.RowError = "Optimistic Concurrency Violation!"  
      args.Status = UpdateStatus.SkipCurrentRow  
   End If  
End Sub  
```  
  
```csharp  
// Assumes connection is a valid SqlConnection.  
SqlDataAdapter adapter = new SqlDataAdapter(  
  "SELECT CustomerID, CompanyName FROM Customers ORDER BY CustomerID",  
  connection);  
  
// The Update command checks for optimistic concurrency violations  
// in the WHERE clause.  
adapter.UpdateCommand = new SqlCommand("UPDATE Customers Set CustomerID = @CustomerID, CompanyName = @CompanyName " +  
   "WHERE CustomerID = @oldCustomerID AND CompanyName = @oldCompanyName", connection);  
adapter.UpdateCommand.Parameters.Add(  
  "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
adapter.UpdateCommand.Parameters.Add(  
  "@CompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
  
// Pass the original values to the WHERE clause parameters.  
SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
parameter.SourceVersion = DataRowVersion.Original;  
parameter = adapter.UpdateCommand.Parameters.Add(  
  "@oldCompanyName", SqlDbType.NVarChar, 30, "CompanyName");  
parameter.SourceVersion = DataRowVersion.Original;  
  
// Add the RowUpdated event handler.  
adapter.RowUpdated += new SqlRowUpdatedEventHandler(OnRowUpdated);  
  
DataSet dataSet = new DataSet();  
adapter.Fill(dataSet, "Customers");  
  
// Modify the DataSet contents.  
  
adapter.Update(dataSet, "Customers");  
  
foreach (DataRow dataRow in dataSet.Tables["Customers"].Rows)  
{  
    if (dataRow.HasErrors)  
       Console.WriteLine(dataRow [0] + "\n" + dataRow.RowError);  
}  
  
protected static void OnRowUpdated(object sender, SqlRowUpdatedEventArgs args)  
{  
  if (args.RecordsAffected == 0)   
  {  
    args.Row.RowError = "Optimistic Concurrency Violation Encountered";  
    args.Status = UpdateStatus.SkipCurrentRow;  
  }  
}  
```  
  
## <a name="see-also"></a>関連項目

- [ADO.NET でのデータの取得および変更](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
- [DataAdapter によるデータ ソースの更新](../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [行エラー情報](../../../../docs/framework/data/adonet/dataset-datatable-dataview/row-error-information.md)
- [トランザクションと同時実行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
