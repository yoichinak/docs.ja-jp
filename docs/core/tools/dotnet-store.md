---
title: dotnet store コマンド
description: "'dotnet store' コマンドは、指定したアセンブリをランタイム パッケージ ストアに格納します。"
author: bleroy
ms.date: 05/29/2018
ms.custom: seodec18
ms.openlocfilehash: 58889039d117a2231cda693e4aca7790f018d1b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54606752"
---
# <a name="dotnet-store"></a>dotnet store

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-2plus.md)]

## <a name="name"></a>name

`dotnet store` - 指定したアセンブリを[ランタイム パッケージ ストア](../deploying/runtime-store.md)に格納します。

## <a name="synopsis"></a>構文

`dotnet store -m|--manifest -f|--framework -r|--runtime  [--framework-version] [-h|--help] [--output] [--skip-optimization] [--skip-symbols] [-v|--verbosity] [--working-dir]`

## <a name="description"></a>説明

`dotnet store` - 指定したアセンブリを[ランタイム パッケージ ストア](../deploying/runtime-store.md)に格納します。 既定では、アセンブリは、ターゲット ランタイムとフレームワークに合わせて最適化されます。 詳細については、[「ランタイム パッケージ ストア」](../deploying/runtime-store.md) を参照してください。

## <a name="required-options"></a>必須オプション

`-f|--framework <FRAMEWORK>`

[ターゲット フレームワーク](../../standard/frameworks.md)を指定します。

`-m|--manifest <PATH_TO_MANIFEST_FILE>`

"*パッケージ ストア マニフェスト ファイル*" は、格納するパッケージの一覧を含む XML ファイルです。 マニフェスト ファイルの形式は、SDK スタイル プロジェクト形式と互換性があります。 そのため、必要なパッケージを参照するプロジェクト ファイルを `-m|--manifest` オプションと使用することで、ランタイム パッケージ ストアにアセンブリを格納することができます。 複数のマニフェスト ファイルを指定するには、ファイルごとにオプションとパスを繰り返します。 たとえば、`--manifest packages1.csproj --manifest packages2.csproj` のように指定します。

`-r|--runtime <RUNTIME_IDENTIFIER>`

ターゲットとする[ランタイム識別子](../rid-catalog.md)。

## <a name="optional-options"></a>省略可能なオプション

`--framework-version <FRAMEWORK_VERSION>`

.NET Core SDK のバージョンを指定します。 このオプションでは、`-f|--framework` オプションで指定したフレームワーク以降の特定のフレームワーク バージョンを選択することができます。

`-h|--help`

ヘルプ情報を表示します。

`-o|--output <OUTPUT_DIRECTORY>`

ランタイム パッケージ ストアへのパスを指定します。 指定しない場合、ユーザー プロファイル .NET Core インストール ディレクトリのサブディレクトリ *store* が既定値となります。

`--skip-optimization`

最適化フェーズをスキップします。

`--skip-symbols`

シンボルの生成をスキップします。 現時点では、Windows と Linux 上でのみシンボルを生成することができます。

`-v|--verbosity <LEVEL>`

コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。

`-w|--working-dir <INTERMEDIATE_WORKING_DIRECTORY>`

コマンドで使用される作業ディレクトリです。 指定しない場合、現在のディレクトリの *obj* サブディレクトリが使用されます。

## <a name="examples"></a>使用例

.NET Core 2.0.0 の *packages.csproj* プロジェクト ファイルで指定されたパッケージを格納します。

`dotnet store --manifest packages.csproj --framework-version 2.0.0`

*packages.csproj* で指定されたパッケージを最適化なしで格納します。

`dotnet store --manifest packages.csproj --skip-optimization`

## <a name="see-also"></a>関連項目

- [ランタイム パッケージ ストア](../deploying/runtime-store.md)
