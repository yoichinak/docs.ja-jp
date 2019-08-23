---
title: SQL Server Express ユーザー インスタンス
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00c12376-cb26-4317-86ad-e6e9c089be57
ms.openlocfilehash: f76b1f0a09be2f745156437919f43ebaa8840519
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69938489"
---
# <a name="sql-server-express-user-instances"></a>SQL Server Express ユーザー インスタンス
Microsoft SQL Server Express Edition (SQL Server Express) でサポートされる機能に、ユーザー インスタンスがあります。ユーザー インスタンスは、.NET Framework Data Provider for SQL Server (`SqlClient`) を使用している場合にしか利用できません。 ユーザー インスタンスは、親インスタンスによって生成される SQL Server Express データベース エンジンの独立したインスタンスです。 ユーザー インスタンスを使用すると、ローカル コンピューターの管理者以外のユーザーが、SQL Server Express データベースにアタッチして接続できます。 それぞれのインスタンスは、1 ユーザーあたり 1 インスタンスの原則に基づいて、個々のユーザーのセキュリティ コンテキストで実行されます。  
  
## <a name="user-instance-capabilities"></a>ユーザー インスタンスの機能  
 Windows を LUA (最小限の特権しか持たないユーザー アカウント) で実行しているユーザーにとっては、ユーザー インスタンスは特に有効な手段です。なぜなら、各ユーザーには、そのコンピューター上で実行されているインスタンスに対して SQL Server システム管理者 (`sysadmin`) の権限が割り当てられ、Windows 管理者として実行する必要がないためです。 SQL Server Express のユーザー インスタンスは、サービスではなく、そのユーザーの非管理者 Windows アカウントで実行されるため、ユーザー インスタンス上で実行されているソフトウェアは権限が限定され、システム全体に及ぶ変更を行うことはできません。 各ユーザー インスタンスは、その親インスタンスや同じコンピューター上で実行されている他のユーザー インスタンスとは分離されます。 ユーザー インスタンスで実行されているデータベースは、シングル ユーザー モードでのみ開くことができ、複数のユーザーが同じユーザー インスタンス上のデータベースに接続することはできません。 ユーザー インスタンスでは、レプリケーションと分散クエリも無効になります。  
  
 詳細については、SQL Server オンライン ブックの「ユーザー インスタンス」を参照してください。  
  
> [!NOTE]
> 既にコンピューターの管理者であるユーザーが、ユーザー インスタンスを使用する必要はありません。また、複数のデータベース ユーザーが関係する場合もユーザー インスタンスは不要です。  
  
## <a name="enabling-user-instances"></a>ユーザー インスタンスの有効化  
 ユーザー インスタンスを生成するには、SQL Server Express の親インスタンスが実行されている必要があります。 ユーザーインスタンスは、SQL Server Express をインストールすると既定で有効になります。ユーザーインスタンスは、親インスタンスで**sp_configure**システムストアドプロシージャを実行しているシステム管理者が明示的に有効または無効にすることができます。  
  
```  
-- Enable user instances.  
sp_configure 'user instances enabled','1'   
  
-- Disable user instances.  
sp_configure 'user instances enabled','0'  
```  
  
 ユーザー インスタンスのネットワーク プロトコルは、ローカルの名前付きパイプにする必要があります。 ユーザー インスタンスを SQL Server のリモート インスタンスで開始することはできません。また、SQL Server ログインは許可されません。  
  
## <a name="connecting-to-a-user-instance"></a>ユーザー インスタンスへの接続  
 キーワードとキーワードを使用<xref:System.Data.SqlClient.SqlConnection>すると`AttachDBFilename` <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 、ユーザーインスタンスに接続できます。 `User Instance` ユーザー インスタンスは、<xref:System.Data.SqlClient.SqlConnectionStringBuilder> の `UserInstance` プロパティおよび `AttachDBFilename` プロパティでもサポートされます。  
  
 以下にサンプルの接続文字列を示します。次の点に注意してください。  
  
