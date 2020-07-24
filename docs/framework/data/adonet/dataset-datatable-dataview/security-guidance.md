---
title: DataSet と DataTable のセキュリティ ガイダンス
ms.date: 07/14/2020
dev_langs:
- csharp
ms.openlocfilehash: 2fbac625ae0049fc4c363977dc1d3fbcfb376025
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416203"
---
# <a name="dataset-and-datatable-security-guidance"></a>DataSet と DataTable のセキュリティ ガイダンス

この記事は以下に適用されます。

* .NET Framework (すべてのバージョン)
* .NET Core 以降
* .NET 5.0 以降

[DataSet](/dotnet/api/system.data.dataset) 型と [DataTable](/dotnet/api/system.data.datatable) 型は .NET のレガシ コンポーネントであり、マネージド オブジェクトとしてデータ セットを表すことができます。 これらのコンポーネントは、元の [ADO.NET インフラストラクチャ](/dotnet/framework/data/adonet/dataset-datatable-dataview/)の一部として .NET 1.0 で導入されました。 それらの目標は、リレーショナル データ セットに対するマネージド ビューを提供し、基になるデータのソースが XML、SQL、または他のテクノロジであるかどうかを抽象化することでした。

最新のデータ ビュー パラダイムを含め、ADO.NET の詳細については、[ADO.NET のドキュメント](/dotnet/framework/data/adonet/)を参照してください。

## <a name="default-restrictions-when-deserializing-a-dataset-or-datatable-from-xml"></a>XML から DataSet または DataTable を逆シリアル化するときの既定の制限

.NET Framework、.NET Core、.NET のサポートされているすべてのバージョンで、`DataSet` と `DataTable` には、逆シリアル化されるデータに存在できるオブジェクトの型に関して次の制限があります。 既定では、このリストは以下に制限されます。

* プリミティブとプリミティブに相当するもの: `bool`、`char`、`sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double`、`decimal`、`DateTime`、`DateTimeOffset`、`TimeSpan`、`string`、`Guid`、`SqlBinary`、`SqlBoolean`、`SqlByte`、`SqlBytes`、`SqlChars`、`SqlDateTime`、`SqlDecimal`、`SqlDouble`、`SqlGuid`、`SqlInt16`、`SqlInt32`、`SqlInt64`、`SqlMoney`、`SqlSingle`、`SqlString`。
* 一般に使用される非プリミティブ: `Type`、`Uri`、`BigInteger`。
* 一般に使用される _System.Drawing_ 型: `Color`、`Point`、`PointF`、`Rectangle`、`RectangleF`、`Size`、`SizeF`。
* `Enum` 型。
* 上記の型の配列およびリスト。

受信 XML データに、このリストにない型のオブジェクトが含まれている場合:

* 例外がスローされる。
* 逆シリアル化操作が失敗する。

既存の `DataSet` または `DataTable` インスタンスに XML を読み込むときは、既存の列の定義も考慮されます。 テーブルにカスタム型の列定義が既に含まれている場合は、XML の逆シリアル化操作の間だけ、その型が許可リストに一時的に追加されます。

```cs
XmlReader xmlReader = GetXmlReader();

// Assume the XML blob contains data for type MyCustomClass.
// The following call to ReadXml fails because MyCustomClass isn't in the allowed types list.

DataTable table = new DataTable("MyDataTable");
table.ReadXml(xmlReader);

// However, the following call to ReadXml succeeds, since the DataTable instance
// already defines a column of type MyCustomClass.

DataTable table = new DataTable("MyDataTable");
table.Columns.Add("MyColumn", typeof(MyCustomClass));
table.ReadXml(xmlReader); // this call will succeed
```

オブジェクトの型の制限は、`XmlSerializer` を使用して `DataSet` または `DataTable` のインスタンスを逆シリアル化するときにも適用されます。 ただし、`BinaryFormatter` を使用して `DataSet` または `DataTable` のインスタンスを逆シリアル化するときは、適用されない場合があります。

