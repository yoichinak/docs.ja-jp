---
title: dotnet-counters - .NET Core
description: dotnet-counter コマンドライン ツールをインストールして使用する方法について説明します。
author: sdmaclea
ms.author: stmaclea
ms.date: 10/14/2019
ms.openlocfilehash: b2fab239713d9d19c580580496e73a91ceafcc52
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321538"
---
# <a name="dotnet-counters"></a>dotnet-カウンター

**この記事の対象: ✓** .NET Core 3.0 SDK 以降のバージョン

## <a name="install-dotnet-counters"></a>dotnet-counters のインストール

`dotnet-counters` [NuGet パッケージ](https://www.nuget.org/packages/dotnet-counters)の最新リリース バージョンをインストールするには、[dotnet tool install](../tools/dotnet-tool-install.md) コマンドを使用します。

```dotnetcli
dotnet tool install --global dotnet-counters
```

## <a name="synopsis"></a>構文

```console
dotnet-counters [-h|--help] [--version] <command>
```

## <a name="description"></a>説明

`dotnet-counters` は、アドホックな正常性監視と第 1 レベルのパフォーマンス調査のためのパフォーマンス監視ツールです。 <xref:System.Diagnostics.Tracing.EventCounter> API を使用して公開されたパフォーマンス カウンターの値を監視できます。 たとえば、CPU 使用率や .NET Core アプリケーションでスローされる例外の発生率などを迅速に監視して、`PerfView` または `dotnet-trace` を使用した、より重大なパフォーマンス調査を開始する前に疑わしいものがあるかどうかを確認できます。

## <a name="options"></a>オプション

- **`--version`**

  dotnet-counters ユーティリティのバージョンを表示します。

- **`-h|--help`**

  コマンド ライン ヘルプを表示します。

## <a name="commands"></a>コマンド

| コマンド                                             |
| --------------------------------------------------- |
| [dotnet-counters list](#dotnet-counters-list)       |
| [dotnet-counters monitor](#dotnet-counters-monitor) |

## <a name="dotnet-counters-list"></a>dotnet-counters list

カウンターの名前と説明の一覧をプロバイダー別にグループ化して表示します。

### <a name="synopsis"></a>構文

```console
dotnet-counters list [-h|--help]
```

### <a name="example"></a>例

```console
> dotnet-counters list

    Showing well-known counters only. Specific processes may support additional counters.
    System.Runtime
        cpu-usage                    Amount of time the process has utilized the CPU (ms)
        working-set                  Amount of working set used by the process (MB)
        gc-heap-size                 Total heap size reported by the GC (MB)
        gen-0-gc-count               Number of Gen 0 GCs / sec
        gen-1-gc-count               Number of Gen 1 GCs / sec
        gen-2-gc-count               Number of Gen 2 GCs / sec
        exception-count              Number of Exceptions / sec
```

## <a name="dotnet-counters-monitor"></a>dotnet-counters monitor

選択したカウンターの定期的に更新される値を表示します。

### <a name="synopsis"></a>構文

```console
dotnet-counters monitor [-h|--help] [-p|--process-id] [--refreshInterval] [counter_list]
```

### <a name="options"></a>オプション

- **`-p|--process-id <PID>`**

  監視するプロセスの ID。

- **`--refresh-interval <SECONDS>`**

  表示されているカウンターを更新するまでの遅延時間 (秒数)

- **`counter_list <COUNTERS>`**

  カウンターのスペース区切りリスト。 カウンターは `provider_name[:counter_name]` で指定できます。 `counter_name` を修飾せずに `provider_name` を使用すると、すべてのカウンターが表示されます。 プロバイダーとカウンターの名前を検出するには、[dotnet-counters list](#dotnet-counters-list) コマンドを使用します。

### <a name="examples"></a>使用例

- 3 秒の更新間隔で `System.Runtime` のすべてのカウンターを監視します。

  ```console
  > dotnet-counters monitor --process-id 1902  --refresh-interval 3 System.Runtime

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      Working Set (MB)                            1982
      GC Heap Size (MB)                            811
      Gen 0 GC / second                             20
      Gen 1 GC / second                              4
      Gen 2 GC / second                              1
      Number of Exceptions / sec                     4
  ```

- `System.Runtime` から CPU 使用率と GC ヒープ サイズのみを監視します。

  ```console
  > dotnet-counters monitor --process-id 1902 System.Runtime[cpu-usage,gc-heap-size]

  Press p to pause, r to resume, q to quit.
    System.Runtime:
      CPU Usage (%)                                 24
      GC Heap Size (MB)                            811
  ```

- ユーザー定義の `EventSource` の `EventCounter` 値を監視します。 詳しくは、「[チュートリアル: How to measure performance for very frequent events using EventCounters](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md)」を参照してください。

  ```console
  > dotnet-counters monitor --process-id 1902 Samples-EventCounterDemos-Minimal

  Press p to pause, r to resume, q to quit.
      request                                      100
  ```
