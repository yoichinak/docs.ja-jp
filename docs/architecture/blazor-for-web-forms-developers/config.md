---
title: アプリの構成
description: 構成マネージャーを使用せずに Blazor アプリを構成する方法について説明します。
author: csharpfritz
ms.author: jefritz
ms.date: 04/01/2020
ms.openlocfilehash: c780a395f72e2520af86c20c7f6618953a528ff7
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588249"
---
# <a name="app-configuration"></a>アプリの構成

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Web フォームでアプリ構成を読み込む主な方法は、サーバー上の*web.config*ファイル&mdash;または*web.config*によって参照される関連する構成ファイルのエントリを使用することです。静的`ConfigurationManager`オブジェクトを使用して、アプリ設定、データ リポジトリ接続文字列、およびアプリに追加されるその他の拡張構成プロバイダーと対話できます。 次のコードに示すように、アプリの構成との相互作用を確認するのが一般的です。

```csharp
var configurationValue = ConfigurationManager.AppSettings["ConfigurationSettingName"];
var connectionString = ConfigurationManager.ConnectionStrings["MyDatabaseConnectionName"].ConnectionString;
```

ASP.NETコアとサーバー側の Blazor を使用すると、アプリが Windows IIS サーバーでホストされている場合 *、web.config*ファイルが存在する場合があります。 ただし、この構成との`ConfigurationManager`対話は行われず、他のソースからより構造化されたアプリ構成を受け取ることができます。 構成がどのように収集され *、web.config*ファイルから構成情報にアクセスする方法について説明します。

## <a name="configuration-sources"></a>構成元

ASP.NET Core では、アプリに使用する構成ソースが多数あると認識しています。 フレームワークは、既定でこれらの機能を最大限に提供しようとします。 構成は、ASP.NET Core によってこれらのさまざまなソースから読み取られ、集計されます。 後で同じコンフィギュレーション キーに対して読み込まれた値は、以前の値よりも優先されます。

ASP.NET Core は、クラウド対応で、オペレーターと開発者の両方にとってアプリの構成を容易にするように設計されています。 ASP.NET Core は環境に対応しており、お客様または`Production``Development`環境で実行されているかどうかを認識します。 システム環境変数に環境標識が`ASPNETCORE_ENVIRONMENT`設定されます。 値が設定されていない場合、アプリはデフォルトで`Production`環境内で実行されます。

アプリは、環境名に基づいて複数のソースから構成をトリガーし、追加できます。 デフォルトでは、以下のリソースから構成がリストされた順にロードされます。

1. *存在する場合は、ファイルを指定*します。
1. *アプリ設定。{ENVIRONMENT_NAME}.json*ファイルが存在する場合
1. ディスク上のユーザー シークレット ファイル (存在する場合)
1. 環境変数
1. コマンド ライン引数

## <a name="appsettingsjson-format-and-access"></a>フォーマットとアクセス

*appsettings.json*ファイルは、次の JSON のように構造化された値を使用して階層構造にすることができます。

```json
{
  "section0": {
    "key0": "value",
    "key1": "value"
  },
  "section1": {
    "key0": "value",
    "key1": "value"
  }
}
```

上記の JSON と共に提供された場合、構成システムは子の値を平坦化し、その完全に修飾された階層パスを参照します。 コロン (`:`) 文字は、階層内の各プロパティを区切ります。 たとえば、コンフィギュレーション キー`section1:key0`はオブジェクト リテラル`section1`の`key0`値にアクセスします。

## <a name="user-secrets"></a>ユーザーシークレット

ユーザーの秘密は次のとおりです。

* 開発者のワークステーションの JSON ファイルに格納される構成値 (アプリ開発フォルダーの外部)。
* 環境で実行されている場合にのみ`Development`ロードされます。
* 特定のアプリに関連付けられます。
* .NET Core CLI の`user-secrets`コマンドで管理されます。

次のコマンドを実行して、シークレット ストレージ`user-secrets`用にアプリを構成します。

```dotnetcli
dotnet user-secrets init
```

上記のコマンドは、プロジェクト`UserSecretsId`ファイルに要素を追加します。 要素には、アプリにシークレットを関連付けるために使用される GUID が含まれています。 その後、コマンドを使用してシークレット`set`を定義できます。 次に例を示します。

```dotnetcli
dotnet user-secrets set "Parent:ApiKey" "12345"
```

上記のコマンドは、値`Parent:ApiKey`を持つ開発者のワークステーションでコンフィギュレーション キーを使用`12345`できるようにします。

ユーザー シークレットの作成、保存、および管理の詳細については[、「ASP.NET Core ドキュメントの開発におけるアプリ シークレットの安全な保管](/aspnet/core/security/app-secrets)」を参照してください。

## <a name="environment-variables"></a>環境変数

アプリ構成に読み込まれる値の次のセットは、システムの環境変数です。 システムのすべての環境変数設定に、構成 API を通じてアクセスできるようになりました。 階層値は、アプリ内で読み取るときに、フラット化され、コロン文字で区切られます。 ただし、一部のオペレーティング システムでは、コロン文字環境変数名を使用できません。 ASP.NET Core は、二重アンダースコア ( )`__`を持つ値がアクセスされたときにコロンに変換することで、この制限に対処します。 上記`Parent:ApiKey`のユーザー シークレット セクションの値は、環境変数`Parent__ApiKey`で上書きできます。