XML の逆シリアル化 API を使用せずにデータベースから直接 `DataTable` のインスタンスにデータを設定する場合など、`DataAdapter.Fill` を使用するときは、オブジェクトの型の制限は適用されません。

### <a name="extend-the-list-of-allowed-types"></a>許可される型のリストを拡張する

アプリでは、許可される型のリストを拡張して、上記の組み込み型に加えてカスタム型を含めることができます。 許可される型のリストを拡張する場合、その変更は、アプリ内の "_すべての_" `DataSet` および `DataTable` のインスタンスに影響します。 組み込みの許可される型のリストから、型を削除することはできません。

#### <a name="extend-through-configuration-net-framework-40---48"></a>構成によって拡張する (.NET Framework 4.0 - 4.8)

_App.config_ を使用して、許可される型のリストを拡張できます。 許可される型のリストを拡張するには、次のようにします。

* `<configSections>` 要素を使用して、_System.Data_ 構成セクションへの参照を追加します。
* `<system.data.dataset.serialization>`/`<allowedTypes>` を使用して、追加の型を指定します。

各 `<add>` 要素では、アセンブリ修飾型名を使用して、型を 1 つだけ指定する必要があります。 許可される型のリストに型を追加するには、複数の `<add>` 要素を使用します。

次の例では、カスタム型 `Fabrikam.CustomType` を追加することによって、許可される型のリストを拡張する方法を示します。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add type="assembly qualified type name" /> -->
      <add type="Fabrikam.CustomType, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
      <!-- additional <add /> elements as needed -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

型のアセンブリ修飾名を取得するには、次のコードで示すように、[Type.AssemblyQualifiedName](/dotnet/api/system.type.assemblyqualifiedname) プロパティを使用します。

```cs
string assemblyQualifiedName = typeof(Fabrikam.CustomType).AssemblyQualifiedName;
```

<a name="etc"></a>

#### <a name="extend-through-configuration-net-framework-20---35"></a>構成によって拡張する (.NET Framework 2.0 - 3.5)

アプリの対象が .NET Framework 2.0 または 3.5 の場合でも、上記の _App.config_ のメカニズムを使用して、許可される型のリストを拡張できます。 ただし、次のコードで示すように、`<configSections>` 要素は少し異なります。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- The below <sectionGroup> and <section> are specific to .NET Framework 2.0 and 3.5. -->
    <sectionGroup name="system.data.dataset.serialization" type="System.Data.SerializationSettingsSectionGroup, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="allowedTypes" type="System.Data.AllowedTypesSectionHandler, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>
    </sectionGroup>
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes>
      <!-- <add /> elements, as demonstrated in the .NET Framework 4.0 - 4.8 sample code above. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

#### <a name="extend-programmatically-net-framework-net-core-net-50"></a>プログラムによって拡張する (.NET Framework、.NET Core、.NET 5.0 以降)

許可される型のリストは、次のコードで示すように、[AppDomain.SetData](/dotnet/api/system.appdomain.setdata) と既知のキー _System.Data.DataSetDefaultAllowedTypes_ を使用することにより、プログラムで拡張することもできます。

```cs
Type[] extraAllowedTypes = new Type[]
{
    typeof(Fabrikam.CustomType),
    typeof(Contoso.AdditionalCustomType)
};

AppDomain.CurrentDomain.SetData("System.Data.DataSetDefaultAllowedTypes", extraAllowedTypes);
```

拡張メカニズムを使用している場合、キー _System.Data.DataSetDefaultAllowedTypes_ に関連付ける値は、`Type[]` 型である必要があります。

.NET Framework では、_App.config_ と `AppDomain.SetData` の両方で、許可される型のリストを拡張できます。 この場合、`DataSet` と `DataTable` では、その型がいずれかのリストに存在する場合、データの一部としてオブジェクトを逆シリアル化できます。

### <a name="run-an-app-in-audit-mode-net-framework"></a>監査モードでアプリを実行する (.NET Framework)

