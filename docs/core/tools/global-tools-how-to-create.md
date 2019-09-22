---
title: .NET Core グローバル ツールの作成方法
description: グローバル ツールを作成する方法について説明します。 グローバル ツールは、.NET Core CLI を介してインストールされるコンソール アプリケーションです。
author: Thraka
ms.author: adegeo
ms.date: 08/22/2018
ms.openlocfilehash: 5c2b1e459f0308f5f96eb041c10f4d7a7ae0ca20
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117443"
---
# <a name="create-a-net-core-global-tool-using-the-net-core-cli"></a>.NET Core CLI を使用して .NET Core グローバル ツールを作成する

この記事では、.NET Core グローバル ツールを作成してパッケージ化する方法について説明します。 .NET Core CLI を使用すると、他のユーザーが簡単にインストールして実行できるコンソール アプリケーションをグローバル ツールとして作成できます。 .NET Core グローバル ツールは、.NET Core CLI からインストールされる NuGet パッケージです。 グローバル ツールの詳細については、「[.NET Core グローバル ツールの概要](global-tools.md)」を参照してください。

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="create-a-project"></a>プロジェクトを作成する

この記事では、プロジェクトの作成と管理に .NET Core CLI を使用します。

ここでの例のツールは、ASCII ボットを生成してメッセージを出力するコンソール アプリケーションです。 まず、新しい .NET Core コンソール アプリケーションを作成します。

```dotnetcli
dotnet new console -o botsay
```

前のコマンドで作成した `botsay` ディレクトリに移動します。

## <a name="add-the-code"></a>コードの追加

