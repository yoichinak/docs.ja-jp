---
title: データベース アクセス アクティビティ
ms.date: 03/30/2017
ms.assetid: 174a381e-1343-46a8-a62c-7c2ae2c4f0b2
ms.openlocfilehash: 2463c3a87be7f7e248572d45e018b72661f4f8c7
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322603"
---
# <a name="database-access-activities"></a>データベース アクセス アクティビティ
データベース アクセス アクティビティを使用すると、ワークフロー内でデータベースにアクセスできます。 これらのアクティビティは、取得、情報を変更または使用するデータベースへのアクセスを許可する[ADO.NET](https://go.microsoft.com/fwlink/?LinkId=166081)データベースにアクセスします。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。
>
>  `<InstallDrive>:\WF_WCF_Samples`
>
>  このディレクトリが存在しない場合は、(ダウンロード ページ) に移動してすべての Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。
>
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`

## <a name="database-activities"></a>データベース アクティビティ
 以降では、このサンプルに含まれている一連のアクティビティについて説明します。

## <a name="dbupdate"></a>DbUpdate
 データベースを変更する SQL クエリを実行します (挿入、更新、削除、およびその他の変更)。

 このクラスは作業を非同期に実行します (<xref:System.Activities.AsyncCodeActivity> から派生し、その非同期機能を使用します)。

 接続情報を構成するには、プロバイダーの不変名 (`ProviderName`) と接続文字列 (`ConnectionString`) を設定するか、アプリケーション構成ファイルの接続文字列構成名 (`ConfigFileSectionName`) を使用します。

 実行するクエリは `Sql` プロパティで構成し、パラメーターは `Parameters` コレクションを通じて渡します。

 `DbUpdate` の実行が完了すると、影響を受けたレコードの数が `AffectedRecords` プロパティで返されます。

```
Public class DbUpdate: AsyncCodeActivity
{
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [DependsOn("Parameters")]
    public OutArgument<int> AffectedRecords { get; set; }
}
```

|引数|説明|
|-|-|
|ProviderName|ADO.NET プロバイダーの不変名。 この引数を設定する場合は、`ConnectionString` も設定する必要があります。|
|ConnectionString|データベースに接続するための接続文字列。 この引数を設定する場合は、`ProviderName` も設定する必要があります。|
|ConfigName|接続情報が格納されている構成ファイル セクションの名前。 この引数を設定する場合は、`ProviderName` と `ConnectionString` は必要ありません。|
|CommandType|実行する <xref:System.Data.Common.DbCommand> の種類。|
|Sql|実行する SQL コマンド。|
|パラメーター|SQL クエリのパラメーターのコレクション。|
|AffectedRecords|最後の操作の影響を受けたレコードの数。|

## <a name="dbqueryscalar"></a>DbQueryScalar
 データベースから 1 つの値を取得するクエリを実行します。

 このクラスは作業を非同期に実行します (<xref:System.Activities.AsyncCodeActivity%601> から派生し、その非同期機能を使用します)。

 接続情報を構成するには、プロバイダーの不変名 (`ProviderName`) と接続文字列 (`ConnectionString`) を設定するか、アプリケーション構成ファイルの接続文字列構成名 (`ConfigFileSectionName`) を使用します。

 実行するクエリは `Sql` プロパティで構成し、パラメーターは `Parameters` コレクションを通じて渡します。

 後`DbQueryScalar`は、スカラー型は、実行で返される、`Result out`引数 (型の`TResult`、つまり基底クラスで定義されている<xref:System.Activities.AsyncCodeActivity%601>)。

```
public class DbQueryScalar<TResult> : AsyncCodeActivity<TResult>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|引数|説明|
|-|-|
|ProviderName|ADO.NET プロバイダーの不変名。 この引数を設定する場合は、`ConnectionString` も設定する必要があります。|
|ConnectionString|データベースに接続するための接続文字列。 この引数を設定する場合は、`ProviderName` も設定する必要があります。|
|ConfigName|接続情報が格納されている構成ファイル セクションの名前。 この引数を設定する場合は、`ProviderName` と `ConnectionString` は必要ありません。|
|CommandType|実行する <xref:System.Data.Common.DbCommand> の種類。|
|Sql|実行する SQL コマンド。|
|パラメーター|SQL クエリのパラメーターのコレクション。|
|結果|クエリの実行後に取得されたスカラー。 この引数は `TResult` 型です。|

## <a name="dbquery"></a>DbQuery
 オブジェクトのリストを取得するクエリを実行します。 マッピング関数が実行されるクエリが実行された後 (できます<xref:System.Func%601> < `DbDataReader`、 `TResult`> または<xref:System.Activities.ActivityFunc%601> < `DbDataReader`、 `TResult`>)。 このマッピング関数は、`DbDataReader` 内のレコードを取得して、返されるオブジェクトにマップします。

 接続情報を構成するには、プロバイダーの不変名 (`ProviderName`) と接続文字列 (`ConnectionString`) を設定するか、アプリケーション構成ファイルの接続文字列構成名 (`ConfigFileSectionName`) を使用します。

 実行するクエリは `Sql` プロパティで構成し、パラメーターは `Parameters` コレクションを通じて渡します。

 SQL クエリの結果は、`DbDataReader` を使用して取得されます。 `DbDataReader` が反復処理されて、`DbDataReader` の行が `TResult` のインスタンスにマップされます。 ユーザー `DbQuery` 、マッピング コードをこれは、2 つの方法で実行できますを提供する必要があります: を使用して、 <xref:System.Func%601> < `DbDataReader`、 `TResult`> または<xref:System.Activities.ActivityFunc%601> < `DbDataReader`、 `TResult`>。 1 つ目の方法は、マッピングが 1 つのパルスで実行されるので 高速ですが、XAML にシリアル化することはできません。 2 つ目の方法は、マッピングが複数のパルスで実行されるので 時間がかかることがありますが、XAML へのシリアル化や宣言による作成が可能です (既存のアクティビティをマッピングに参加させることができます)。

```
public class DbQuery<TResult> : AsyncCodeActivity<IList<TResult>> where TResult : class
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }

    [OverloadGroup("DirectMapping")]
    [DefaultValue(null)]
    public Func<DbDataReader, TResult> Mapper { get; set; }

    [OverloadGroup("MultiplePulseMapping")]
    [DefaultValue(null)]
    public ActivityFunc<DbDataReader, TResult> MapperFunc { get; set; }
}
```

|引数|説明|
|-|-|
|ProviderName|ADO.NET プロバイダーの不変名。 この引数を設定する場合は、`ConnectionString` も設定する必要があります。|
|ConnectionString|データベースに接続するための接続文字列。 この引数を設定する場合は、`ProviderName` も設定する必要があります。|
|ConfigName|接続情報が格納されている構成ファイル セクションの名前。 この引数を設定する場合は、`ProviderName` と `ConnectionString` は必要ありません。|
|CommandType|実行する <xref:System.Data.Common.DbCommand> の種類。|
|Sql|実行する SQL コマンド。|
|パラメーター|SQL クエリのパラメーターのコレクション。|
|Mapper|マッピング関数 (<xref:System.Func%601><`DbDataReader`、 `TResult`>) 内のレコードを取得する、 `DataReader` 、クエリの実行結果として取得され、型のオブジェクトのインスタンスを返します`TResult`に追加するには`Result`コレクション。<br /><br /> この場合、マッピングは 1 つのパルスで実行されますが、デザイナーを使用して宣言で作成することはできません。|
|MapperFunc|マッピング関数 (<xref:System.Activities.ActivityFunc%601><`DbDataReader`、 `TResult`>) 内のレコードを取得する、 `DataReader` 、クエリの実行結果として取得され、型のオブジェクトのインスタンスを返します`TResult`に追加するには`Result`コレクション。<br /><br /> この場合、マッピングは複数のパルスで実行されます。 この関数は、XAML へのシリアル化や宣言による作成が可能です (既存のアクティビティをマッピングに参加させることができます)。|
|結果|クエリを実行し、`DataReader` の各レコードに対してマッピング関数を実行した結果として取得されたオブジェクトのリスト。|

## <a name="dbquerydataset"></a>DbQueryDataSet
 <xref:System.Data.DataSet> を返すクエリを実行します。 このクラスは作業を非同期に実行します  派生した<xref:System.Activities.AsyncCodeActivity> < `TResult`> とその非同期機能を使用します。

 接続情報を構成するには、プロバイダーの不変名 (`ProviderName`) と接続文字列 (`ConnectionString`) を設定するか、アプリケーション構成ファイルの接続文字列構成名 (`ConfigFileSectionName`) を使用します。

 実行するクエリは `Sql` プロパティで構成し、パラメーターは `Parameters` コレクションを通じて渡します。

 後に、`DbQueryDataSet`が実行される、`DataSet`で返される、`Result out`引数 (型の`TResult`、つまり基底クラスで定義されている<xref:System.Activities.AsyncCodeActivity%601>)。

```
public class DbQueryDataSet : AsyncCodeActivity<DataSet>
{
    // public arguments
    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DefaultValue(null)]
    public InArgument<string> ProviderName { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConnectionString")]
    [DependsOn("ProviderName")]
    [DefaultValue(null)]
    public InArgument<string> ConnectionString { get; set; }

    [RequiredArgument]
    [OverloadGroup("ConfigFileSectionName")]
    [DefaultValue(null)]
    public InArgument<string> ConfigName { get; set; }

    [DefaultValue(null)]
    public CommandType CommandType { get; set; }

    [RequiredArgument]
    public InArgument<string> Sql { get; set; }

    [DependsOn("Sql")]
    [DefaultValue(null)]
    public IDictionary<string, Argument> Parameters { get; }
}
```

|引数|説明|
|-|-|
|ProviderName|ADO.NET プロバイダーの不変名。 この引数を設定する場合は、`ConnectionString` も設定する必要があります。|
|ConnectionString|データベースに接続するための接続文字列。 この引数を設定する場合は、`ProviderName` も設定する必要があります。|
|ConfigName|接続情報が格納されている構成ファイル セクションの名前。 この引数を設定する場合は、`ProviderName` と `ConnectionString` は必要ありません。|
|CommandType|実行する <xref:System.Data.Common.DbCommand> の種類。|
|Sql|実行する SQL コマンド。|
|パラメーター|SQL クエリのパラメーターのコレクション。|
|結果|<xref:System.Data.DataSet> クエリの実行後に取得しました。|

## <a name="configuring-connection-information"></a>接続情報の構成
 すべての DbActivities は同じ構成パラメーターを共有します。 パラメーターを構成するには次の 2 つの方法があります。

-   `ConnectionString + InvariantName`:ADO.NET プロバイダーの不変の名前と接続文字列を設定します。

    ```
    Activity dbSelectCount = new DbQueryScalar<DateTime>()
    {
        ProviderName = "System.Data.SqlClient",
        ConnectionString = @"Data Source=.\SQLExpress;
                             Initial Catalog=DbActivitiesSample;
                             Integrated Security=True",
        Sql = "SELECT GetDate()"
    };
    ```

-   `ConfigName`:接続情報を含む構成セクションの名前を設定します。

    ```xml
    <connectionStrings>
        <add name="DbActivitiesSample"
             providerName="System.Data.SqlClient"
             connectionString="Data Source=.\SQLExpress;Initial Catalog=DbActivitiesSample;Integrated Security=true"/>
      </connectionStrings>
    ```

-   アクティビティで次のように設定します。

    ```
    Activity dbSelectCount = new DbQueryScalar<int>()
    {
        ConfigName = "DbActivitiesSample",
        Sql = "SELECT COUNT(*) FROM Roles"
    };
    ```

## <a name="running-this-sample"></a>このサンプルの実行

### <a name="setup-instructions"></a>セットアップ手順
 このサンプルはデータベースを使用します。 設定と読み込みのためのスクリプト (Setup.cmd) がサンプルに付属しているので、 そのファイルを、コマンド プロンプトを使用して実行してください。

 Setup.cmd スクリプトは、CreateDb.sql スクリプト ファイルを呼び出します。このスクリプト ファイルには、次の操作を実行する SQL コマンドが含まれています。

-   DbActivitiesSample という名前のデータベースを作成します。

-   Roles テーブルを作成します。

-   Employees テーブルを作成します。

-   3 個のレコードを Roles テーブルに挿入します。

-   12 個のレコードを Employees テーブルに挿入します。

##### <a name="to-run-setupcmd"></a>Setup.cmd を実行するには

1. コマンド プロンプトを開きます。

2. DbActivities サンプル フォルダーに移動します。

3. "Setup.cmd"を入力し、ENTER キーを押します。

    > [!NOTE]
    >  Setup.cmd は、ローカル コンピューターの SqlExpress インスタンスにサンプルをインストールしようとします。 他の SQL Server インスタンスにインストールする場合は、その新しいインスタンス名を使用して Setup.cmd を編集します。

##### <a name="to-uninstall-the-sample-database"></a>サンプル データベースをアンインストールするには

1. コマンド プロンプトで、サンプル フォルダーから Cleanup.cmd を実行します。

##### <a name="to-run-the-sample"></a>サンプルを実行するには

1. Visual Studio 2010 でソリューションを開きます

2. ソリューションをコンパイルするには、Ctrl キーと Shift キーを押しながら B キーを押します。

3. Ctrl キーを押しながら F5 キーを押して、サンプルをデバッグなしで実行します。

> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\DbActivities`
