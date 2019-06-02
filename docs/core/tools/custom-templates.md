---
title: dotnet new のカスタム テンプレート
description: あらゆる種類の .NET プロジェクトまたはファイルのカスタム テンプレートについて説明します。
author: mairaw
ms.date: 08/11/2017
ms.openlocfilehash: 6ce53cab308ed404974e4d736e735bc82ac04fe6
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/29/2019
ms.locfileid: "66299923"
---
# <a name="custom-templates-for-dotnet-new"></a>dotnet new のカスタム テンプレート

[.NET Core SDK](https://www.microsoft.com/net/download/core) には、[`dotnet new` コマンド](dotnet-new.md)で使用するさまざまなテンプレートが既にインストールされています。 .NET Core 2.0 以降から、アプリ、サービス、ツール、クラス ライブラリなど、あらゆる種類のプロジェクトを対象に独自のテンプレートを作成できるようになりました。 構成ファイルなど、1 つまたは複数の独立ファイルを出力するテンプレートを作成することもできます。

カスタム テンプレートは、あらゆる NuGet フィードで NuGet パッケージからインストールできます。NuGet *nupkg* ファイルを直接参照するか、テンプレートが含まれるファイル システム ディレクトリを指定します。 テンプレート エンジンの機能を利用すると、値を置換したり、ファイルやファイルの領域を追加したり、除外したり、テンプレートの利用時に独自の処理操作を実行したりできます。

テンプレート エンジンはオープン ソースです。オンライン コード リポジトリは GitHub の [dotnet/templating](https://github.com/dotnet/templating/) にあります。 テンプレートのサンプルが必要であれば、[dotnet/dotnet-template-samples](https://github.com/dotnet/dotnet-template-samples) リポジトリをご覧ください。 GitHub の「[Available templates for dotnet new](https://github.com/dotnet/templating/wiki/Available-templates-for-dotnet-new)」 (dotnet new で利用できるテンプレート) には、サードパーティのテンプレートなど、テンプレートが他にもあります。 カスタム テンプレートの作成と利用の詳細については、「[dotnet new の独自のテンプレートを作成する方法](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)」と「[dotnet/templating GitHub リポジトリ Wiki](https://github.com/dotnet/templating/wiki)」を参照してください。

チュートリアルでテンプレートを作成するには、「[dotnet new のカスタム テンプレートを作成する](~/docs/core/tutorials/create-custom-template.md)」チュートリアルをご利用ください。

## <a name="configuration"></a>構成

テンプレートは次の要素から構成されます。

- ソース ファイルとフォルダー
- 構成ファイル (*template.json*)

### <a name="source-files-and-folders"></a>ソース ファイルとフォルダー

ソース ファイルとフォルダーには、`dotnet new <TEMPLATE>` コマンドの実行時にテンプレート エンジンで使用されるあらゆるファイルとフォルダーが含まれます。 テンプレート エンジンは、ソース コードとして*実行可能なプロジェクト*を利用し、プロジェクトを生成するように設計されています。 これにはいくつかの利点があります。

- テンプレート エンジンでは、プロジェクトのソース コードに特別なトークンを挿入することを必要としません。
- コード ファイルは特別なファイルではなく、テンプレート エンジンで利用するために変更されることはありません。 そのため、プロジェクトの利用時に通常利用しているツールでテンプレート コンテンツに対応できます。
- 他のプロジェクトの場合と同じように、テンプレート プロジェクトをビルドし、実行し、デバッグします。
- *template.json* 構成ファイルをプロジェクトに追加するだけで、既存のプロジェクトからテンプレートを簡単に作成できます。

テンプレートに保存されるファイルやフォルダーは、.NET Core や .NET Framework ソリューションなど、正式な種類の .NET プロジェクトに限定されません。 ソース ファイルとフォルダーは、テンプレートの利用時に作成するあらゆるコンテンツで構成できます。構成ファイルやソリューション ファイルなど、テンプレート エンジンでファイルが 1 つだけ生成される場合も同様です。 たとえば、*web.config* ソース ファイルを含み、テンプレートの利用時、プロジェクトに対して、変更された *web.config* ファイルを作成するテンプレートを作成できます。 ソース ファイルの変更は、*template.json* 構成ファイルのロジックと設定、およびユーザーが `dotnet new <TEMPLATE>` コマンドにオプションとして渡した値に基づきます。

### <a name="templatejson"></a>template.json

*template.json* ファイルは、テンプレートのルート ディレクトリの *.template.config* フォルダーにあります。 このファイルは、テンプレート エンジンに構成情報を提供します。 最小構成には、次の表に示すメンバーが必要です。この最小構成があれば、実際に機能するテンプレートが作成されます。

| メンバー            | 型          | 説明 |
| ----------------- | ------------- | ----------- |
| `$schema`         | URI           | *template.json* ファイルの JSON スキーマ。 エディターが JSON スキーマ対応であれば、スキーマの指定時、JSON 編集機能が有効になります。 たとえば、[Visual Studio Code](https://code.visualstudio.com/) の場合、IntelliSense を有効にするためにこのメンバーが必要になります。 値として `http://json.schemastore.org/template` を使用します。 |
| `author`          | string        | テンプレートの作成者。 |
| `classifications` | array(string) | テンプレートのゼロ以上の特性。ユーザーがこれを利用し、テンプレートを探すことがあります。 <code>dotnet new -l&#124;--list</code> コマンドでテンプレートの一覧を生成したとき、*Tags* 列が表示される場合、この列にも分類が表示されます。 |
| `identity`        | string        | このテンプレートの一意の名前。 |
| `name`            | string        | ユーザーに対して表示されるテンプレートの名前。 |
| `shortName`       | string        | テンプレートを選択するための既定の省略名 (短い名前)。テンプレート名が GUI 経由で選択されるのではなく、ユーザーによって指定される環境に適用されます。 たとえば、CLI コマンドでコマンド プロンプトからテンプレートを利用するときに省略名が便利です。 |

#### <a name="example"></a>例:

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

*template.json* ファイルの完全スキーマは [JSON Schema Store](http://json.schemastore.org/template) にあります。

## <a name="net-default-templates"></a>.NET の既定のテンプレート

[.NET Core SDK](https://www.microsoft.com/net/download/core) をインストールすると、コンソール アプリ、クラス ライブラリ、単体テスト プロジェクト、ASP.NET Core アプリ ([Angular](https://angular.io/) プロジェクトと [React](https://facebook.github.io/react/) プロジェクトを含む)、構成ファイルなど、プロジェクトやファイルを作成するための 12 個を超える組み込みテンプレートが与えられます。 `-l|--list` オプションを付けて `dotnet new` コマンドを実行すると、組み込みテンプレートの一覧が表示されます。

```console
dotnet new -l
```

## <a name="packing-a-template-into-a-nuget-package-nupkg-file"></a>テンプレートをパッケージ化し、NuGet パッケージ (nupkg ファイル) を作成する

現在のところ、カスタム テンプレートを Windows でパッケージ化するとき、[dotnet pack](dotnet-pack.md) ではなく、[nuget.exe](https://dist.nuget.org/win-x86-commandline/latest/nuget.exe) が利用されます。 プラットフォームに依存しないパッケージ化の場合、[NuGetizer 3000](https://github.com/NuGet/Home/wiki/NuGetizer-3000) の利用を検討してください。

プロジェクト フォルダーの中身はその *.template.config/template.json* ファイルと共に *content* という名前のフォルダーに置かれます。 *content* フォルダーの隣に [*nuspec*](/nuget/create-packages/creating-a-package) ファイルを追加します。このファイルは XML マニフェスト ファイルであり、パッケージの中身が記述され、NuGet パッケージの作成プロセスを実行します。 *nuspec* ファイルの **\<packageTypes>** 要素の中に、 **\<packageType>** 要素を追加し、`name` 属性の値を `Template` にします。 *content* フォルダーと *nuspec* ファイルの両方を同じディレクトリに入れます。 下の表は、NuGet パッケージとしてテンプレートを生成するために必要な *nuspec* ファイルの最小要素をまとめたものです。

| 要素            | 型   | 説明 |
| ------------------ | ------ | ----------- |
| **\<authors>**     | string | パッケージ作成者の一覧。コンマで区切られています。nuget.org のプロファイル名と一致します。作成者は nuget.org の NuGet ギャラリーに表示され、同じ作成者によるパッケージの相互参照に使用されます。 |
| **\<description>** | string | UI 画面用のパッケージの長い説明。 |
| **\<id>**          | string | パッケージの識別子で、大文字と小文字が区別されます。nuget.org 全体で、あるいはパッケージが置かれるギャラリーで一意でなければなりません。 ID には、URL によっては無効なスペースや文字が含まれることがあります。また、一般的に、.NET の名前空間ルールに従います。 手引きについては、「[Choosing a unique package identifier and setting the version number](/nuget/create-packages/creating-a-package#choosing-a-unique-package-identifier-and-setting-the-version-number)」 (一意のパッケージ識別子を選択し、バージョン番号を設定する) をご覧ください。 |
| **\<packageType>** | string | この要素を **\<metadata>** 要素の中の **\<packageTypes>** 要素内に置きます。 **\<packageType>** 要素の `name` 属性を `Template` に設定します。 |
| **\<version>**     | string | パッケージのバージョン。major.minor.patch パターンになります。 「[プレリリース バージョン](/nuget/create-packages/prerelease-packages#semantic-versioning)」トピックに説明があるように、バージョン番号にはプレリリース接尾辞が含まれることがあります。 |

*nuspec* ファイルの完全スキーマについては、[.nuspec リファレンス](/nuget/schema/nuspec)をご覧ください。 テンプレートのサンプル *nuspec* ファイルは、「[dotnet new のカスタム テンプレートを作成する](~/docs/core/tutorials/create-custom-template.md)」チュートリアルにあります。

`nuget pack <PATH_TO_NUSPEC_FILE>` コマンドで[パッケージを作成](/nuget/create-packages/creating-a-package#creating-the-package)します。

## <a name="installing-a-template"></a>テンプレートをインストールする

カスタム テンプレートは、あらゆる NuGet フィードで NuGet パッケージからインストールできます。*nupkg* ファイルを直接参照するか、テンプレートを作成する構成が含まれるファイル システム ディレクトリを指定します。 [dotnet new](dotnet-new.md) コマンドで `-i|--install` オプションを使用します。

### <a name="to-install-a-template-from-a-nuget-package-stored-at-nugetorg"></a>nuget.org に保存されている NuGet パッケージからテンプレートをインストールするには

```console
dotnet new -i <NUGET_PACKAGE_ID>
```

### <a name="to-install-a-template-from-a-local-nupkg-file"></a>ローカル nupkg ファイルからテンプレートをインストールするには

```console
dotnet new -i <PATH_TO_NUPKG_FILE>
```

### <a name="to-install-a-template-from-a-file-system-directory"></a>ファイル システム ディレクトリからテンプレートをインストールするには

`FILE_SYSTEM_DIRECTORY` は、プロジェクトと *.template.config* フォルダーが含まれるプロジェクト フォルダーです。

```console
dotnet new -i <FILE_SYSTEM_DIRECTORY>
```

## <a name="uninstalling-a-template"></a>テンプレートをアンインストールする

カスタム テンプレートをアンインストールするには、その `id` で NuGet パッケージを参照するか、テンプレートを作成する構成が含まれるファイル システム ディレクトリを指定します。 [dotnet new](dotnet-new.md) コマンドで `-u|--uninstall` インストール オプションを使用します。

### <a name="to-uninstall-a-template-from-a-nuget-package-stored-at-nugetorg"></a>nuget.org に保存されている NuGet パッケージからテンプレートをアンインストールするには

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-local-nupkg-file"></a>ローカル nupkg ファイルからテンプレートをアンインストールするには

テンプレートをアンインストールするとき、*nupkg* ファイルのパスを利用しないでください。 `dotnet new -u <PATH_TO_NUPKG_FILE>` を使用してテンプレートをアンインストールしようとすると失敗します。 パッケージはその `id` で参照してください。

```console
dotnet new -u <NUGET_PACKAGE_ID>
```

### <a name="to-uninstall-a-template-from-a-file-system-directory"></a>ファイル システム ディレクトリからテンプレートをアンインストールするには

`FILE_SYSTEM_DIRECTORY` は、プロジェクトと *.template.config* フォルダーが含まれるプロジェクト フォルダーです。 絶対パスを指定する必要があります。 相対パスを使用してテンプレートをアンインストールしようとすると失敗します。 詳細については、「[dotnet new](dotnet-new.md)」を参照してください。

```console
dotnet new -u <FILE_SYSTEM_DIRECTORY>
```

## <a name="create-a-project-using-a-custom-template"></a>カスタム テンプレートを利用してプロジェクトを作成する

テンプレートがインストールされたら、事前インストールされている他のテンプレートの場合と同様に、`dotnet new <TEMPLATE>` コマンドを実行してテンプレートを使用します。 [オプション](dotnet-new.md#options)を `dotnet new` コマンドに指定することもできます。テンプレート設定で構成した、テンプレート固有のオプションなどがあります。 テンプレートの省略名 (短い名前) をコマンドに直接指定します。

```console
dotnet new <TEMPLATE>
```

## <a name="see-also"></a>関連項目

- [dotnet new のカスタム テンプレートを作成する (チュートリアル)](../tutorials/create-custom-template.md)
- [dotnet/templating GitHub リポジトリ Wiki](https://github.com/dotnet/templating/wiki)
- [dotnet/dotnet-template-samples GitHub リポジトリ](https://github.com/dotnet/dotnet-template-samples)
- [dotnet new の独自のテンプレートを作成する方法](https://devblogs.microsoft.com/dotnet/how-to-create-your-own-templates-for-dotnet-new/)
- [JSON Schema Store の *template.json* スキーマ](http://json.schemastore.org/template)
