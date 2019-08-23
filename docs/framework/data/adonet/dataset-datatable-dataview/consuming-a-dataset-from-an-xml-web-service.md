---
title: XML Web サービスからの DataSet の使用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: acf5af755d6322f75a616005cc904d464564bc81
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915829"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>XML Web サービスからの DataSet の使用
<xref:System.Data.DataSet> は、非接続型デザインで設計されています。インターネットで簡単にデータを転送するのが目的の一部です。 **データセット**は xml web サービスからの入力または出力として指定できることを示す "serializable" です。 xml web サービスからクライアントおよびクライアントに**データセット**の内容をストリームするために必要な追加のコーディングは必要ありません。 **データセット**は、DiffGram 形式を使用して xml ストリームに暗黙的に変換され、ネットワーク経由で送信された後、受信側の**データセット**として xml ストリームから再構築されます。 これにより、XML Web サービスを使用してリレーショナル データを送信および返送する、たいへん簡単で柔軟性のある方法が提供されます。 DiffGram 形式の詳細については、「diffgram[グラム](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)」を参照してください。  
  
 次の例では、データ**セット**を使用してリレーショナルデータ (変更されたデータを含む) を転送し、更新内容を元のデータソースに解決する XML Web サービスとクライアントを作成する方法を示します。  
  
> [!NOTE]
> XML Web サービスを作成する場合は、常にセキュリティへの影響を考慮することをお勧めします。 XML Web サービスのセキュリティ保護の詳細については、「 [ASP.NET を使用して作成された Xml Web サービスのセキュリティ保護](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))」を参照してください。  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>DataSet を返し、処理する XML Web サービスを作成するには、次のようにします。  
  
1. XML Web サービスを作成します。  
  
     この例では、データを返す XML Web サービスが作成されます。この例では、 **Northwind**データベースから顧客の一覧を取得し、データの更新を含むデータ**セット**を受け取ります。このデータは、xml web サービスによって元のデータソースに解決されます。  
  
     XML Web サービスは、次の2つのメソッドを公開します。データソースへの更新を解決するために、顧客の一覧と**UpdateCustomers**を返す**getcustomers**。 この XML Web サービスは、Web サーバー上の DataSetSample.asmx というファイルに格納されます。 次のコードは、DataSetSample.asmx の内容の概要を示しています。  
  
    ```vb  
    <% @ WebService Language = "vb" Class = "Sample" %>  
    Imports System  
    Imports System.Data  
    Imports System.Data.SqlClient  
    Imports System.Web.Services  
  
    <WebService(Namespace:="http://microsoft.com/webservices/")> _  
    Public Class Sample  
  
    Public connection As SqlConnection = New SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind")  
  
      <WebMethod( Description := "Returns Northwind Customers", EnableSession := False )> _  
      Public Function GetCustomers() As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter( _  
          "SELECT CustomerID, CompanyName FROM Customers", connection)  
  
        Dim custDS As DataSet = New DataSet()  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey  
        adapter.Fill(custDS, "Customers")  
  
        Return custDS  
      End Function  
  
      <WebMethod( Description := "Updates Northwind Customers", EnableSession := False )> _  
      Public Function UpdateCustomers(custDS As DataSet) As DataSet  
        Dim adapter As SqlDataAdapter = New SqlDataAdapter()  
  
        adapter.InsertCommand = New SqlCommand( _  
          "INSERT INTO Customers (CustomerID, CompanyName) " & _  
          "Values(@CustomerID, @CompanyName)", connection)  
        adapter.InsertCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.InsertCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        adapter.UpdateCommand = New SqlCommand( _  
          "UPDATE Customers Set CustomerID = @CustomerID, " & _  
          "CompanyName = @CompanyName WHERE CustomerID = " & _  
          @OldCustomerID", connection)  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        adapter.UpdateCommand.Parameters.Add( _  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName")  
  
        Dim parameter As SqlParameter = _  
          adapter.UpdateCommand.Parameters.Add( _  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.DeleteCommand = New SqlCommand( _  
          "DELETE FROM Customers WHERE CustomerID = @CustomerID", _  
          connection)  
        parameter = adapter.DeleteCommand.Parameters.Add( _  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID")  
        parameter.SourceVersion = DataRowVersion.Original  
  
        adapter.Update(custDS, "Customers")  
  
        Return custDS  
      End Function  
    End Class  
    ```  
  
    ```csharp  
    <% @ WebService Language = "C#" Class = "Sample" %>  
    using System;  
    using System.Data;  
    using System.Data.SqlClient;  
    using System.Web.Services;  
  
    [WebService(Namespace="http://microsoft.com/webservices/")]  
    public class Sample  
    {  
      public SqlConnection connection = new SqlConnection("Data Source=(local);Integrated Security=SSPI;Initial Catalog=Northwind");  
  
      [WebMethod( Description = "Returns Northwind Customers", EnableSession = false )]  
      public DataSet GetCustomers()  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter(  
          "SELECT CustomerID, CompanyName FROM Customers", connection);  
  
        DataSet custDS = new DataSet();  
        adapter.MissingSchemaAction = MissingSchemaAction.AddWithKey;  
        adapter.Fill(custDS, "Customers");  
  
        return custDS;  
      }  
  
      [WebMethod( Description = "Updates Northwind Customers",  
        EnableSession = false )]  
      public DataSet UpdateCustomers(DataSet custDS)  
      {  
        SqlDataAdapter adapter = new SqlDataAdapter();  
  
        adapter.InsertCommand = new SqlCommand(  
          "INSERT INTO Customers (CustomerID, CompanyName) " +  
          "Values(@CustomerID, @CompanyName)", connection);  
        adapter.InsertCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.InsertCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
  
        adapter.UpdateCommand = new SqlCommand(  
          "UPDATE Customers Set CustomerID = @CustomerID, " +  
          "CompanyName = @CompanyName WHERE CustomerID = " +  
          "@OldCustomerID", connection);  
        adapter.UpdateCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        adapter.UpdateCommand.Parameters.Add(  
          "@CompanyName", SqlDbType.NChar, 15, "CompanyName");  
        SqlParameter parameter = adapter.UpdateCommand.Parameters.Add(  
          "@OldCustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.DeleteCommand = new SqlCommand(  
        "DELETE FROM Customers WHERE CustomerID = @CustomerID",  
         connection);  
        parameter = adapter.DeleteCommand.Parameters.Add(  
          "@CustomerID", SqlDbType.NChar, 5, "CustomerID");  
        parameter.SourceVersion = DataRowVersion.Original;  
  
        adapter.Update(custDS, "Customers");  
  
        return custDS;  
      }  
    }  
    ```  
  
     一般的なシナリオでは、オプティミスティック同時実行制御違反をキャッチするために**UpdateCustomers**メソッドが記述されます。 説明を簡単にするために、この例では UpdateCustmoers メソッドを省略しています。 オプティミスティック同時実行制御の詳細については、「[オプティミスティック同時実行制御](../../../../../docs/framework/data/adonet/optimistic-concurrency.md)」を参照してください。  
  
