---
title: XML Web サービスからの DataSet の使用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9edd6b71-0fa5-4649-ae1d-ac1c12541019
ms.openlocfilehash: dbb45b890ddfab3f771d4b4a8932f970036b346d
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828294"
---
# <a name="consuming-a-dataset-from-an-xml-web-service"></a>XML Web サービスからの DataSet の使用
<xref:System.Data.DataSet> は、非接続型デザインで設計されています。インターネットで簡単にデータを転送するのが目的の一部です。 **データセット**への入力として指定できますまたはコードを追加せず、XML Web サービスからの出力のコンテンツをストリームするために必要という点では、「シリアル化可能な」、**データセット**XML Web サービスからクライアントとバックエンド。 **データセット**DiffGram 形式を使用して XML ストリームに暗黙的に変換は、ネットワーク経由で送信およびとして XML ストリームから再構築し、**データセット**受信側でします。 これにより、XML Web サービスを使用してリレーショナル データを送信および返送する、たいへん簡単で柔軟性のある方法が提供されます。 DiffGram 形式の詳細については、[Diffgram](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/diffgrams.md)を参照してください。  
  
 次の例は、XML Web サービスとを使用してクライアントを作成する方法を示します、**データセット**(変更されたデータを含む)、リレーショナル データの転送を解決するには、元のデータ ソースを更新します。  
  
> [!NOTE]
>  XML Web サービスを作成する場合は、常にセキュリティへの影響を考慮することをお勧めします。 XML Web サービスをセキュリティで保護する方法の詳細については、[セキュリティで保護する XML Web Services Created Using ASP.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/w67h0dw7(v=vs.100))を参照してください。  
  
### <a name="to-create-an-xml-web-service-that-returns-and-consumes-a-dataset"></a>DataSet を返し、処理する XML Web サービスを作成するには、次のようにします。  
  
1.  XML Web サービスを作成します。  
  
     例では、XML Web サービスが作成から顧客の一覧をここでは、データを返す、 **Northwind**データベース、および受信を**データセット**データへの更新プログラムを使用する XML Web サービス元のデータ ソースに解決します。  
  
     XML Web サービスは、2 つのメソッドを公開します。**GetCustomers**、顧客の一覧を返すと**UpdateCustomers**、更新プログラムをデータ ソースに解決します。 この XML Web サービスは、Web サーバー上の DataSetSample.asmx というファイルに格納されます。 次のコードは、DataSetSample.asmx の内容の概要を示しています。  
  
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
  
     一般的なシナリオで、 **UpdateCustomers**メソッド オプティミスティック同時実行制御違反をキャッチに書き込まれます。 説明を簡単にするために、この例では UpdateCustmoers メソッドを省略しています。 オプティミスティック同時実行制御の詳細については、[オプティミスティック同時実行制御](../../../../../docs/framework/data/adonet/optimistic-concurrency.md)を参照してください。  
  
2.  XML Web サービス プロキシを作成します。  
  
     XML Web サービスのクライアントは、公開されたメソッドを使用するために SOAP プロキシを必要とします。 このプロキシは、Visual Studio を使用して生成することができます。 Visual Studio から既存の Web サービスへの Web 参照を設定することにより、この手順で説明されているすべての動作が自動的に実行されます。 プロキシ クラスを手動で作成する場合は、後述の手順を参照してください。 ほとんどの場合、Visual Studio による、クライアント アプリケーションのプロキシ クラスの作成で十分です。  
  
     プロキシは、Web サービス記述言語ツールを使用して作成できます。 たとえば、XML Web サービスが、URL で公開されている`http://myserver/data/DataSetSample.asmx`の名前空間と Visual Basic .NET プロキシを作成する、次のコマンドを発行**WebData.DSSample**ファイル sample.vb に格納します。  
  
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
  
3.  XML Web サービスのクライアントを作成します。  
  
     Visual studio で、Web サービス プロキシ クラスを生成する場合は、簡単に、クライアント プロジェクトを作成し、ソリューション エクスプ ローラー ウィンドウで、プロジェクトを右クリックし、 をクリックして**Web 参照の追加**から Web サービスを選択します。(この必要があります、Web サービス エンドポイントのアドレスを提供して、Web サービスを現在のソリューション内、または現在のコンピューターで使用できない場合。) Web サービスの一覧上記の手順に従って、XML Web サービス プロキシを作成した場合は、それをクライアント コードにインポートし、XML Web サービスのメソッドを処理できます。 次のサンプル コードは、プロキシのライブラリ呼び出しをインポート**GetCustomers**顧客の一覧を取得する、新しい顧客に追加して返します、**データセット**する更新プログラムが、 **UpdateCustomers**.  
  
     例では、渡される通知、**データセット**によって返される**DataSet.GetChanges**に**UpdateCustomers**変更行のみに渡される必要があるため**UpdateCustomers**します。 **UpdateCustomers** 、解決を返します**データセット**、し、可能な**マージ**既存**データセット**を組み込むと、解決された変更更新プログラムからの行エラー情報。 次のコードには、Web 参照を作成する Visual Studio を使用していると、名前が dssample に変更済みの Web 参照が前提としています、 **Web 参照の追加** ダイアログ ボックス。  
  
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