- `Data Source` キーワードは、ユーザー インスタンスを生成している SQL Server Express の親インスタンスを指します。 既定のインスタンスは、.\sqlexpress です。  
  
- `Integrated Security` が `true` に設定されます。 ユーザー インスタンスに接続するには Windows 認証が必要です。SQL Server ログインはサポートされません。  
  
- `User Instance` は `true` に設定されます。これにより、ユーザー インスタンスが呼び出されます。 既定値は `false` です。  
  
- プライマリ データベース ファイル (.mdf) にアタッチするには、`AttachDbFileName` 接続文字列キーワードで完全パス名を指定します。 また、`AttachDbFileName` は、<xref:System.Data.SqlClient.SqlConnection> 接続文字列内の "extended properties" キーおよび "initial file name" キーに対応しています。  
  
- パイプ記号で囲まれた `|DataDirectory|` の部分には、接続元のアプリケーションのデータ ディレクトリを表す文字列が入ります。データベース ファイルである .mdf と .ldf、およびログ ファイルの格納場所を相対パスで指定します。 これらのファイルを別の場所に移す場合は、ファイルの完全パスを指定する必要があります。  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;AttachDBFilename=|DataDirectory|\InstanceDB.mdf;  
Initial Catalog=InstanceDB;  
```  
  
> [!NOTE]
> 実行時に接続文字列を作成するために <xref:System.Data.SqlClient.SqlConnectionStringBuilder><xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserInstance%2A> および <xref:System.Data.SqlClient.SqlConnectionStringBuilder.AttachDBFilename%2A> プロパティを使用することもできます。  
  
### <a name="using-the-124datadirectory124-substitution-string"></a>DataDirectory&#124;代替&#124;文字列の使用  
 ADO.NET 2.0 では、`AttachDbFileName` が拡張されて、`|DataDirectory|` というパイプ記号で囲まれた置換文字列が導入されました。 `DataDirectory` に `AttachDbFileName` を組み合わせて使用することで、データ ファイルへの相対パスを指定でき、完全パスを使用する代わりに、データ ソースの相対パスに基づいて接続文字列を作成できます。  
  
 `DataDirectory` が表す物理的な場所は、アプリケーションの種類によって異なります。 次の例では、アタッチする Northwind.mdf ファイルが、アプリケーションの \app_data フォルダーに格納されています。  
  
```  
Data Source=.\\SQLExpress;Integrated Security=true;  
User Instance=true;  
AttachDBFilename=|DataDirectory|\app_data\Northwind.mdf;  
Initial Catalog=Northwind;  
```  
  
 `DataDirectory` を使用する場合、最終的なファイル パスが、必ずその置換文字列が表すディレクトリのサブディレクトリとなるように指定する必要があります。 たとえば、`DataDirectory` を展開した結果が C:\AppDirectory\app_data である場合、app_data は c:\AppDirectory よりも下位であるため、上の例の接続文字列は適切に動作します。 しかし、`DataDirectory` を「`|DataDirectory|\..\data`」として指定すると、\data が \AppDirectory のサブディレクトリではないため、エラーが発生します。  
  
 接続文字列に指定した置換文字列の形式が正しくない場合、<xref:System.ArgumentException> がスローされます。  
  
> [!NOTE]
> 置換文字列は、<xref:System.Data.SqlClient> によってローカル コンピューターのファイル システムと照合されて完全パスに解決されます。 したがって、リモート サーバー、HTTP、および UNC のパス名はサポートされません。 サーバーがローカル コンピューター上に存在しない場合、接続を開こうとすると例外がスローされます。  
  
 <xref:System.Data.SqlClient.SqlConnection> を開くと、この接続文字列が、既定の SQL Server Express インスタンスから、実行時に開始された (呼び出し元のアカウントで実行される) インスタンスへとリダイレクトされます。  
  
> [!NOTE]
> ユーザー インスタンスは、通常のインスタンスよりも読み込みに時間がかかる場合があります。その場合は、<xref:System.Data.SqlClient.SqlConnection.ConnectionTimeout%2A> の値を増やす必要があります。  
  
 次のコード フラグメントでは、新しい `SqlConnection` を開き、接続文字列をコンソール ウィンドウに表示した後、`using` コード ブロックを終了した時点で接続を閉じます。  
  
```vb  
Private Sub OpenSqlConnection()  
    ' Retrieve the connection string.  
    Dim connectionString As String = GetConnectionString()  
  
    Using connection As New SqlConnection(connectionString)  
        connection.Open()  
        Console.WriteLine("ConnectionString: {0}", _  
           connection.ConnectionString)  
    End Using  
