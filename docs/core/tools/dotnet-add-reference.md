---
title: dotnet add reference コマンド
description: dotnet add 参照コマンドは、プロジェクト間参照を追加する便利なオプションを提供します。
ms.date: 06/26/2019
ms.openlocfilehash: dc8bc01a2bff4f2cf3a8af9efb233448d7de337f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733276"
---
# <a name="dotnet-add-reference"></a>dotnet add reference

**この記事の対象:** ✔️ .NET Core 1.x SDK 以降のバージョン

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a>名前

`dotnet add reference` - プロジェクト間 (P2P) 参照を追加します。

## <a name="synopsis"></a>構文

`dotnet add [<PROJECT>] reference [-f|--framework] <PROJECT_REFERENCES> [-h|--help] [--interactive]`

## <a name="description"></a>説明

`dotnet add reference` コマンドは、プロジェクトにプロジェクト参照を追加する便利なオプションを提供します。 このコマンドを実行すると、`<ProjectReference>` 要素がプロジェクト ファイルに追加されます。

```xml
<ItemGroup>
  <ProjectReference Include="app.csproj" />
  <ProjectReference Include="..\lib2\lib2.csproj" />
  <ProjectReference Include="..\lib1\lib1.csproj" />
</ItemGroup>
```

## <a name="arguments"></a>引数

- **`PROJECT`**

  プロジェクト ファイルを指定します。 指定されていない場合、現在のディレクトリで検索されます。

- **`PROJECT_REFERENCES`**

  追加するプロジェクト間参照 (P2P) です。 1 つ以上のプロジェクトを指定します。 [glob パターン](https://en.wikipedia.org/wiki/Glob_(programming))は Unix/Linux ベースのシステムで利用できます。

## <a name="options"></a>オプション

- **`-h|--help`**

  コマンドの短いヘルプを印刷します。

- **`-f|--framework <FRAMEWORK>`**

  特定の[フレームワーク](../../standard/frameworks.md)を対象にしている場合にのみ、プロジェクト参照を追加します。

- **`--interactive`**

  コマンドを停止して、ユーザーの入力または操作のために待機させることができます (たとえば、認証を完了する場合)。 .NET Core 3.0 SDK 以降で使用できます。

## <a name="examples"></a>使用例

- プロジェクト参照を追加する:

  ```dotnetcli
  dotnet add app/app.csproj reference lib/lib.csproj
  ```

- 現在のディレクトリのプロジェクトに複数のプロジェクト参照を追加する:

  ```dotnetcli
  dotnet add reference lib1/lib1.csproj lib2/lib2.csproj
  ```

- Linux/Unix で glob パターンを使って複数のプロジェクト参照を追加する:

  ```dotnetcli
  dotnet add app/app.csproj reference **/*.csproj
  ```
