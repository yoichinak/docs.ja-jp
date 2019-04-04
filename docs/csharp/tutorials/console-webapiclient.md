---
title: .NET Core を使用した REST クライアントの作成
description: このチュートリアルでは、.NET Core と C# 言語のさまざまな機能を説明します。
ms.date: 03/06/2017
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: a375215f2d31845333290c85f7701c1a7dfbe780
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412306"
---
# <a name="rest-client"></a>REST クライアント

## <a name="introduction"></a>はじめに

このチュートリアルでは、.NET Core と C# 言語のさまざまな機能を説明します。 内容は以下のとおりです。

* .NET Core コマンド ライン インターフェイス (CLI) の基本
* C# 言語機能の概要
* NuGet での依存関係の管理
* HTTP 通信
* JSON 情報の処理
* 属性を使用した構成の管理

GitHub 上の REST サービスに対して HTTP 要求を発行するアプリケーションをビルドします。 JSON 形式で情報を読み取り、その JSON パケットを C# オブジェクトに変換します。 最後に、C# オブジェクトを操作する方法について説明します。

このチュートリアルには、多くの機能が含まれています。 それらを 1 つずつビルドしてみましょう。

このトピックの[最終的なサンプル](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)も参照したい方は、ダウンロードできます。 ダウンロード方法については、「[サンプルおよびチュートリアル](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)」を参照してください。

## <a name="prerequisites"></a>必須コンポーネント