`vim` や [Visual Studio Code](https://code.visualstudio.com/) など、使い慣れたテキスト エディターで `Program.cs` ファイルを開きます。

次の `using` ディレクティブをファイルの先頭に追加すると、アプリケーションのバージョン情報を表示するコードを短くすることができます。

```csharp
using System.Reflection;
```

次に、`Main` メソッドに移動します。 メソッドを次のコードに置き換えて、アプリケーションのコマンドライン引数を処理します。 引数が渡されなかった場合、短いヘルプ メッセージが表示されます。 それ以外の場合、それらの引数はすべて文字列に変換され、ボットで出力されます。

```csharp
static void Main(string[] args)
{
    if (args.Length == 0)
    {
        var versionString = Assembly.GetEntryAssembly()
                                .GetCustomAttribute<AssemblyInformationalVersionAttribute>()
                                .InformationalVersion
                                .ToString();

        Console.WriteLine($"botsay v{versionString}");
        Console.WriteLine("-------------");
        Console.WriteLine("\nUsage:");
        Console.WriteLine("  botsay <message>");
        return;
    }

    ShowBot(string.Join(' ', args));
}
```

### <a name="create-the-bot"></a>ボットを作成する

次に、文字列パラメーターを受け取る `ShowBot` という新しいメソッドを追加します。 このメソッドは、メッセージと ASCII ボットを出力します。 ASCII ボットのコードは、[dotnetbot](https://github.com/dotnet/core/blob/master/samples/dotnetsay/Program.cs) サンプルの一部です。

```csharp
static void ShowBot(string message)
{
    string bot = $"\n        {message}";
    bot += @"
    __________________
                      \
                       \
                          ....
                          ....'
                           ....
                        ..........
                    .............'..'..
                 ................'..'.....
               .......'..........'..'..'....
              ........'..........'..'..'.....
             .'....'..'..........'..'.......'.
             .'..................'...   ......
             .  ......'.........         .....
             .    _            __        ......
            ..    #            ##        ......
           ....       .                 .......
           ......  .......          ............
            ................  ......................
            ........................'................
           ......................'..'......    .......
        .........................'..'.....       .......
     ........    ..'.............'..'....      ..........
   ..'..'...      ...............'.......      ..........
  ...'......     ...... ..........  ......         .......
 ...........   .......              ........        ......
.......        '...'.'.              '.'.'.'         ....
.......       .....'..               ..'.....
   ..       ..........               ..'........
          ............               ..............
         .............               '..............
        ...........'..              .'.'............
       ...............              .'.'.............
      .............'..               ..'..'...........
      ...............                 .'..............
       .........                        ..............
        .....
";
    Console.WriteLine(bot);
}
```

### <a name="test-the-tool"></a>ツールをテストする

プロジェクトを実行して出力を確認します。 次のようにコマンドラインを変えて、異なる結果を表示してみてください。

```dotnetcli
dotnet run
dotnet run -- "Hello from the bot"
dotnet run -- hello from the bot
```

区切り記号 `--` の後の引数は、すべてアプリケーションに渡されます。

## <a name="setup-the-global-tool"></a>グローバル ツールを設定する

アプリケーションをパッケージ化してグローバル ツールとして配布する前に、プロジェクト ファイルを変更する必要があります。 `botsay.csproj` ファイルを開き、3 つの新しい XML ノードを `<Project><PropertyGroup>` ノードに追加します。

- `<PackAsTool>`\
[必須] アプリケーションがグローバル ツールとしてインストールされるようにパッケージ化されることを示します。

- `<ToolCommandName>`\
[省略可能] ツールの代替名。指定しない場合、プロジェクト ファイル名に従ってツールのコマンド名が付けられます。 1 つのパッケージに複数のツールを含めることができます。一意のわかりやすい名前を選択すると、同じパッケージ内の他のツールと区別しやすくなります。

- `<PackageOutputPath>`\
[省略可能] NuGet パッケージが生成される場所。 NuGet パッケージは、.NET Core CLI グローバル ツールがツールのインストールに使用するパッケージです。

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp2.1</TargetFramework>

    <PackAsTool>true</PackAsTool>
    <ToolCommandName>botsay</ToolCommandName>
    <PackageOutputPath>./nupkg</PackageOutputPath>

  </PropertyGroup>

</Project>
```

`<PackageOutputPath>` は省略可能ですが、この例では使用します。 必ず `<PackageOutputPath>./nupkg</PackageOutputPath>` を設定してください。

次に、アプリケーション用の NuGet パッケージを作成します。

```dotnetcli
dotnet pack
```

`botsay.1.0.0.nupkg` ファイルは、`botsay.csproj` ファイルの `<PackageOutputPath>` XML 値で識別されるフォルダー (この例では `./nupkg` フォルダー) に作成されます。 これにより、インストールとテストが簡単になります。 ツールを公開する場合は、<https://www.nuget.org> にアップロードしてください。 NuGet でツールを使用できるようになると、開発者は [dotnet tool install](dotnet-tool-install.md) コマンドの `--global` オプションを使用してツールのユーザー全体のインストールを実行できます。

パッケージを用意できたので、そのパッケージからツールをインストールします。

```dotnetcli
dotnet tool install --global --add-source ./nupkg botsay
```

`--add-source` パラメーターで、NuGet パッケージの追加のソース フィードとして `./nupkg` フォルダー (ここでは `<PackageOutputPath>` フォルダー) を一時的に使用するように .NET CoreCLI に指示します。 グローバル ツールのインストールの詳細については、「[.NET Core グローバル ツールの概要](global-tools.md)」を参照してください。

インストールが成功すると、ツールの呼び出しに使用したコマンドとインストールされたバージョンを示す、次の例のようなメッセージが表示されます。

```output
You can invoke the tool using the following command: botsay
Tool 'botsay' (version '1.0.0') was successfully installed.
```

これで、`botsay` を入力してツールから応答を取得できるようになりました。

> [!NOTE]
> インストールは成功しても `botsay` コマンドを使用できない場合は、新しい端末を開いて PATH を更新する必要があります。

## <a name="remove-the-tool"></a>ツールを削除する

ツールの実験を完了したら、次のコマンドでツールを削除することができます。

```dotnetcli
dotnet tool uninstall -g botsay
```