.NET Framework では、`DataSet` と `DataTable` において監査モード機能が提供されます。 監査モードが有効になっていると、`DataSet` と `DataTable` では、受信したオブジェクトの型が、許可される型のリストと比較されます。 ただし、許可されていない型のオブジェクトが見つかった場合でも、例外はスローされ**ません**。 代わりに、`DataSet` と `DataTable` では、アタッチされている `TraceListener` のインスタンスに、疑わしい型が存在することが通知されます。これにより、`TraceListener` ではこの情報をログに記録できます。 例外はスローされず、逆シリアル化操作は続行されます。

> [!WARNING]
> "監査モード" でのアプリの実行は、テストに使用する一時的な手段のみにする必要があります。 監査モードが有効になっていると、`DataSet` と `DataTable` では型の制限が適用されず、これによりアプリ内にセキュリティ ホールが生じる可能性があります。 詳細については、「[すべての型の制限を削除する](#ratr)」および「[信頼されていない入力に関する安全性](#swr)」のセクションを参照してください。

監査モードは、_App.config_ を使用して有効にすることができます。

* `<configSections>` 要素に設定する適切な値については、このドキュメントの[構成による拡張](#etc)に関するセクションを参照してください。
* 次のマークアップで示すように、監査モードを有効にするには `<allowedTypes auditOnly="true">` を使用します。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <!-- See the section of this document titled "Extending through configuration" for the appropriate
         <sectionGroup> and <section> elements to put here, depending on whether you're running .NET
         Framework 2.0 - 3.5 or 4.0 - 4.8. -->
  </configSections>
  <system.data.dataset.serialization>
    <allowedTypes auditOnly="true"> <!-- setting auditOnly="true" enables audit mode -->
      <!-- Optional <add /> elements as needed. -->
    </allowedTypes>
  </system.data.dataset.serialization>
</configuration>
```

監査モードを有効にした後は、_App.config_ を使用して、適切な `TraceListener` を `DataSet` の組み込みの `TraceSource.` に接続できます。組み込みのトレース ソースの名前は _System.Data.DataSet_ です。 次の例では、トレース イベントをコンソール_と_ディスク上のログ ファイルに書き込む方法を示します。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.diagnostics>
    <sources>
      <source name="System.Data.DataSet"
              switchType="System.Diagnostics.SourceSwitch"
              switchValue="Warning">
        <listeners>
          <!-- write to the console -->
          <add name="console"
               type="System.Diagnostics.ConsoleTraceListener" />
          <!-- *and* write to a log file on disk -->
          <add name="filelog"
               type="System.Diagnostics.TextWriterTraceListener"
               initializeData="c:\logs\mylog.txt" />
        </listeners>
      </source>
    </sources>
  </system.diagnostics>
</configuration>
```

`TraceSource` と `TraceListener` の詳細については、「[方法: TraceSource とフィルターをトレース リスナーと共に使用する](../../../debug-trace-profile/how-to-use-tracesource-and-filters-with-trace-listeners.md)」を参照してください。

> [!NOTE]
> 監査モードでのアプリの実行は、.NET Core または .NET 5.0 以降では使用できません。

<a name="ratr"></a>

### <a name="remove-all-type-restrictions"></a>すべての型の制限を削除する

アプリで `DataSet` と `DataTable` からすべての型の制限を削除する必要がある場合:

* 型の制限を抑制するには、いくつかのオプションがあります。
* 使用できるオプションは、アプリの対象となるフレームワークによって異なります。

> [!WARNING]
> 型の制限をすべて削除すると、アプリ内にセキュリティ ホールが生じる可能性があります。 このメカニズムを使用するときは、アプリで信頼されていない入力を読み取るために `DataSet` または `DataTable` を使用して**いない**ことを確認してください。 詳細については、[CVE-2020-1147](https://portal.msrc.microsoft.com/en-us/security-guidance/advisory/CVE-2020-1147) および後のセクション「[信頼されていない入力に関する安全性](#swr)」を参照してください。

#### <a name="through-appcontext-configuration-net-framework-46---48-net-core-21-and-later-net-50-and-later"></a>AppContext の構成を使用 (.NET Framework 4.6 - 4.8、.NET Core 2.1 以降、.NET 5.0 以降)

`AppContext` スイッチの `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` を `true` に設定すると、`DataSet` および `DataTable` からすべての型制限が削除されます。

.NET Framework では、次の構成で示すように、_App.config_ を使用してこのスイッチを有効にすることができます。

```xml
<configuration>
   <runtime>
      <!-- Warning: setting the following switch can introduce a security problem. -->
      <AppContextSwitchOverrides value="Switch.System.Data.AllowArbitraryDataSetTypeInstantiation=true" />
   </runtime>
</configuration>
```

ASP.NET では、`<AppContextSwitchOverrides>` 要素は使用できません。 代わりに、次の構成で示すように、_Web.config_ を使用してスイッチを有効にすることができます。

```xml
<configuration>
    <appSettings>
        <!-- Warning: setting the following switch can introduce a security problem. -->
        <add key="AppContext.SetSwitch:Switch.System.Data.AllowArbitraryDataSetTypeInstantiation" value="true" />
    </appSettings>
</configuration>
```

詳細については、[\<AppContextSwitchOverrides>](../../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) 要素を参照してください。

.NET Core、.NET 5、および ASP.NET Core では、次の JSON で示すように、この設定は _runtimeconfig.json_ によって制御されます。

```json
{
  "runtimeOptions": {
    "configProperties": {
      "Switch.System.Data.AllowArbitraryDataSetTypeInstantiation": true
    }
  }
}
```

詳細については、「[.NET Core ランタイム構成設定](/dotnet/core/run-time-config/)」を参照してください。

`AllowArbitraryDataSetTypeInstantiation` は、構成ファイルを使用する代わりに、次のコードで示すように、[AppContext.SetSwitch](/dotnet/api/system.appcontext.setswitch) を使用してプログラムで設定することもできます。

```cs
// Warning: setting the following switch can introduce a security problem.
AppContext.SetSwitch("Switch.System.Data.AllowArbitraryDataSetTypeInstantiation", true);
```

 前述のプログラムによる方法を選択する場合は、アプリの起動の初期段階で `AppContext.SetSwitch` の呼び出しを行う必要があります。

#### <a name="through-the-machine-wide-registry-net-framework-20---48"></a>コンピューター全体のレジストリを使用 (.NET Framework 2.0 - 4.8)

`AppContext` を使用できない場合は、Windows レジストリを使用して、型制限のチェックを無効にすることができます。

* 管理者は、レジストリを構成する必要があります。
* レジストリの使用は、コンピューター全体の変更であり、コンピューター上で実行されている "_すべての_" アプリに影響を与えます。

| 種類  |  [値] |
|---|---|
| **レジストリ キー** | `HKLM\SOFTWARE\Microsoft\.NETFramework\AppContext` |
| **値の名前** | `Switch.System.Data.AllowArbitraryDataSetTypeInstantiation` |
| **値の型** | `REG_SZ` |
| **値のデータ** | `true` |

64 ビットのオペレーティング システムでは、64 ビット キー (上記) と 32 ビット キーの両方に、この値を追加することが必要な場合があります。 32 ビット キーは `HKLM\SOFTWARE\WOW6432Node\Microsoft\.NETFramework\AppContext` にあります。

レジストリを使用して `AppContext` を構成する方法の詳細については、「[ライブラリ コンシューマーの AppContext](/dotnet/api/system.appcontext#appcontext-for-library-consumers)」を参照してください。

<a name="swr"></a>

## <a name="safety-with-regard-to-untrusted-input"></a>信頼されていない入力に関する安全性

`DataSet` と `DataTable` では、XML ペイロードの逆シリアル化中に存在することが許可される型に対して既定の制限が適用されますが、 __`DataSet` と `DataTable` は、信頼されていない入力で設定されるときは一般に安全ではありません__。 次に示すのは、`DataSet` または `DataTable` のインスタンスが信頼されていない入力を読み取る可能性がある方法の一覧ですが、これだけではありません。

* `DataAdapter` でデータベースを参照し、`DataAdapter.Fill` メソッドを使用してデータベース クエリの内容を `DataSet` に設定します。
* `DataSet.ReadXml` または `DataTable.ReadXml` メソッドを使用して、列と行の情報が含まれる XML ファイルを読み取ります。
* ASP.NET (SOAP) Web サービスまたは WCF エンドポイントの一部として、`DataSet` または `DataTable` のインスタンスをシリアル化します。
* `XmlSerializer` などのシリアライザーを使用して、XML ストリームから `DataSet` または `DataTable` のインスタンスを逆シリアル化します。
* `JsonConvert` などのシリアライザーを使用して、JSON ストリームから `DataSet` または `DataTable` のインスタンスを逆シリアル化します。 `JsonConvert` は、一般的なサードパーティの [Newtonsoft.Json](https://www.newtonsoft.com/json) ライブラリのメソッドです。
* `BinaryFormatter` などのシリアライザーを使用して、RAW 型バイト ストリームから `DataSet` または `DataTable` のインスタンスを逆シリアル化します。

このドキュメントでは、前述のシナリオの安全性に関する考慮事項について説明します。

## <a name="use-dataadapterfill-to-populate-a-dataset-from-an-untrusted-data-source"></a>`DataAdapter.Fill` を使用して、信頼されていないデータ ソースから `DataSet` を設定する

次の例で示すように、[`DataAdapter.Fill` メソッド](/dotnet/api/system.data.common.dataadapter.fill)を使用して `DataAdapter` から `DataSet` インスタンスを設定できます。

```cs
// Assumes that connection is a valid SqlConnection object.  
string queryString =
  "SELECT CustomerID, CompanyName FROM dbo.Customers";  
SqlDataAdapter adapter = new SqlDataAdapter(queryString, connection);  
  
DataSet customers = new DataSet();  
adapter.Fill(customers, "Customers");
```

(上のコード例は、「[DataAdapter からの DataSet の読み込み](../populating-a-dataset-from-a-dataadapter.md)」にある、より大きな例の一部です。)

> ほとんどのアプリでは単純化し、データベース レイヤーが信頼されていると想定できます。 ただし、アプリの[脅威モデリング](https://www.microsoft.com/securityengineering/sdl/threatmodeling)を行う習慣がある場合は、脅威モデルで、アプリケーション (クライアント) とデータベース層 (サーバー) の間に信頼境界があると考えられる場合があります。 クライアントとサーバーの間で[相互認証](/sql/relational-databases/native-client/features/service-principal-name-spn-support-in-client-connections)または [AAD 認証](/azure/azure-sql/database/authentication-aad-overview)を使用することは、これに関連するリスクに対処するための 1 つの方法です。 このセクションの残りの部分では、信頼されていないサーバーに接続するクライアントで可能性のある結果について説明します。

信頼されていないデータ ソースで `DataAdapter` を参照した場合の結果は、`DataAdapter` 自体の実装によって異なります。

### <a name="sqldataadapter"></a>SqlDataAdapter

組み込み型 [SqlDataAdapter](/dotnet/api/microsoft.data.sqlclient.sqldataadapter) の場合、信頼されていないデータ ソースを参照すると、サービス拒否 (DoS) 攻撃が発生する可能性があります。 DoS 攻撃により、アプリが応答しなくなったりクラッシュしたりする可能性があります。 攻撃者がアプリと一緒に DLL を仕掛けることができる場合は、ローカル コード実行も実現できる可能性があります。

### <a name="other-dataadapter-types"></a>その他の DataAdapter 型

サードパーティによる `DataAdapter` の実装では、信頼されていない入力に対して提供するセキュリティ保証について、独自の評価を行う必要があります。 .NET では、これらの実装に関する安全性についてどのような保証も行うことはできません。

<a name="dsrdtr"></a>

## <a name="datasetreadxml-and-datatablereadxml"></a>DataSet.ReadXml と DataTable.ReadXml

`DataSet.ReadXml` メソッドと `DataTable.ReadXml` メソッドは、信頼されていない入力で使用するときは安全ではありません。 代わりにこのドキュメントで後述する代替手段のいずれかの使用を検討することを強くお勧めします。

`DataSet.ReadXml` と `DataTable.ReadXml` の実装は、もともと、シリアル化の脆弱性がよく理解された脅威カテゴリになる前に作成されました。 このため、そのコードは現在のセキュリティのベスト プラクティスに従っていません。 これらの API は、攻撃者が Web アプリに対して DoS 攻撃を実行するためのベクトルとして使用できます。 これらの攻撃によって、Web サービスが応答しなくなったり、予期しないプロセスの終了が発生したりする可能性があります。 フレームワークでは、これらの攻撃カテゴリに対する軽減策が提供されず、.NET ではこの動作は "仕様" と見なされます。

.NET では、`DataSet.ReadXml` および `DataTable.ReadXml` での情報漏えいやリモート コード実行などの一部の問題を軽減するために、セキュリティ更新プログラムがリリースされています。 .NET のセキュリティ更新プログラムでは、これらの脅威カテゴリに対する完全な保護が提供されない場合があります。 コンシューマーは、個々のシナリオを評価し、これらのリスクに対する潜在的な危険を検討する必要があります。

コンシューマーは、これらの API に対するセキュリティ更新プログラムが、アプリケーションの互換性に影響する場合があることに注意する必要があります。 さらに、これらの API には .NET でセキュリティ更新プログラムを実質的に公開できない新しい脆弱性が検出される可能性があります。

これらの API のコンシューマーには、次のいずれかをお勧めします。

* 後で説明するいずれかの代替手段を使用することを検討します。
* アプリで個々のリスク評価を実行します。

これらの API を利用するかどうかの判断に関する責任は、すべてコンシューマーにあります。 コンシューマーは、これらの API の使用に伴う可能性のある、規制要件を含む、セキュリティ、技術的、および法的リスクを評価する必要があります。

## <a name="dataset-and-datatable-via-aspnet-web-services-or-wcf"></a>ASP.NET Web サービスまたは WCF による DataSet と DataTable

次のコードで示すように、ASP.NET (SOAP) Web サービスで `DataSet` または `DataTable` のインスタンスを受け入れることができます。

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(DataTable dataTable)
    {
        /* Web method implementation. */
    }
}
```

これのバリエーションとしては、`DataSet` または `DataTable` をパラメーターとして直接受け入れるのではなく、次のコードで示すように、SOAP でシリアル化されたオブジェクト グラフ全体の一部として受け入れます。

```cs
using System.Data;
using System.Web.Services;

[WebService(Namespace = "http://contoso.com/")]
public class MyService : WebService
{
    [WebMethod]
    public string MyWebMethod(MyClass data)
    {
        /* Web method implementation. */
    }
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

または、ASP.NET Web サービスの代わりに WCF を使用します。

```cs
using System.Data;
using System.ServiceModel;

[ServiceContract(Namespace = "http://contoso.com/")]
public interface IMyContract
{
    [OperationContract]
    string MyMethod(DataTable dataTable);
    [OperationContract]
    string MyOtherMethod(MyClass data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

これらのどのケースでも、脅威モデルとセキュリティの保証は「[DataSet.ReadXml と DataTable.ReadXml section](#dsrdtr)」セクションと同じです。

## <a name="deserialize-a-dataset-or-datatable-via-xmlserializer"></a>XmlSerializer を使用して DataSet または DataTable を逆シリアル化する

開発者は、次のコードで示すように、`XmlSerializer` を使用して `DataSet` や `DataTable` のインスタンスを逆シリアル化できます。

```cs
using System.Data;
using System.IO;
using System.Xml.Serialization;

public DataSet PerformDeserialization1(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(DataSet));
    return (DataSet)serializer.Deserialize(stream);
}

public MyClass PerformDeserialization2(Stream stream) {
    XmlSerializer serializer = new XmlSerializer(typeof(MyClass));
    return (MyClass)serializer.Deserialize(stream);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

これらのケースでも、脅威モデルとセキュリティの保証は「[DataSet.ReadXml と DataTable.ReadXml section](#dsrdtr)」セクションと同じです

## <a name="deserialize-a-dataset-or-datatable-via-jsonconvert"></a>JsonConvert を使用して DataSet または DataTable を逆シリアル化する

一般的なサードパーティの Newtonsoft ライブラリ [JSON.NET](https://www.newtonsoft.com/json) を使用すると、次のコードで示すように、`DataSet` および `DataTable` のインスタンスを逆シリアル化できます。

```cs
using System.Data;
using Newtonsoft.Json;

public DataSet PerformDeserialization1(string json) {
    return JsonConvert.DeserializeObect<DataSet>(data);
}

public MyClass PerformDeserialization2(string json) {
    return JsonConvert.DeserializeObect<MyClass>(data);
}

public class MyClass
{
    // Property of type DataTable, automatically serialized and
    // deserialized as part of the overall MyClass payload.
    public DataTable MyDataTable { get; set; }
}
```

この方法で信頼されていない JSON BLOB から `DataSet` または `DataTable` を逆シリアル化することは、安全ではありません。 このパターンは、サービス拒否攻撃に対して脆弱です。 このような攻撃によって、アプリがクラッシュしたり、応答しなくなったりする可能性があります。

> [!NOTE]
> Microsoft では、_Newtonsoft.Json_ のようなサードパーティ製ライブラリの実装については、保証もサポートも行いません。 この情報は完全を期すために提供されており、このドキュメントの執筆時点の正確な情報です。

## <a name="deserialize-a-dataset-or-datatable-via-binaryformatter"></a>BinaryFormatter を使用して DataSet または DataTable を逆シリアル化する

開発者は、`BinaryFormatter`、`NetDataContractSerializer`、`SoapFormatter`、または関連する "***安全でない***" フォーマッタを使用して、信頼されていないペイロードから `DataSet` または `DataTable` のインスタンスを逆シリアル化しないでください。

* これは、完全なリモート コード実行攻撃の影響を受けやすくなります。
* このような攻撃を防ぐには、カスタム `SerializationBinder` を使用するだけでは不十分です。

## <a name="safe-replacements"></a>安全な置換

次のいずれかのアプリの場合:

* .asmx SOAP エンドポイントまたは WCF エンドポイントを通して `DataSet` または `DataTable` を受け入れる。
* 信頼されていないデータを `DataSet` または `DataTable` のインスタンスに逆シリアル化する。

[Entity Framework](/ef) を使用するようにオブジェクト モデルを置き換えることを検討してください。 Entity Framework:

* リレーショナル データを表すことができる、高度な最新のオブジェクト指向フレームワークです。
* データベース プロバイダーの[さまざまなエコシステム](/ef/core/providers/)を使用して、Entity Framework オブジェクト モデルによるデータベース クエリを簡単に射影できます。
* 信頼されていないソースからデータを逆シリアル化するときに、組み込みの保護が提供されます。

`.aspx` SOAP エンドポイントを使用するアプリの場合、[WCF](/dotnet/framework/wcf/) を使用するようにそれらのエンドポイントを変更することを検討してください。 WCF は、`.asmx` Web サービスに対する、より完全な機能を備えた代替手段です。 既存の呼び出し元との互換性のため、WCF エンドポイントは [SOAP 経由で公開できます](../../../wcf/feature-details/how-to-expose-a-contract-to-soap-and-web-clients.md)。