## <a name="command-line-arguments"></a>コマンド ライン引数

アプリの起動時に、構成をコマンド ライン引数として指定することもできます。 設定する構成値の名前`--`と構成する値を示`/`すには、ダブルダッシュ () またはスラッシュ () を使用します。 構文は、次のコマンドに似ています。

```dotnetcli
dotnet run CommandLineKey1=value1 --CommandLineKey2=value2 /CommandLineKey3=value3
dotnet run --CommandLineKey1 value1 /CommandLineKey2 value2
dotnet run Parent:ApiKey=67890
```

## <a name="the-return-of-webconfig"></a>web.config の戻り値

IIS 上の Windows にアプリを展開した場合でも *、web.config*ファイルは引き続き IIS を構成してアプリを管理します。 既定では、IIS は ASP.NET コア モジュール (ANCM) への参照を追加します。 ANCM は、Kestrel Web サーバーの代わりにアプリをホストするネイティブ IIS モジュールです。 この*web.config*セクションは、次の XML マークアップに似ています。

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <location path="." inheritInChildApplications="false">
    <system.webServer>
      <handlers>
        <add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModuleV2" resourceType="Unspecified" />
      </handlers>
      <aspNetCore processPath=".\MyApp.exe"
                  stdoutLogEnabled="false"
                  stdoutLogFile=".\logs\stdout"
                  hostingModel="inprocess" />
    </system.webServer>
  </location>
</configuration>
```

アプリケーション固有の構成は、`environmentVariables``aspNetCore`要素内の要素を入れ子にすることで定義できます。 このセクションで定義された値は、ASP.NET Core アプリに環境変数として表示されます。 環境変数は、アプリの起動のそのセグメント中に適切に読み込まれます。

```xml
<aspNetCore processPath="dotnet"
      arguments=".\MyApp.dll"
      stdoutLogEnabled="false"
      stdoutLogFile=".\logs\stdout"
      hostingModel="inprocess">
  <environmentVariables>
    <environmentVariable name="ASPNETCORE_ENVIRONMENT" value="Development" />
    <environmentVariable name="Parent:ApiKey" value="67890" />
  </environmentVariables>
</aspNetCore>
```

## <a name="read-configuration-in-the-app"></a>アプリでの構成の読み取り

ASP.NET Core は、インターフェイス<xref:Microsoft.Extensions.Configuration.IConfiguration>を通じてアプリの構成を提供します。 この構成インターフェイスは、Blazor コンポーネント、Blazor ページ、および構成にアクセスする必要があるその他のASP.NETコア管理クラスによって要求される必要があります。 ASP.NET Core フレームワークは、このインターフェイスに、先ほど構成された解決済みの構成を自動的に設定します。 Blazor ページまたはコンポーネントの Razor マークアップで *、.razor*ファイル`IConfiguration`の先頭に`@inject`次のようなディレクティブをオブジェクトに挿入できます。

```razor
@inject IConfiguration Configuration
```

このステートメントを使用すると、Razor テンプレート`IConfiguration`の`Configuration`残りの部分でオブジェクトを変数として使用できるようになります。

個々の構成設定は、インデクサー パラメーターとして求める構成設定階層を指定することによって読み取ることができます。

```csharp
var mySetting = Configuration["section1:key0"];
```

このメソッドを使用して、前の<xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A>例から section1 の構成を取得`GetSection("section1")`する構文と類似した構文を使用して、特定の場所にあるキーのコレクションを取得することにより、構成セクション全体をフェッチできます。

## <a name="strongly-typed-configuration"></a>厳密に型指定された構成

Web フォームでは、型と関連付けられた型から継承した厳密に型指定<xref:System.Configuration.ConfigurationSection>された構成型を作成できました。 では`ConfigurationSection`、いくつかのビジネス ルールと、それらの構成値の処理を構成できます。

ASP.NET Core では、構成値を受け取るクラス階層を指定できます。 これらのクラス:

* 親クラスから継承する必要はありません。
* キャプチャする`public`構成構造のプロパティと型参照に一致するプロパティを含める必要があります。

以前の*appsettings.json*サンプルでは、値をキャプチャする次のクラスを定義できます。

```csharp
public class MyConfig
{
    public MyConfigSection section0 { get; set;}

    public MyConfigSection section1 { get; set;}
}

public class MyConfigSection
{
    public string key0 { get; set; }

    public string key1 { get; set; }
}
```

このクラス階層は、`Startup.ConfigureServices`メソッドに次の行を追加することで設定できます。

```csharp
services.Configure<MyConfig>(Configuration);
```

アプリの残りの部分では、厳密に型指定された構成設定を受け`@inject`取る入力パラメーターをクラス`IOptions<MyConfig>`または Razor テンプレートの型のディレクティブに追加できます。 プロパティ`IOptions<MyConfig>.Value`は、構成設定`MyConfig`から設定された値を生成します。

```razor
@inject IOptions<MyConfig> options
@code {
    var MyConfiguration = options.Value;
    var theSetting = MyConfiguration.section1.key0;
}
```

オプション機能の詳細については、core ドキュメントの[オプション パターンASP.NET](/aspnet/core/fundamentals/configuration/options#options-interfaces)参照してください。

>[!div class="step-by-step"]
>[前へ](middleware.md)
>[次へ](security-authentication-authorization.md)