お使いのコンピューターを、.NET Core が実行されるように設定する必要があります。 インストールの手順については、[.NET Core](https://www.microsoft.com/net/core) のページを参照してください。 このアプリケーションは、Windows、Linux、macOS または Docker コンテナーで実行できます。
お好みのコード エディターをインストールしてください。 次の説明では、オープン ソースのクロス プラットフォーム エディターである [Visual Studio Code](https://code.visualstudio.com/) を使用しています。 しかし、他の使い慣れたツールを使用しても構いません。

## <a name="create-the-application"></a>アプリケーションを作成する

最初に新しいアプリケーションを作成します。 コマンド プロンプトを開き、アプリケーション用の新しいディレクトリを作成します。 それを、現在のディレクトリとしてください。 コマンド プロンプトで `dotnet new console` のコマンドを入力します。 これで、基本的な "Hello World" アプリケーションのスターター ファイルが作成されます。

変更を加える前に、このシンプルな Hello World アプリケーションを実行する手順を見ていきましょう。 アプリケーション作成後、コマンド プロンプトで「`dotnet restore`」 ([注記を参照](#dotnet-restore-note)) と入力します。 このコマンドにより、NuGet パッケージの復元処理が実行されます。 NuGet は .NET パッケージ マネージャーです。 このコマンドにより、プロジェクトの依存関係のうち欠落しているものがすべてダウンロードされます。 これは新しいプロジェクトなので、依存関係は何もなく、最初の実行で .NET Core フレームワークがダウンロードされます。 この最初の手順の後は、新しい依存パッケージを追加するときに `dotnet restore` ([注記を参照](#dotnet-restore-note)) を実行するか、依存関係のいずれかのバージョンを更新する必要があるだけです。

パッケージを復元したら、`dotnet build` を実行します。 これにより、ビルド エンジンが実行され、アプリケーションが作成されます。 最後に、`dotnet run` を実行してアプリケーションを実行します。

## <a name="adding-new-dependencies"></a>新しい依存関係を追加する

.NET Core の重要な設計目標の 1 つは、.NET インストール サイズを最小限に抑えることです。 その一部の機能のための追加ライブラリがアプリケーションで必要な場合は、C# プロジェクト (\*.csproj) ファイルにそれらの依存関係を追加します。 ここで示す例の場合は、`System.Runtime.Serialization.Json` パッケージを追加して、アプリケーションが JSON 応答を処理できるようにする必要があります。

`csproj` プロジェクト ファイルを開きます。 ファイルの最初の行は次のように表示されます。

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

この行の直後に次のコードを追加します。

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup>
```

ほとんどのコード エディターでは、これらのライブラリの複数のバージョンの入力候補が表示されます。 通常は、追加するパッケージの最新バージョンを使用します。 ただし、すべてのパッケージのバージョンが一致しており、.NET Core アプリケーション フレームワークのバージョンとも一致していることを確認してください。

これらの変更を加えた後で、`dotnet restore` ([注記を参照](#dotnet-restore-note)) をもう一度実行して、システムにパッケージがインストールされるようにします。

## <a name="making-web-requests"></a>Web 要求を作成する

Web サイトからデータの取得を開始する準備ができました。 このアプリケーションでは、[GitHub API](https://developer.github.com/v3/) から情報を読み取ります。 [.NET Foundation](https://www.dotnetfoundation.org/) にあるプロジェクトに関する情報を読み取ります。 最初に、プロジェクトに関する情報を取得する GitHub API に対する要求を作成します。 使用するエンドポイントは [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos) です。 HTTP GET 要求を使用して、これらのプロジェクトに関する情報をすべて取得します。
HTTP GET 要求はブラウザーでも使用されるので、ブラウザーに URL を貼り付けて、取得および処理する情報を確認できます。

<xref:System.Net.Http.HttpClient> クラスを使用して Web 要求を作成します。 最新のすべての .NET API と同様に、<xref:System.Net.Http.HttpClient> は実行時間の長い API の非同期メソッドだけをサポートします。
最初に非同期メソッドを作成します。 アプリケーションの機能をビルドする際に実装を記述します。 最初に、プロジェクト ディレクトリ内の `program.cs` ファイルを開き、`Program` クラスに次のメソッドを追加します。

```csharp
private static async Task ProcessRepositories()
{
}
```

`Main` メソッドの先頭に `using` ステートメントを追加して、C# コンパイラに <xref:System.Threading.Tasks.Task> 型を認識させる必要があります。

```csharp
using System.Threading.Tasks;
```

この時点でプロジェクトをビルドすると、このメソッドに対して警告が生成されます。これは、`await` 演算子がメソッドに含まれておらず、メソッドが同期的に実行されるためです。 現時点ではこの警告を無視してください。`await` 演算子は、メソッドを記述する際に追加します。

次に、`namespace` ステートメントに定義されている名前空間の名前を、既定値の `ConsoleApp` から `WebAPIClient` に変更します。 後から、この名前空間で `repo` クラスを定義します。

次に、`Main` メソッドを更新してこのメソッドを呼び出します。 `ProcessRepositories` メソッドはタスクを返します。そのタスクが完了する前にプログラムを終了しないでください。 そのため、`Wait` メソッドを使用してブロックし、タスクの完了を待機する必要があります。

```csharp
static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

これで、何も実行せず、非同期的に実行されるプログラムの準備ができました。 これを改善しましょう。

まず、Web からデータを取得できるオブジェクトが必要です。この条件に合うものとして、<xref:System.Net.Http.HttpClient> を使用できます。 このオブジェクトは要求と応答を処理します。 Program.cs ファイル内の `Program` クラスで該当する型の単一のインスタンスをインスタンス化します。

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static void Main(string[] args)
        {
            //...
        }
    }
}
```

`ProcessRepositories` メソッドに戻って、最初のバージョンのプログラムを記述します。

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

また、ファイルの先頭に 2 つの新しい using ステートメントを追加して、プログラムをコンパイルする必要があります。

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

この最初のバージョンでは、.NET Foundation にあるすべてのリポジトリのリストを読み取る Web 要求を作成します  (.NET Foundation の gitHub ID は "dotnet" です)。 最初の数行では、この要求の <xref:System.Net.Http.HttpClient> を設定します。 最初は、GitHub の JSON 応答を受け入れるように構成されます。
この形式は単なる JSON です。 次の行では、このオブジェクトからのすべての要求にユーザー エージェント ヘッダーを追加します。 これらの 2 つのヘッダーは、GitHub サーバー コードによってチェックされ、GitHub から情報を取得するために必要です。

<xref:System.Net.Http.HttpClient> を構成したら、Web 要求を作成して応答を取得します。 この最初のバージョンでは、<xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> 簡易メソッドを使います。 この簡易メソッドは、Web 要求を作成するタスクを開始し、要求が返されると応答ストリームを読み取って、ストリームからコンテンツを抽出します。 応答の本文は <xref:System.String> として返されます。 この文字列は、タスクが完了すると使用できます。

このメソッドの最後の 2 行は、そのタスクを待機し、コンソールに応答を出力します。
アプリケーションをビルドして実行してください。 `ProcessRepositories` に `await` 演算子が含まれているため、ビルドの警告が表示されなくなりました。 JSON 形式の長いテキストが表示されます。

## <a name="processing-the-json-result"></a>JSON の結果を処理する

この時点では、Web サーバーからの応答を取得し、その応答に含まれているテキストを表示するコードの記述が完了しています。 次に、JSON 応答を C# オブジェクトに変換します。

JSON シリアライザーは、JSON データを C# オブジェクトに変換します。 最初のタスクでは、この応答から使用する情報を格納する C# クラスの型を定義します。 最初に、リポジトリの名前を含むシンプルな C# 型を使用します。

```csharp
using System;

namespace WebAPIClient
{
    public class repo
    {
        public string name;
    }
}
```

"repo.cs" という新しいファイルに上記のコードを記述します。 このバージョンのクラスは、JSON データを処理する最もシンプルなパスを表します。 クラス名とメンバー名は、C# の規約に従うのではなく、JSON パケットで使用される名前に一致します。 後でいくつかの構成属性を指定して、これを修正します。 このクラスは、JSON のシリアル化と逆シリアル化に関する、もう一つの重要な特性を示しています:JSON パケット内のすべてのフィールドがこのクラスの一部というわけではありません。
JSON シリアライザーは、使用されているクラス型に含まれていない情報を無視します。
この機能により、JSON パケット内のフィールドのサブセットのみを操作する型を容易に作成できます。

型の作成が完了したら、逆シリアル化を実行します。 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> オブジェクトを作成する必要があります。 このオブジェクトは、取得する JSON パケットで必要な CLR 型を認識する必要があります。 GitHub からのパケットには一連のリポジトリが含まれているため、正しい型は `List<repo>` です。 次の行を `ProcessRepositories` メソッドに追加します。

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

2 つの新しい名前空間を使用しているため、次の行も追加する必要があります。

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

次に、シリアライザーを使用して、JSON を C# オブジェクトに変換します。 `ProcessRepositories` メソッド内の <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> の呼び出しを次の 2 行に置き換えます。

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> ではなく、<xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> が使用されていることをご確認ください。 シリアライザーは、文字列の代わりにストリームをソースとして使用します。 上記の 2 行目で使用されている C# 言語のいくつかの機能について説明します。 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> への引数は `await` 式です。 await 式は、コード内のほとんどの場所に表示される可能性があります (これまでは代入ステートメントの一部としてしか表示されていませんでした)。

次に、`as` 演算子がコンパイル時の型である `object` を `List<repo>` に変換します。
<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> の宣言は、<xref:System.Object?displayProperty=nameWithType> 型のオブジェクトが返されることを宣言しています。 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> は、構成時に指定した型 (このチュートリアルでは `List<repo>`) を返します。 変換が成功しなかった場合、`as` 演算子は例外をスローする代わりに `null` と評価します。

このセクションでの作業はほぼ完了です。 JSON を C# オブジェクトに変換したので、次は各リポジトリの名前を表示します。 次の行があるとします。

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

この行を次の行に置き換えます。

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

アプリケーションをコンパイルして実行します。 .NET Foundation に含まれるリポジトリの名前が出力されます。

## <a name="controlling-serialization"></a>シリアル化を制御する

機能を追加する前に、`repo` 型を処理して、その型が C# の標準的な規約に従うようにします。 そのためには、JSON シリアライザーの動作を制御する "*属性*" を使用して `repo` 型に注釈を設定します。 ここでは、これらの属性を使用して、JSON キー名と C# のクラスおよびメンバーの名前との間のマッピングを定義します。 使用する 2 つの属性は <xref:System.Runtime.Serialization.DataContractAttribute> と <xref:System.Runtime.Serialization.DataMemberAttribute> 属性です。 慣例により、すべての属性クラスはサフィックス `Attribute` で終わります。 ただし、属性の適用時にそのサフィックスを使用する必要はありません。

<xref:System.Runtime.Serialization.DataContractAttribute> 属性と <xref:System.Runtime.Serialization.DataMemberAttribute> 属性は別のライブラリにあるため、C# プロジェクト ファイルにそのライブラリを依存関係として追加する必要があります。 プロジェクト ファイルの `<ItemGroup>` セクションに次の行を追加します。

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

ファイルを保存したら、`dotnet restore` ([注記を参照](#dotnet-restore-note))を実行してこのパッケージを取得します。

次に、`repo.cs` ファイルを開きます。 パスカル ケースを使用するように名前を変更し、`Repository` という名前を記述します。 この型に JSON の "repo" ノードをマップするために、クラス宣言に <xref:System.Runtime.Serialization.DataContractAttribute> 属性を追加する必要があります。 属性の `Name` プロパティを、この型にマップする JSON ノードの名前に設定します。

```csharp
[DataContract(Name="repo")]
public class Repository
```

<xref:System.Runtime.Serialization.DataContractAttribute> は <xref:System.Runtime.Serialization> 名前空間のメンバーであるため、ファイルの先頭に適切な `using` ステートメントを追加する必要があります。

```csharp
using System.Runtime.Serialization;
```

`repo` クラスの名前を `Repository` に変更したので、Program.cs でも同じ名前の変更を行う必要があります (一部のエディターでは名前変更のリファクタリングがサポートされているため、この変更が自動的に行われます)。

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

次に、<xref:System.Runtime.Serialization.DataMemberAttribute> クラスを使用して、`name` フィールドで同じ変更を行います。 repo.cs の `name` フィールドの宣言を次のように変更してください。

```csharp
[DataMember(Name="name")]
public string Name;
```

この変更により、program.cs で各リポジトリの名前を記述するコードを変更する必要があります。

```csharp
Console.WriteLine(repo.Name);
```

`dotnet build` に続けて `dotnet run` を実行し、マッピングが正しいことを確認します。 前と同じ出力が表示されるはずです。 Web サーバーから他のプロパティを処理する前に、`Repository` クラスに対してもう 1 つの変更を行います。 `Name` メンバーはパブリックにアクセスできるフィールドです。 これはオブジェクト指向においては適切な手法でないため、このフィールドをプロパティに変更します。 プロパティの取得または設定の際に実行するコードは不要ですが、プロパティを変更すると、これらの変更を後から容易に追加できます (`Repository` クラスを使用するコードを中断する必要はありません)。

フィールド定義を削除して、"[自動実装プロパティ](../programming-guide/classes-and-structs/auto-implemented-properties.md)" に置き換えます。

```csharp
public string Name { get; set; }
```

コンパイラは、`get` アクセサーと `set` アクセサーの本文および名前を格納するプライベート フィールドを生成します。 次のようなコードを手動で入力できます。

```csharp
public string Name
{
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

新機能を追加する前に、もう 1 つの変更を行います。 `ProcessRepositories` メソッドは非同期作業を行って、リポジトリのコレクションを返すことができます。 そのメソッドから `List<Repository>` を返して、情報を記述するコードを `Main` メソッドに移動します。

結果が `Repository` オブジェクトのリストであるタスクを返すように `ProcessRepositories` のシグネチャを変更します。

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

続いて、JSON 応答の処理後にリポジトリを返します。

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

このメソッドを `async` とマークしたので、コンパイラは戻り値として `Task<T>` オブジェクトを生成します。
次に、`Main` メソッドを変更して、それらの結果をキャプチャし、各リポジトリ名をコンソールに書き込むようにします。 `Main` メソッドは次のようになります。

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

Task ブロックの `Result` プロパティへのアクセスは、タスクが完了するまでブロックされます。 通常、`ProcessRepositories` メソッドなどではタスクの完了に対して `await` の実行を選択しますが、`Main` メソッドでは許可されていません。

## <a name="reading-more-information"></a>詳細情報を確認する

最後に、GitHub API から送信される JSON パケット内のいくつかのプロパティを処理します。 すべてのプロパティを追加する必要はありませんが、いくつかのプロパティを追加することで C# 言語のさらなる機能を示すことができます。

最初に、いくつかの単純型を `Repository` クラスの定義に追加します。 そのクラスに次のプロパティを追加します。

```csharp
[DataMember(Name="description")]
public string Description { get; set; }

[DataMember(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[DataMember(Name="homepage")]
public Uri Homepage { get; set; }

[DataMember(Name="watchers")]
public int Watchers { get; set; }
```

これらのプロパティには、(JSON パケットに格納されている) 文字列型からターゲット型への組み込みの変換があります。 <xref:System.Uri> 型はおそらく初めて使用する型でしょう。 これは URI (ここでは URL) を表します。 `Uri` 型と `int` 型では、ターゲット型に変換しないデータが JSON パケットに含まれている場合、シリアル化アクションで例外がスローされます。

プロパティの追加が完了したら、それらの要素を表示するように `Main` メソッドを更新してください。

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```

最後の手順として、最後のプッシュ操作に関する情報を追加します。 この情報は、JSON 応答では次のように書式設定されます。

```json
2016-02-08T21:27:00Z
```

この形式は .NET の標準の <xref:System.DateTime> 形式に従っていません。 そのため、カスタムの変換メソッドを記述する必要があります。 また、`Repository` クラスのユーザーに公開されている未加工の文字列もおそらく不要でしょう。 この文字列も属性を使用して制御できます。 最初に、日時の文字列表現を `Repository` クラスに保持する `private` プロパティを定義します。

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<xref:System.Runtime.Serialization.DataMemberAttribute> 属性は、このプロパティがパブリック メンバーでないとしても処理する必要があることをシリアライザーに通知します。 次に、文字列を有効な <xref:System.DateTime> オブジェクトに変換してその <xref:System.DateTime> を返す読み取り専用のパブリック プロパティを記述する必要があります。

```csharp
[IgnoreDataMember]
public DateTime LastPush
{
    get
    {
        return DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
    }
}
```

上記の新しいコンストラクトについて詳しく見てみましょう。 `IgnoreDataMember` 属性は、JSON オブジェクトとの間でこの型の読み取りまたは書き込みを行わないようにシリアライザーに指示します。 このプロパティには `get` アクセサーだけが含まれています。 `set` アクセサーがない。 C# では、この方法で "*読み取り専用*" プロパティを定義します  (C# では "*書き込み専用*" プロパティを作成できますが、その値は制限されています)。<xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> メソッドは、指定された日付形式を使用して文字列を解析し、<xref:System.DateTime> オブジェクトを作成します。次に、`CultureInfo` オブジェクトを使用して `DateTime` にメタデータを追加します。 解析操作が失敗した場合、プロパティのアクセサーは例外をスローします。

<xref:System.Globalization.CultureInfo.InvariantCulture> を使用するには、`repo.cs` 内の `using` ステートメントに <xref:System.Globalization> 名前空間を追加する必要があります。

```csharp
using System.Globalization;
```

最後に、コンソールで出力ステートメントをもう 1 つ追加すれば、このアプリケーションを再度ビルドして実行する準備は完了です。

```csharp
Console.WriteLine(repo.LastPush);
```

以上で、作成してきたバージョンは[最終的なサンプル](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)と同じになるはずです。

## <a name="conclusion"></a>まとめ

このチュートリアルでは、Web 要求を作成する方法、結果を解析する方法、およびそれらの結果のプロパティを表示する方法を紹介しました。 また、依存関係として新しいパッケージをプロジェクトに追加しました。 さらに、オブジェクト指向の手法をサポートする C# 言語の一部の機能について確認しました。

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
