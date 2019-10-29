---
title: dotnet-trace - .NET Core
description: dotnet-trace コマンドライン ツールのインストールおよび使用。
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: 6513cf63070bc1984006da75313e9912d76a6c95
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321532"
---
# <a name="trace-for-performance-analysis-utility-dotnet-trace"></a>パフォーマンス分析ユーティリティ (`dotnet-trace`) 用のトレース

**この記事の対象:** .NET Core 3.0 SDK 以降のバージョン

## <a name="installing-dotnet-trace"></a>`dotnet-trace` のインストール

`dotnet-trace` [NuGet パッケージ](https://www.nuget.org/packages/dotnet-trace)の最新のリリース バージョンをインストールするには、次のように [dotnet tool install](../tools/dotnet-tool-install.md) コマンドを使用します。

```dotnetcli
dotnet tool install --global dotnet-trace
```

## <a name="synopsis"></a>構文

```console
dotnet-trace [-h, --help] [--version] <command>
```

## <a name="description"></a>説明

`dotnet-trace` ツールは、ネイティブ プロファイラーを使用せずに、実行中のプロセスの .NET Core のトレースを収集するクロスプラットフォームの CLI グローバル ツールです。 これは、.NET Core ランタイムのクロスプラットフォームの `EventPipe` テクノロジを中心に構築されています。 `dotnet-trace` は、Windows、Linux または macOS でも同じエクスペリエンスを提供します。

## <a name="options"></a>オプション

- **`--version`**

dotnet-counters ユーティリティのバージョンを表示します。

- **`-h|--help`**

コマンド ラインのヘルプを表示します。

## <a name="commands"></a>コマンド

| コマンド                                                     |
| ----------------------------------------------------------- |
| [dotnet-trace collect](#dotnet-trace-collect)               |
| [dotnet-trace convert](#dotnet-trace-convert)               |
| [dotnet-trace list-processes](#dotnet-trace-list-processes) |
| [dotnet-trace list-profiles](#dotnet-trace-list-profiles)   |

## <a name="dotnet-trace-collect"></a>dotnet-trace collect

実行中のプロセスから診断トレースを収集します。

### <a name="synopsis"></a>構文

```console
dotnet-trace collect [-h|--help] [-p|--process-id] [--buffersize <size>] [-o|--output]
    [--providers] [--profile <profile-name>] [--format]
```

### <a name="options"></a>オプション

- **`-p|--process-id <PID>`**

  トレースを収集するプロセス。

- **`--buffersize <size>`**

  メモリ内の循環バッファーのサイズをメガバイトに設定します。 既定は 256 MB です。

- **`-o|--output <trace-file-path>`**

  収集されたトレース データの出力パス。 指定しない場合の既定は、`trace.nettrace` です。

- **`--providers <list-of-comma-separated-providers>`**

  有効にする `EventPipe` プロバイダーのコンマ区切りのリスト。 これらのプロバイダーは、`--profile <profile-name>` で示されている任意のプロバイダーを補完します。 特定のプロバイダーに不整合がある場合、この構成がプロファイルの暗黙的な構成に優先されます。

  プロバイダーの一覧の形式は、次のとおりです。

  - `Provider[,Provider]`
  - `Provider` は、`KnownProviderName[:Flags[:Level][:KeyValueArgs]]` という形式です。
  - `KeyValueArgs` は、`[key1=value1][;key2=value2]` という形式です。

- **`--profile <profile-name>`**

  共通のトレース シナリオを簡潔に指定できるようにする、事前定義されたプロバイダーの名前付き構成のセット。

- **`--format <NetTrace|Speedscope>`**

  トレース ファイルの出力の変換形式を設定します。

## <a name="dotnet-trace-convert"></a>dotnet-trace convert

`nettrace` トレースを、別のトレース分析ツールで使用するために、別の形式に変換します。

### <a name="synopsis"></a>構文

```console
dotnet-trace convert [<input-filename>] [-h|--help] [--format] [-o|--output]
```

### <a name="arguments"></a>引数

- **`<input-filename>`**

  変換する入力トレース ファイル。 既定は *trace.nettrace* です。

### <a name="options"></a>オプション

- **`--format <NetTrace|Speedscope>`**

  トレース ファイルの出力の変換形式を設定します。

- **`-o|--output <output-filename>`**

  出力ファイルの名前。 ターゲットの形式の拡張子が追加されます。

## <a name="dotnet-trace-list-processes"></a>dotnet-trace list-processes

トレースできる dotnet プロセスの一覧を示します。

### <a name="synopsis"></a>構文

```console
dotnet-trace list-processes [-h|--help]
```

## <a name="dotnet-trace-list-profiles"></a>dotnet-trace list-profiles

各プロファイルに含まれるプロバイダーとフィルターの記述と共に、事前に構築されているトレースのプロファイルを一覧表示します。

### <a name="synopsis"></a>構文

```console
dotnet-trace list-profiles [-h|--help]
```

## <a name="collect-a-trace-with-dotnet-trace"></a>`dotnet-trace` を使用してトレースを収集する

- `dotnet-trace` を使用してトレースを収集するには、まずトレースを収集する .NET Core アプリケーションのプロセス識別子 (PID) を調べます。

  - Windows では、タスク マネージャーや `tasklist` コマンドなどを使用するオプションがあります。
  - Linux での簡易オプションは、`ps` コマンドの使用です。

また、その PID と共に [dotnet-trace list-processes](#dotnet-trace-list-processes) コマンドを使用して、実行中の .NET Core プロセスを調べることもできます。

- 次に、次のコマンドを実行します。

```console
> dotnet-trace collect --process-id <PID>

Press <Enter> to exit...
Connecting to process: <Full-Path-To-Process-Being-Profiled>/dotnet.exe
Collecting to file: <Full-Path-To-Trace>/trace.nettrace
  Session Id: <SessionId>
  Recording trace 721.025 (KB)
```

- 最後に、`<Enter>` キーを押して収集を停止すると、`dotnet-trace` は `trace.nettrace` ファイルへのイベントのログ記録を終了します。

## <a name="viewing-the-trace-captured-from-dotnet-trace"></a>`dotnet-trace` でキャプチャしたトレースを表示する

Windows で `.nettrace` ファイルは、ETW または LTTng を使用して収集したトレースと同様、[PerfView ](https://github.com/microsoft/perfview) で参照して分析できます。 Linux で収集したトレースを PerfView で参照するには、トレースを Windows マシンに移動します。

また、`dotnet-trace` の出力形式を `speedscope` に変更して、Linux マシンでトレースを表示することもできます。 出力ファイルの形式は、`-f|--format` オプションを使用して変更できます。`-f speedscope` が、`dotnet-trace` に `speedscope` ファイルを生成させます。 現在、`nettrace` (既定のオプション) と `speedscope` の間で選択できます。 `Speedscope` ファイルは <https://www.speedscope.app> で開くことができます。

> [!NOTE]
> .NET Core ランタイムは、トレースを `nettrace` 形式で生成し、トレースの完了後 (指定されている場合は)、それを speedscope に変換します。 変換によってはデータが失われる場合もあるため、元の `nettrace` ファイルが変換されたファイルの横に保持されます。

## <a name="using-dotnet-trace-to-collect-counter-values-over-time"></a>`dotnet-trace` を使用して経時的なカウンター値を収集する

パフォーマンスが影響する運用環境などの正常性の基本監視に `EventCounter` を使用する場合に、リアルタイムで監視するのではなく、トレースを収集したい場合は、`dotnet-trace` で行うこともできます。

たとえば、実行時のパフォーマンス カウンター値を収集したい場合は、次のコマンドを使用します。

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1
```

このコマンドは、正常性の簡易監視のために 1 秒ごとにランタイム カウンターをレポートします。 `EventCounterIntervalSec=1` の値を (60 など) 大きい値に置き換えた場合、カウンター データの細分性の詳細度がより低いトレースをより少数収集できるようになります。

ランタイム イベントを無効にしてオーバーヘッド (およびトレースのサイズ) をさらに減らしたい場合は、次のコマンドを使用して、ランタイム イベントとマネージド スタック プロファイラーを無効にできます。

```console
dotnet-trace collect --process-id <PID> --providers System.Runtime:0:1:EventCounterIntervalSec=1,Microsoft-Windows-DotNETRuntime:0:1,Microsoft-DotNETCore-SampleProfiler:0:1
```

## <a name="net-providers"></a>.NET プロバイダー

.NET Core ランタイムでは、次の .NET プロバイダーがサポートされています。 .NET Core では、`Event Tracing for Windows (ETW)` と `EventPipe` トレースの有効化に、いずれも同じキーワードを使用しています。

| プロバイダー名                            | 情報 |
|------------------------------------------|-------------|
| `Microsoft-Windows-DotNETRuntime`        | [ランタイム プロバイダー](../../framework/performance/clr-etw-providers.md#the-runtime-provider)<br>[CLR ランタイム キーワード](../../framework/performance/clr-etw-keywords-and-levels.md#runtime) |
| `Microsoft-Windows-DotNETRuntimeRundown` | [ランダウン プロバイダー](../../framework/performance/clr-etw-providers.md#the-rundown-provider)<br>[CLR ランダウン キーワード](../../framework/performance/clr-etw-keywords-and-levels.md#rundown) |
| `Microsoft-DotNETCore-SampleProfiler`    | サンプル プロファイラーを有効にします。 |
