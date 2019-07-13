---
title: パッケージの管理を使用してF#for Azure
description: パケットを作成または Nuget を使用して管理するF#Azure の依存関係
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: b180024e2276a2fd7786f35cb922b1aa1d91f0ad
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880015"
---
# <a name="package-management-for-f-azure-dependencies"></a>F# の Azure の依存関係のためのパッケージ管理

パッケージ マネージャーを使用すると、Azure 向け開発用のパッケージを取得することは簡単です。 2 つのオプションは[パケット](https://fsprojects.github.io/Paket/)と[NuGet](https://www.nuget.org/)します。

## <a name="using-paket"></a>パケットを使用します。

使用している場合[パケット](https://fsprojects.github.io/Paket/)の依存関係マネージャーとして使用することができます、 `paket.exe` Azure の依存関係を追加するツール。 例:

```
> paket add nuget WindowsAzure.Storage
```

または、使用している[Mono](https://www.mono-project.com/)クロスプラット フォーム対応 .NET 開発。

```
> mono paket.exe add nuget WindowsAzure.Storage
```

これが追加されます`WindowsAzure.Storage`、現在のディレクトリでプロジェクトのパッケージの依存関係のセット、変更、`paket.dependencies`ファイルを開き、パッケージをダウンロードします。 依存関係を設定したが、依存関係が設定されていない他の開発者がプロジェクトを使用するか、解決およびローカルのような依存関係をインストールできます。

```
> paket install
```

または、Mono の開発。

```
> mono paket.exe install
```

すべてのパッケージ依存関係は、このような最新バージョンに更新できます。

```
> paket update
```

または、Mono の開発。

```
> mono paket.exe update
```

## <a name="using-nuget"></a>Nuget を使用してください。

使用している場合[NuGet](https://www.nuget.org/)の依存関係マネージャーとして使用することができます、 `nuget.exe` Azure の依存関係を追加するツール。 例:

```
> nuget install WindowsAzure.Storage -ExcludeVersion
```

または、Mono の開発。

```
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

これは追加`WindowsAzure.Storage`を現在のディレクトリ、およびダウンロード パッケージにプロジェクトのパッケージの依存関係のセットにします。 依存関係を設定したが、依存関係が設定されていない他の開発者がプロジェクトを使用するか、解決およびローカルのような依存関係をインストールできます。

```
> nuget restore
```

または、Mono の開発。

```
> mono nuget.exe restore
```

すべてのパッケージ依存関係は、このような最新バージョンに更新できます。

```
> nuget update
```

または、Mono の開発。

```
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a>参照元のアセンブリ

パッケージを使用するには、 F# 、スクリプトを使用してパッケージに含まれるアセンブリを参照する必要があります、`#r`ディレクティブ。 例:

```
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

ご覧のように、DLL と完全の DLL の名前は必ずしも厳密パッケージ名と同じ相対パスを指定する必要があります。 パスには、framework のバージョンやパッケージのバージョン番号が含まれます。 インストールされているすべてのアセンブリを見つけるには、Windows コマンド ラインでこのようなものを使用できます。

```
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

または、Unix シェルのような処理。

```
> find packages/WindowsAzure.Storage -name "*.dll"
```

こうパスにインストールされているアセンブリ。 そこから、フレームワークのバージョンの正しいパスを選択できます。