2. XML Web サービス プロキシを作成します。  
  
     XML Web サービスのクライアントは、公開されたメソッドを使用するために SOAP プロキシを必要とします。 このプロキシは、Visual Studio を使用して生成することができます。 Visual Studio から既存の Web サービスへの Web 参照を設定することにより、この手順で説明されているすべての動作が自動的に実行されます。 プロキシ クラスを手動で作成する場合は、後述の手順を参照してください。 ほとんどの場合、Visual Studio による、クライアント アプリケーションのプロキシ クラスの作成で十分です。  
  
     プロキシは、Web サービス記述言語ツールを使用して作成できます。 たとえば、XML Web サービスが URL `http://myserver/data/DataSetSample.asmx`で公開されている場合は、次のようなコマンドを発行して、 **WebData**の名前空間を持つ Visual Basic .net プロキシを作成し、ファイルサンプルに格納します。  
  
    ```console
    wsdl /l:VB -out:sample.vb http://myserver/data/DataSetSample.asmx /n:WebData.DSSample  
    ```  
  
     ファイル sample.cs に C# プロキシを作成するには、次のコマンドを実行します。  
  
    ```console
    wsdl -l:CS -out:sample.cs http://myserver/data/DataSetSample.asmx -n:WebData.DSSample  
    ```  
  
     その後、プロキシをライブラリとしてコンパイルし、XML Web サービスのクライアントにインポートします。 sample.vb に格納されている Visual Basic .NET プロキシ コードを sample.dll としてコンパイルするには次のコマンドを実行します。  
  
    ```console  
    vbc -t:library -out:sample.dll sample.vb -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
     sample.cs に格納されている C# プロキシ コードを sample.dll としてコンパイルするには次のコマンドを実行します。  
  
    ```console
    csc -t:library -out:sample.dll sample.cs -r:System.dll -r:System.Web.Services.dll -r:System.Data.dll -r:System.Xml.dll  
    ```  
  
3. XML Web サービスのクライアントを作成します。  
  
     Visual Studio で Web サービスプロキシクラスを生成する場合は、単にクライアントプロジェクトを作成し、ソリューションエクスプローラー ウィンドウでプロジェクトを右クリックし、 **Web 参照の追加** をクリックして、使用可能な web の一覧から web サービスを選択します。サービス (web サービスが現在のソリューション内または現在のコンピューターで使用できない場合、Web サービスエンドポイントのアドレスの指定が必要になることがあります)。上記の手順に従って、XML Web サービス プロキシを作成した場合は、それをクライアント コードにインポートし、XML Web サービスのメソッドを処理できます。 次のサンプルコードは、プロキシライブラリをインポートし、 **Getcustomers**を呼び出して顧客の一覧を取得し、新しい顧客を追加して、更新された**データセット**を**UpdateCustomers**に返します。  
  
     この例では、GetChanges によって返される**データセット**を**UpdateCustomers**に渡しています **。** これは、変更された行のみが**UpdateCustomers**に渡される必要があるためです。 **UpdateCustomers**は解決された**データセット**を返します。このデータセットを既存の**データセット**に**マージ**して、解決された変更と行のエラー情報を更新に組み込むことができます。 次のコードは、Visual Studio を使用して Web 参照を作成し、 **[Web 参照の追加]** ダイアログボックスで dssample への web 参照の名前を変更したことを前提としています。  
  
    ```vb  
    Imports System  
    Imports System.Data  
  
    Public Class Client  
  
      Public Shared Sub Main()  
        Dim proxySample As New DsSample.Sample ()  ' Proxy object.  
        Dim customersDataSet As DataSet = proxySample.GetCustomers()  
        Dim customersTable As DataTable = _  
          customersDataSet.Tables("Customers")  
  
        Dim rowAs DataRow = customersTable.NewRow()  
        row("CustomerID") = "ABCDE"  
        row("CompanyName") = "New Company Name"  
        customersTable.Rows.Add(row)  
  
        Dim updateDataSet As DataSet = _  
          proxySample.UpdateCustomers(customersDataSet.GetChanges())  
  
        customersDataSet.Merge(updateDataSet)  
        customersDataSet.AcceptChanges()  
      End Sub  
    End Class  
    ```  
  
    ```csharp  
    using System;  
    using System.Data;  
  
    public class Client  
    {  
      public static void Main()  
      {  
        Sample proxySample = new DsSample.Sample();  // Proxy object.  
        DataSet customersDataSet = proxySample.GetCustomers();  
        DataTable customersTable = customersDataSet.Tables["Customers"];  
  
        DataRow row = customersTable.NewRow();  
        row["CustomerID"] = "ABCDE";  
        row["CompanyName"] = "New Company Name";  
        customersTable.Rows.Add(row);  
  
        DataSet updateDataSet = new DataSet();  
  
        updateDataSet =   
          proxySample.UpdateCustomers(customersDataSet.GetChanges());  
  
        customersDataSet.Merge(updateDataSet);  
        customersDataSet.AcceptChanges();  
      }  
    }  
    ```  
  
     プロキシ クラスを手動で作成する場合は、次の手順に従ってください。 このサンプルをコンパイルするには、作成したプロキシ ライブラリ (sample.dll) および関連する .NET ライブラリを指定します。 ファイル client.vb に格納されている Visual Basic .NET バージョンのサンプルをコンパイルするには次のコマンドを実行します。  
  
    ```console
    vbc client.vb -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
     ファイル client.cs に格納されている C# バージョンのサンプルをコンパイルするには、次のコマンドを実行します。  
  
    ```console
    csc client.cs -r:sample.dll -r:System.dll -r:System.Data.dll -r:System.Xml.dll -r:System.Web.Services.dll  
    ```  
  
## <a name="see-also"></a>関連項目

- [ADO.NET](../../../../../docs/framework/data/adonet/index.md)
- [DataSet、DataTable、および DataView](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)
- [DataTables](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/datatables.md)
- [DataAdapter からの DataSet の読み込み](../../../../../docs/framework/data/adonet/populating-a-dataset-from-a-dataadapter.md)
- [DataAdapter によるデータ ソースの更新](../../../../../docs/framework/data/adonet/updating-data-sources-with-dataadapters.md)
- [DataAdapter パラメーター](../../../../../docs/framework/data/adonet/dataadapter-parameters.md)
- [Web サービス記述言語ツール (Wsdl.exe)](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7h3ystb6(v=vs.100))
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
