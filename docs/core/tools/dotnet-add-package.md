---
title: dotnet add package コマンド
description: "'dotnet add package' コマンドは、NuGet パッケージ参照をプロジェクトに追加する便利なオプションを提供します。"
ms.date: 06/26/2019
ms.openlocfilehash: 124e42b1d5897802bb1698c8e22b7e76031391a2
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105162"
---
# <a name="dotnet-add-package"></a>dotnet add package

**この記事の対象: ✓** .NET Core 1.x SDK 以降のバージョン

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>name

`dotnet add package` - プロジェクト ファイルにパッケージ参照を追加します。

## <a name="synopsis"></a>構文

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a>説明

`dotnet add package` コマンドは、プロジェクト ファイルにパッケージ参照を追加する便利なオプションを提供します。 このコマンドの実行後に、パッケージがプロジェクト内のフレームワークと互換性があることを確認する互換性チェックがあります。 互換性チェックに合格すると、`<PackageReference>` 要素がプロジェクト ファイルに追加されて、[dotnet restore](dotnet-restore.md) が実行されます。

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

たとえば、`Newtonsoft.Json` を *ToDo.csproj* に追加すると、次のような出力が生成されます。

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

この *ToDo.csproj* ファイルには、参照されるパッケージの [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) 要素が含まれます。

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a>引数

- **`PROJECT`**

  プロジェクト ファイルを指定します。 指定されていない場合、現在のディレクトリで検索されます。

- **`PACKAGE_NAME`**

  追加するパッケージ参照。

## <a name="options"></a>オプション

- **`-f|--framework <FRAMEWORK>`**

  特定の[フレームワーク](../../standard/frameworks.md)を対象にしている場合にのみ、パッケージ参照を追加します。

- **`-h|--help`**

  コマンドの短いヘルプを印刷します。

- **`--interactive`**

  コマンドを停止して、ユーザーの入力または操作のために待機させることができます (たとえば、認証を完了する場合)。 .NET Core 2.1 SDK バージョン 2.1.400 以降で使用可能です。

- **`-n|--no-restore`**

  復元のプレビューと互換性チェックを実行せずにパッケージ参照を追加します。

- **`--package-directory <PACKAGE_DIRECTORY>`**

  パッケージの復元先となるディレクトリ。 既定のパッケージ復元場所は、Windows の場合は `%userprofile%\.nuget\packages`、macOS と Linux の場合は `~/.nuget/packages` です。 詳細については、[NuGet でのグローバル パッケージ、キャッシュ、および一時フォルダーの管理](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)に関する記事を参照してください。

- **`-s|--source <SOURCE>`**

  復元操作時に使用する NuGet パッケージのソース。

- **`-v|--version <VERSION>`**

  パッケージのバージョン。 [NuGet パッケージのバージョン管理](https://docs.microsoft.com/nuget/reference/package-versioning)に関するページを参照してください。

## <a name="examples"></a>使用例

- `Newtonsoft.Json` NuGet パッケージをプロジェクトに追加する:

  ```console
  dotnet add package Newtonsoft.Json
  ```

- 特定バージョンのパッケージをプロジェクトに追加する:

  ```console
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- 特定の NuGet ソースを使用してパッケージを追加する:

  ```console
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a>関連項目

- [NuGet でグローバル パッケージ、キャッシュ、および一時フォルダーを管理する](https://docs.microsoft.com/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [NuGet パッケージのバージョン管理](https://docs.microsoft.com/nuget/reference/package-versioning)
