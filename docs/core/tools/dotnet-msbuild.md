---
title: dotnet msbuild コマンド
description: dotnet msbuild コマンドは、MSBuild コマンド ラインへのアクセスを提供します。
ms.date: 02/14/2020
ms.openlocfilehash: 88e85868e2d7de564b2e4c90ce6e78bde4cb350e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463620"
---
# <a name="dotnet-msbuild"></a>dotnet msbuild

**この記事の対象:** ✔️ .NET Core 2.x SDK 以降のバージョン

## <a name="name"></a>name

`dotnet msbuild` - プロジェクトとそのすべての依存関係をビルドします。

## <a name="synopsis"></a>構文

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a>[説明]

`dotnet msbuild` コマンドでは、完全に機能する MSBuild へのアクセスを許可します。

このコマンドには、SDK スタイルのプロジェクトに対してのみ、既存の MSBuild コマンド ライン クライアントとまったく同じ機能があります。 オプションはすべて同じです。 使用可能なオプションの詳細については、「[MSBuild コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)」を参照してください。

[dotnet build](dotnet-build.md) コマンドは、`dotnet msbuild -restore -target:Build` に相当します。 [dotnet ビルド](dotnet-build.md)は、プロジェクトのビルドによく使用されますが、ビルド ターゲットを常に実行するため、プロジェクトをビルドしなくてもよい場合は `dotnet msbuild` を使用できます。 たとえば、プロジェクトをビルドせずに実行したい特定のターゲットがある場合は、`dotnet msbuild` を使用してターゲットを指定します。

## <a name="examples"></a>例

- プロジェクトとその依存関係をビルドします。

  ```dotnetcli
  dotnet msbuild
  ```

- リリース構成を使用して、プロジェクトとその依存関係をビルドします。

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- 発行先を実行して、RID `osx.10.11-x64` に発行します。

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- プロジェクト全体と SDK に付属するすべてのターゲットをご覧ください。

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