End Sub  
```  
  
```csharp  
private static void OpenSqlConnection()  
{  
    // Retrieve the connection string.  
    string connectionString = GetConnectionString();  
  
    using (SqlConnection connection =   
        new SqlConnection(connectionString))  
    {  
        connection.Open();  
        Console.WriteLine("ConnectionString: {0}",   
             connection.ConnectionString);  
    }  
}  
```  
  
> [!NOTE]
> SQL Server の内部で実行される共通言語ランタイム (CLR) コードでは、ユーザー インスタンスはサポートされません。 <xref:System.InvalidOperationException> の接続文字列で `Open` を指定して <xref:System.Data.SqlClient.SqlConnection> を呼び出すと、`User Instance=true` がスローされます。  
  
## <a name="lifetime-of-a-user-instance-connection"></a>ユーザー インスタンスの接続の有効期間  
 SQL Server にはサービスとして実行されるバージョンもありますが、それらのバージョンとは異なり、SQL Server Express のインスタンスは、開始と停止を手動で行う必要はありません。 既に実行されている場合を除き、ユーザーがログインして接続するたびにユーザー インスタンスが開始されます。 ユーザー インスタンス データベースには `AutoClose` オプションが用意されており、アクティブでない状態が一定期間続くとデータベースが自動的にシャットダウンされます。 開始された sqlservr.exe プロセスは、そのインスタンスに対する最後の接続が閉じられた後も、タイムアウトの期限が切れるまで引き続き実行されます。したがって、タイムアウトの期限が切れる前であれば、再開しなくても、新たに接続を開くことができます。 タイムアウトの期限が切れるまでの間に新しい接続が開かれなかった場合、ユーザー インスタンスは自動的にシャットダウンされます。 親インスタンスのシステム管理者は、 **sp_configure**を使用してユーザーインスタンス**タイムアウト**オプションを変更することにより、ユーザーインスタンスのタイムアウト期間を設定できます。 既定値は、60 分です。  
  
> [!NOTE]
> 接続文字列の `Min Pool Size` に 0 を超える値を指定した場合、接続プーラーは、開かれているいくつかの接続を常に保持するようになります。この場合、ユーザー インスタンスは自動的にはシャットダウンされません。  
  
## <a name="how-user-instances-work"></a>ユーザー インスタンスの動作  
 ユーザーごとに最初にユーザーインスタンスが生成されると、ユーザーインスタンスによって排他的に使用されるように、 **master**および**msdb**システムデータベースが、テンプレートデータフォルダーからユーザーのローカルアプリケーションデータリポジトリディレクトリの下のパスにコピーされます。 通常、このパスは `C:\Documents and Settings\<UserName>\Local Settings\Application Data\Microsoft\Microsoft SQL Server Data\SQLEXPRESS` です。 ユーザーインスタンスが起動すると、 **tempdb**、ログ、およびトレースファイルもこのディレクトリに書き込まれます。 ユーザー インスタンスには、ユーザーごとに一意の名前が生成されます。  
  
 既定では、Windows Builtin\Users グループのすべてのメンバーには、ローカル インスタンスへの接続のほか、SQL Server プログラム ファイルの読み取りと実行のための権限が付与されます。 ユーザー インスタンスをホストする呼び出し元ユーザーの資格情報が検証されると、そのユーザーは、そのインスタンスの `sysadmin` になります。 ユーザー インスタンスに対して有効になるのは共有メモリだけです。つまり、ローカル コンピューター上の操作以外は実行できません。  
  
 ユーザーには、接続文字列で指定された .mdf ファイルと .ldf ファイルについて、読み取りと書き込みの両方の権限が付与されている必要があります。  
  
> [!NOTE]
> .mdf ファイルと .ldf ファイルは、それぞれデータベース ファイルおよびログ ファイルを表します。 この 2 つのファイルはペアで存在するため、バックアップや復元操作を行う際は注意が必要です。 データベース ファイルには、ログ ファイルの正確なバージョンについての情報が格納されており、間違ったログ ファイルとペアになっていると、データベースを開くことはできません。  
  
 データの破損を防ぐため、ユーザー インスタンスのデータベースは排他アクセスで開かれます。 同じコンピューター上の同じデータベースを 2 つの異なるユーザー インスタンスで共有する場合は、一方のインスタンスのユーザーがデータベースを閉じる必要があります。データベースを閉じない限り、もう一方のインスタンスでそのデータベースを開くことはできません。  
  
## <a name="user-instance-scenarios"></a>ユーザー インスタンスのシナリオ  
 データベース アプリケーションの開発者は、ユーザー インスタンスを使用することで、開発コンピューター上に自分の管理者アカウントがなくても、SQL Server のデータ ストアを自由に利用できるようになります。 ユーザー インスタンスは Access/Jet モデルをベースとしています。つまり、データベース アプリケーションは単にファイルにアクセスするだけです。ユーザーには、すべてのデータベース オブジェクトに対する完全な権限が自動的に割り当てられます。システム管理者に権限を付与してもらう必要はありません。 サーバー コンピューターまたはローカル コンピューター上の管理特権を持たず、LUA (最小限の特権しか持たないユーザー アカウント) を使用しているユーザーが、データベース オブジェクトやアプリケーションを作成するケースもあります。ユーザー インスタンスには、こうした作業が想定されています。 ユーザー インスタンスを使って実行時にインスタンスを作成することで、より高い特権を持つシステム サービスのセキュリティ コンテキストではなく、そのユーザー自身のセキュリティ コンテキストでインスタンスを実行できます。  
  
> [!IMPORTANT]
> ユーザー インスタンスは、それを使用するすべてのアプリケーションが完全に信頼できる場合以外は使用しないでください。  
  
 ユーザー インスタンスのシナリオ  
  
- データの共有を必要としないシングル ユーザー アプリケーション。  
  
- ClickOnce 配置。 .NET Framework 2.0 以降および SQL Server Express が既にターゲット コンピューターにインストールされている場合、管理者以外のユーザーでも、ClickOnce アクションの結果としてダウンロードされたインストール パッケージをインストールして使用できます。 ただし、SQL Server Express がセットアップの一部として含まれている場合は、管理者が SQL Server Express をインストールする必要があります。 詳細については、「 [ClickOnce Deployment for Windows フォーム](../../../winforms/clickonce-deployment-for-windows-forms.md)」を参照してください。
  
- Windows 認証を使用した ASP.NET 専用ホスティング。 イントラネット上で、単一の SQL Server Express インスタンスをホストできます。 アプリケーションは、権限の借用ではなく、ASPNET Windows アカウントを使ってこのインスタンスに接続することになります。 サードパーティ製品を使ったホスティングや共有ホスティングのシナリオでユーザー インスタンスを使用することは避けてください。すべてのアプリケーションで同じユーザー インスタンスが使用され、アプリケーションを互いに分離することができなくなります。  
  
## <a name="see-also"></a>関連項目

- [SQL Server と ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)
- [接続文字列](../../../../../docs/framework/data/adonet/connection-strings.md)
- [データ ソースへの接続](../../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)
- [ADO.NET のマネージド プロバイダーと DataSet デベロッパー センター](https://go.microsoft.com/fwlink/?LinkId=217917)
