---
title: dotnet new のカスタム テンプレートを作成する
description: この楽しいチュートリアルで、dotnet new のカスタム テンプレートを作成する方法を学びましょう。
author: guardrex
ms.date: 08/12/2017
ms.custom: seodec18
ms.openlocfilehash: 3b45a24c8a249eeb99fb1a4b14918483b978980b
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57676448"
---
# <a name="create-a-custom-template-for-dotnet-new"></a>dotnet new のカスタム テンプレートを作成する

このチュートリアルでは、次の方法を紹介します。

- 既存のプロジェクトまたは新しいコンソール アプリ プロジェクトから基本テンプレートを作成する。
- nuget.org で、またはローカルの *nupkg* ファイルから配布用にテンプレートをパッケージ化する。
- nuget.org、ローカル *nupkg* ファイル、またはローカル ファイル システムからテンプレートをインストールする。
- テンプレートをアンインストールする。

完全なサンプルでチュートリアルを続行する場合は、[サンプル プロジェクト テンプレート](https://github.com/dotnet/dotnet-template-samples/tree/master/16-nuget-package)をダウンロードしてください。 サンプル テンプレートは NuGet 配布用に構成されています。

ダウンロードしたサンプルをファイル システム配布で使用する場合、次の操作を行います。

- サンプルの *content* フォルダーの中身を 1 つ上のレベルの *GarciaSoftware.ConsoleTemplate.CSharp* フォルダーに移動する。
- 空になった *content* フォルダーを削除する。
- *nuspec* ファイルを削除する。

## <a name="prerequisites"></a>必須コンポーネント

- [.NET Core 2.0 SDK](https://www.microsoft.com/net/core) 以降のバージョンをインストールします。
- 参照トピックの「[dotnet new のカスタム テンプレート](../tools/custom-templates.md)」を確認しておきます。

## <a name="create-a-template-from-a-project"></a>プロジェクトからテンプレートを作成する

コンパイルして実行できることが確認されている既存のプロジェクトを利用するか、ハード ドライブのフォルダーで新しいコンソール アプリ プロジェクトを作成します。 このチュートリアルでは、ユーザーのプロファイルの *Documents\Templates* に保存されている *GarciaSoftware.ConsoleTemplate.CSharp* をプロジェクト フォルダーとして想定しています。 チュートリアルのプロジェクト テンプレート名は、*\<会社名>.\<テンプレートの種類>.\<プログラミング言語>* という形式になりますが、プロジェクトとテンプレートには自由に名前を付けることができます。

1. *.template.config* という名前のプロジェクトのルートにフォルダーを追加します。
1. *.template.config* フォルダー内で、テンプレートを構成する *template.json* ファイルを作成します。 *template.json* ファイルの詳細情報とメンバー定義については、「[dotnet new のカスタム テンプレート](../tools/custom-templates.md#templatejson)」トピックと JSON Schema Store の [*template.json*](http://json.schemastore.org/template) スキーマを参照してください。

```json
{
    "$schema": "http://json.schemastore.org/template",
    "author": "Catalina Garcia",
    "classifications": [ "Common", "Console" ],
    "identity": "GarciaSoftware.ConsoleTemplate.CSharp",
    "name": "Garcia Software Console Application",
    "shortName": "garciaconsole"
}
```

テンプレートは完成となります。 この時点で、テンプレート配布の選択肢が 2 つ与えられます。 このチュートリアルを続行するには、いずれかのパスを選択します。

1. [NuGet 配布](#use-nuget-distribution): NuGet またはローカル *nupkg* ファイルからテンプレートをインストールし、インストールしたテンプレートを使用します。
2. [ファイル システム配布](#use-file-system-distribution)。

## <a name="use-nuget-distribution"></a>NuGet 配布を利用する

### <a name="pack-the-template-into-a-nuget-package"></a>テンプレートをパッケージ化し、NuGet パッケージを作成する

1. NuGet パッケージのフォルダーを作成します。 このチュートリアルでは、*GarciaSoftware.ConsoleTemplate.CSharp* フォルダーが使用されます。このフォルダーは、ユーザーのプロファイルの *Documents\NuGetTemplates* フォルダーの中に作成されています。 プロジェクト ファイルを保存する目的で、新しいテンプレート フォルダー内に *content* という名前のフォルダーを作成します。
1. 作成した *content* フォルダーに、プロジェクト フォルダーの中身を *.template.config/template.json* ファイルと共にコピーします。
1. *content* フォルダーの隣に、[*nuspec*](/nuget/create-packages/creating-a-package) ファイルを追加します。 nuspec ファイルは XML マニフェスト ファイルであり、パッケージの中身が記述され、NuGet パッケージの作成プロセスを実行します。

   ![NuGet パッケージのレイアウトを示すディレクトリ構造](./media/create-custom-template/nuget-directory-layout.png)

1. *nuspec* ファイルの **\<packageTypes>** 要素の中に、**\<packageType>** 要素を追加し、`name` 属性の値を `Template` にします。 *content* フォルダーと *nuspec* ファイルの両方を同じディレクトリに入れます。 下の表は、NuGet パッケージとしてテンプレートを生成するために必要な *nuspec* ファイルの最小要素をまとめたものです。

   | 要素            | 型   | 説明 |
   | ------------------ | ------ | ----------- |
   | **\<authors>**     | string | パッケージ作成者の一覧。コンマで区切られています。nuget.org のプロファイル名と一致します。作成者は nuget.org の NuGet ギャラリーに表示され、同じ作成者によるパッケージの相互参照に使用されます。 |
   | **\<description>** | string | UI 画面用のパッケージの長い説明。 |
   | **\<id>**          | string | パッケージの識別子で、大文字と小文字が区別されます。nuget.org 全体で、あるいはパッケージが置かれるギャラリーで一意でなければなりません。 ID には、URL によっては無効なスペースや文字が含まれることがあります。また、一般的に、.NET の名前空間ルールに従います。 手引きについては、「[Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number)」 (一意のパッケージ識別子を選択し、バージョン番号を設定する) をご覧ください。 |
   | **\<packageType>** | string | この要素を **\<metadata>** 要素の中の **\<packageTypes>** 要素内に置きます。 **\<packageType>** 要素の `name` 属性を `Template` に設定します。 |
   | **\<version>**     | string | パッケージのバージョン。major.minor.patch パターンになります。 [プレリリース バージョン](/nuget/create-packages/prerelease-packages#semantic-versioning)に説明があるように、バージョン番号にはプレリリース接尾辞が含まれることがあります。 |

   *nuspec* ファイルの完全スキーマについては、[.nuspec リファレンス](/nuget/schema/nuspec)をご覧ください。

   このチュートリアルの *nuspec* ファイルの名前は *GarciaSoftware.ConsoleTemplate.CSharp.nuspec* であり、中身は次のようになります。

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <package xmlns="http://schemas.microsoft.com/packaging/2012/06/nuspec.xsd">
     <metadata>
       <id>GarciaSoftware.ConsoleTemplate.CSharp</id>
       <version>1.0.0</version>
       <description>
         Creates the Garcia Software console app.
       </description>
       <authors>Catalina Garcia</authors>
       <packageTypes>
         <packageType name="Template" />
       </packageTypes>
     </metadata>
   </package>
   ```

1. `nuget pack <PATH_TO_NUSPEC_FILE>` コマンドで[パッケージを作成](/nuget/create-packages/creating-a-package#creating-the-package)します。 次のコマンドでは、NuGet アセットが保持されているフォルダーが *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* にあると想定しています。 ただし、システムのどこにフォルダーを置いても、`nuget pack` コマンドは *nuspec* ファイルのパスを受け取ります。

   ```console
   nuget pack C:\Users\<USER>\Documents\NuGetTemplates\GarciaSoftware.ConsoleTemplate.CSharp\GarciaSoftware.ConsoleTemplate.CSharp.nuspec
   ```

### <a name="publishing-the-package-to-nugetorg"></a>パッケージを nuget.org に公開する

NuGet パッケージを公開するには、「[Create and publish a package](/nuget/quickstart/create-and-publish-a-package#publish-the-package)」 (パッケージを作成して公開する) トピックの手順に従ってください。 ただし、チュートリアル テンプレートを NuGet に公開することは推奨されません。公開後は一覧から外すことはできますが、削除することができないためです。 これで *nupkg* ファイルの形式で NuGet パッケージができました。下の指示に従い、ローカル *nupkg* ファイルから直接、テンプレートをインストールすることを推奨します。

### <a name="install-the-template-from-a-nuget-package"></a>NuGet パッケージからテンプレートをインストールする

#### <a name="install-the-template-from-the-local-nupkg-file"></a>ローカル *nupkg* ファイルからテンプレートをインストールする

作成した *nupkg* ファイルからテンプレートをインストールするには、`-i|--install` オプションを付けて `dotnet new` コマンドを実行します。*nupkg* ファイルのパスを指定します。

```console
dotnet new -i C:\Users\<USER>\GarciaSoftware.ConsoleTemplate.CSharp.1.0.0.nupkg
```

#### <a name="install-the-template-from-a-nuget-package-stored-at-nugetorg"></a>nuget.org に保存されている NuGet パッケージからテンプレートをインストールする

nuget.org に保存されている NuGet パッケージからテンプレートをインストールする場合、`-i|--install` オプションを付けて `dotnet new` コマンドを実行します。NuGet パッケージの名前を指定します。

```console
dotnet new -i GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> 次の例は、デモンストレーション目的のみで提供されます。 nuget.org には `GarciaSoftware.ConsoleTemplate.CSharp` NuGet パッケージがありません。NuGet からテスト テンプレートを公開し、利用する行為は推奨されません。 コマンドを実行しても、テンプレートはインストールされません。 ただし、nuget.org に公開されていないテンプレートをインストールできます。前のセクション「[ローカル nupkg ファイルからテンプレートをインストールする](#install-the-template-from-the-local-nupkg-file)」にあるように、ローカル ファイル システムで直接、*nupkg* ファイルを参照します。

nuget.org でパッケージからテンプレートをインストールする方法を実演例で確認する場合は、[dotnet-new の NUnit 3 テンプレート](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/)をご利用ください。 このテンプレートで、NUnit 単体テストを使用するプロジェクトが作成されます。 次のコマンドでインストールします。

```console
dotnet new -i NUnit3.DotNetNew.Template
```

`dotnet new -l` でテンプレートを一覧表示すると、テンプレートの一覧で *NUnit 3 Test Project* を確認できます。Short Name は *nunit* です。 次のセクションでこのテンプレートを利用できます。

![NUnit テンプレートとその他のテンプレートを表示しているコンソール ウィンドウ](./media/create-custom-template/nunit-template-console-window.png)

### <a name="create-a-project-from-the-template"></a>テンプレートからプロジェクトを作成する

テンプレートを NuGet からインストールしたら、そのテンプレートを使用します。(`-o|--output` オプションを利用して特定のディレクトリを指定するのでなければ) テンプレート エンジンの出力を置くディレクトリから `dotnet new <TEMPLATE>` コマンドを実行します。 詳細については、「[`dotnet new` オプション](~/docs/core/tools/dotnet-new.md#options)」を参照してください。 テンプレートの省略名 (短い名前) を `dotnet new` コマンドに直接指定します。 NUnit テンプレートからプロジェクトを作成するには、次のコマンドを実行します。

```console
dotnet new nunit
```

プロジェクトが作成され、プロジェクトのパッケージが復元されたことがコンソールに表示されます。 コマンドを実行すると、プロジェクトが使用できる状態になります。

![プロジェクトの依存関係の復元を含む dotnet の新しい nunit の出力を示すコンソール ウィンドウ](./media/create-custom-template/dotnet-new-nunit-console-output.png)

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>nuget.org に保存されている NuGet パッケージからテンプレートをアンインストールするには

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> 次の例は、デモンストレーション目的のみで提供されます。 nuget.org には `GarciaSoftware.ConsoleTemplate.CSharp` NuGet パッケージがありません。あるいは、.NET Core SDK と共にインストールされていません。 コマンドを実行すると、パッケージ/テンプレートはアンインストールされません。次の例外が表示されます。
>
> > Could not find something to uninstall called 'GarciaSoftware.ConsoleTemplate.CSharp'. ('GarciaSoftware.ConsoleTemplate.CSharp' という名前のアンインストール対象が見つかりませんでした。)

[dotnet-new の NUnit 3 テンプレート](https://www.nuget.org/packages/NUnit3.DotNetNew.Template/)をインストールしているとき、それをアンインストールする場合、次のコマンドを利用します。

```console
dotnet new -u NUnit3.DotNetNew.Template
```

### <a name="uninstall-the-template-from-a-local-nupkg-file"></a>ローカル nupkg ファイルからテンプレートをアンインストールする

テンプレートをアンインストールするとき、*nupkg* ファイルのパスを利用しないでください。 *`dotnet new -u <PATH_TO_NUPKG_FILE>` でテンプレートをアンインストールしようとすると失敗します。* パッケージはその `id` で参照してください。

```console
dotnet new -u GarciaSoftware.ConsoleTemplate.CSharp.1.0.0
```

## <a name="use-file-system-distribution"></a>ファイル システム配布を使用する

テンプレートを配布するには、ネットワーク上のユーザーがアクセスできる場所にプロジェクト テンプレート フォルダーを置きます。 `-i|--install` オプションを付けて `dotnet new` コマンドを実行します。テンプレート フォルダー (プロジェクトと *.template.config* フォルダーが含まれるプロジェクト フォルダー) のパスを指定します。

このチュートリアルでは、ユーザーのプロファイルの *Documents/Templates* フォルダーにプロジェクト テンプレートが保存されていると想定しています。 その場所から、次のコマンドでテンプレートをインストールします。\<USER> はユーザーのプロファイルの名前に変更します。

```console
dotnet new -i C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

### <a name="create-a-project-from-the-template"></a>テンプレートからプロジェクトを作成する

テンプレートをファイル システムからインストールしたら、そのテンプレートを使用します。(`-o|--output` オプションを利用して特定のディレクトリを指定するのでなければ) テンプレート エンジンの出力を置くディレクトリから `dotnet new <TEMPLATE>` コマンドを実行します。 詳細については、「[`dotnet new` オプション](~/docs/core/tools/dotnet-new.md#options)」を参照してください。 テンプレートの省略名 (短い名前) を `dotnet new` コマンドに直接指定します。

*C:\Users\\\<USER>\Documents\Projects\MyConsoleApp* に作成された新しいプロジェクト フォルダーで、`garciaconsole` テンプレートからプロジェクトを作成します。

```console
dotnet new garciaconsole
```

### <a name="uninstall-the-template"></a>テンプレートをアンインストールする

ローカル ファイル システムの *C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* にテンプレートを作成した場合、`-u|--uninstall` スイッチとテンプレート フォルダーのパスを指定してアンインストールします。

```console
dotnet new -u C:\Users\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp
```

> [!NOTE]
> テンプレートをお使いのローカル ファイル システムからアンインストールするには、完全修飾パスを使用する必要があります。 たとえば、*C:\Users\\\<USER>\Documents\Templates\GarciaSoftware.ConsoleTemplate.CSharp* は有効ですが、*./GarciaSoftware.ConsoleTemplate.CSharp* が含まれるフォルダーから、そのパスを指定することはできません。
> また、テンプレートのパスの最後にある終端ディレクトリのスラッシュは含めないでください。

## <a name="see-also"></a>関連項目

- [dotnet/templating GitHub リポジトリ Wiki](https://github.com/dotnet/templating/wiki)
- [dotnet/dotnet-template-samples GitHub リポジトリ](https://github.com/dotnet/dotnet-template-samples)
- [dotnet new の独自のテンプレートを作成する方法](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [JSON Schema Store の *template.json* スキーマ](http://json.schemastore.org/template)
