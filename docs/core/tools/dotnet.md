---
title: dotnet コマンド
description: dotnet コマンド (.NET Core CLI の汎用ドライバー) とその使用方法について説明します。
ms.date: 02/13/2020
ms.openlocfilehash: 8692d419afd528bf49e1dc7dc1a7a5fd698b363b
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134072"
---
# <a name="dotnet-command"></a>dotnet コマンド

**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン

## <a name="name"></a>名前

`dotnet` - .NET Core CLI の汎用ドライバー。

## <a name="synopsis"></a>構文

利用できるコマンドと環境に関する情報を取得するには:

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

コマンドを実行するには (SDK のインストールが必要):

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

アプリケーションを実行するには:

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

`--roll-forward` は、.NET Core 3.x 以降で利用できます。 .NET Core 2.x には `--roll-forward-on-no-candidate-fx` を使用します。

## <a name="description"></a>説明

`dotnet` コマンドには、次の 2 つの機能があります。

- .NET Core プロジェクトを操作するためのコマンドが用意されています。

  たとえば、[`dotnet build`](dotnet-build.md) を使うと、プロジェクトをビルドできます。 各コマンドには独自のオプションと引数が定義されています。 すべてのコマンドは、コマンドの使用方法に関する簡単なドキュメントを出力するための `--help` オプションをサポートしています。

- .NET Core アプリケーションを実行します。

  アプリケーションを実行するには、アプリケーション `.dll` ファイルへのパスを指定します。 たとえば、`dotnet myapp.dll` を使うと、`myapp` アプリケーションが実行されます。 展開オプションについては、「[.NET Core アプリケーションの展開](../deploying/index.md)」を参照してください。

## <a name="options"></a>オプション

`dotnet` 単独、コマンドの実行、アプリケーションの実行にはさまざまなオプションを使用できます。

### <a name="options-for-dotnet-by-itself"></a>dotnet 単独のオプション

次のオプションは、`dotnet` 単独のものです。 たとえば、`dotnet --info` のようにします。 環境に関する情報が出力されます。

- **`--info`**

  現在のオペレーティング システムや .NET Core バージョンのコミット SHA など、.NET Core インストールとコンピューター環境に関する詳細を出力します。

- **`--version`**

  使用中の .NET Core SDK のバージョンを印刷します。

- **`--list-runtimes`**

  インストールされている .NET Core ランタイムの一覧が出力されます。

- **`--list-sdks`**

  インストールされている .NET Core SDK の一覧が出力されます。

- **`-h|--help`**

  使用できるコマンドの一覧が出力されます。

### <a name="sdk-options-for-running-a-command"></a>コマンドを実行するための SDK のオプション

次のオプションは、コマンドを指定した `dotnet` 用です。 たとえば、`dotnet build --help` のようにします。

- **`-d|--diagnostics`**

  診断出力を有効にします。

- **`-v|--verbosity <LEVEL>`**

  コマンドの詳細レベルを設定します。 指定できる値は、`q[uiet]`、`m[inimal]`、`n[ormal]`、`d[etailed]`、および `diag[nostic]` です。 すべてのコマンドでサポートされているわけではありません。 このオプションを使用できるかどうかについては、そのコマンド ページを参照してください。

- **`-h|--help`**

  `dotnet build --help` など、特定のコマンドのドキュメントを出力します。

- **`command options`**

  各コマンドには、そのコマンドに固有のオプションが定義されています。 使用できるオプションの一覧については、そのコマンドのページを参照してください。

### <a name="runtime-options"></a>ランタイム オプション

次のオプションは、`dotnet` でアプリケーションを実行するときに使用できます。 たとえば、`dotnet myapp.dll --fx-version 3.1.1` のようにします。

- **`--additionalprobingpath <PATH>`**

  プローブ ポリシーとプローブするアセンブリを含むパスです。

- **`--additional-deps <PATH>`**

  追加の *.deps.json* ファイルへのパス。 *deps.json* ファイルには、依存関係、コンパイル依存関係、アセンブリ競合に対処するためのバージョン情報の一覧が含まれています。 詳細については、GitHub の「[Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)」 (ランタイム構成ファイル) を参照してください。

- **`--fx-version <VERSION>`**

  アプリケーションを実行するために使用する .NET Core ランタイムのバージョン。

- **`--runtimeconfig`**

  *runtimeconfig.json* ファイルへのパス。 *runtimeconfig.json* ファイルは、ランタイム設定を含む構成ファイルです。 詳細については、「[.NET Core ランタイム構成設定](../run-time-config/index.md#runtimeconfigjson)」を参照してください。

- **`--roll-forward-on-no-candidate-fx <N>`** **.NET Core 2.x SDK で使用できます。**

  必要な共有フレームワークが利用できない場合の動作を定義します。 `N` には以下があります。

  - `0` - マイナー バージョンのロールフォワードでも無効にします。
  - `1` - マイナー バージョンはロール フォワードしますが、メジャー バージョンはしません。 これが既定の動作です。
  - `2` - マイナー バージョンとメジャー バージョンをロール フォワードします。

   詳細については、「[Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward)」(ロールフォワード) を参照してください。

- **`--roll-forward <SETTING>`** **.NET Core SDK 3.0 以降で使用できます。**

  アプリにロール フォ ワードを適用する方法を制御します。 `SETTING` には次のいずれかの値を指定できます。 指定しない場合の既定は、`Minor` です。

  - `LatestPatch` - 最新のパッチ バージョンにロール フォワードします。 これで、マイナー バージョンのロールフォワードが無効になります。
  - `Minor` - 要求されたマイナー バージョンが見つからない場合は、それよりも高い最小マイナー バージョンにロール フォワードします。 要求されたマイナー バージョンが存在する場合は、LatestPatch ポリシーが使用されます。
  - `Major` - 要求されたメジャー バージョンが見つからない場合は、それよりも高い最小メジャー バージョンで最小マイナー バージョンにロール フォワードします。 要求されたメジャー バージョンが存在する場合は、Minor ポリシーが使用されます。
  - `LatestMinor` - 要求されたマイナー バージョンが存在する場合でも、最上位のマイナー バージョンにロール フォワードします。 コンポーネント ホスティング シナリオを対象としています。
  - `LatestMajor` - 要求されたメジャーが存在する場合でも、最上位のメジャー バージョンで最上位のマイナー バージョンにロール フォワードします。 コンポーネント ホスティング シナリオを対象としています。
  - `Disable` - ロール フォワードしません。 指定されたバージョンにのみバインドします。 このポリシーは、最新のパッチにロールフォワードする機能が無効になるため、一般的な使用にはお勧めできません。 この値はテスト用にのみ推奨されます。

`Disable` を除いて、すべての設定は使用できる最高のパッチ バージョンを使用します。

ロール フォワード動作は、プロジェクト ファイル プロパティ、ランタイム構成ファイル プロパティ、および環境変数でも構成できます。 詳細については、「[メジャーバージョン ランタイムのロールフォワード](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward)」を参照してください。

## <a name="dotnet-commands"></a>dotnet コマンド

### <a name="general"></a>全般

| コマンド                                       | 関数                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [dotnet build](dotnet-build.md)               | .NET Core アプリケーションをビルドします。                                     |
| [dotnet build-server](dotnet-build-server.md) | ビルドによって起動されたサーバーとやり取りします。                          |
| [dotnet clean](dotnet-clean.md)               | クリーン ビルド出力です。                                                |
| [dotnet help](dotnet-help.md)                 | コマンドのより詳細なドキュメントをオンラインで表示します。           |
| [dotnet migrate](dotnet-migrate.md)           | 有効な Preview 2 プロジェクトを .NET Core SDK 1.0 プロジェクトに移行します。  |
| [dotnet msbuild](dotnet-msbuild.md)           | MSBuild コマンド ラインへのアクセスを提供します。                        |
| [dotnet new](dotnet-new.md)                   | 指定されたテンプレートの C# または F# プロジェクトを初期化します。                |
| [dotnet pack](dotnet-pack.md)                 | コードの NuGet パッケージを作成します。                               |
| [dotnet publish](dotnet-publish.md)           | .NET Framework に依存するアプリケーションまたは自己完結型アプリケーションを発行します。 |
| [dotnet restore](dotnet-restore.md)           | 指定されたアプリケーションの依存関係を復元します。                  |
| [dotnet run](dotnet-run.md)                   | ソースからアプリケーションを実行します。                                   |
| [dotnet sln](dotnet-sln.md)                   | ソリューション ファイルのプロジェクトを追加、削除、一覧表示するオプション。       |
| [dotnet store](dotnet-store.md)               | ランタイム パッケージ ストアにアセンブリを格納します。                     |
| [dotnet test](dotnet-test.md)                 | テスト ランナーを使用してテストを実行します。                                     |

### <a name="project-references"></a>プロジェクト参照

コマンド | 関数
--- | ---
[dotnet add reference](dotnet-add-reference.md) | プロジェクト参照を追加します。
[dotnet list reference](dotnet-list-reference.md) | プロジェクト参照をリストします。
[dotnet remove reference](dotnet-remove-reference.md) | プロジェクト参照を削除します。

### <a name="nuget-packages"></a>NuGet パッケージ

コマンド | 関数
--- | ---
[dotnet add package](dotnet-add-package.md) | NuGet パッケージを追加します。
[dotnet remove package](dotnet-remove-package.md) | NuGet パッケージを削除します。

### <a name="nuget-commands"></a>NuGet コマンド

コマンド | 関数
--- | ---
[dotnet nuget delete](dotnet-nuget-delete.md) | サーバーからパッケージを削除または一覧から削除します。
[dotnet nuget push](dotnet-nuget-push.md) | パッケージをサーバーにプッシュして発行します。
[dotnet nuget locals](dotnet-nuget-locals.md) | HTTP 要求キャッシュ、一時的なキャッシュ、コンピューター全体のグローバル パッケージ フォルダーなどのローカルの NuGet リソースをクリアまたは一覧表示します。
[dotnet nuget add source](dotnet-nuget-add-source.md) | NuGet ソースを追加します。
[dotnet nuget disable source](dotnet-nuget-disable-source.md) | NuGet ソースを無効にします。
[dotnet nuget enable source](dotnet-nuget-enable-source.md) | NuGet ソースを有効にします。
[dotnet nuget list source](dotnet-nuget-list-source.md) | 構成されている NuGet ソースをすべて一覧表示します。
[dotnet nuget remove source](dotnet-nuget-remove-source.md) | NuGet ソースを削除します。
[dotnet nuget update source](dotnet-nuget-update-source.md) | NuGet ソースを更新します。

### <a name="global-tool-path-and-local-tools-commands"></a>グローバル、ツールパス、およびローカル ツールのコマンド

ツールは、NuGet パッケージからインストールされ、コマンド プロンプトから呼び出されるコンソール アプリケーションです。 ツールは自分で作成することも、サードパーティによって作成されたツールをインストールすることもできます。 ツールは、グローバル ツール、ツールパス ツール、およびローカル ツールとも呼ばれます。 詳細については、[.NET Core ツールの概要](global-tools.md)に関するページを参照してください。 グローバル ツールとツールパス ツールは、.NET Core SDK 2.1 以降使用できます。 ローカル ツールは、.NET Core SDK 3.0 以降使用できます。

コマンド | 関数
--- | ---
[dotnet tool install](dotnet-tool-install.md) | ツールをお使いのコンピューターにインストールします。
[dotnet tool list](dotnet-tool-list.md) | コンピューターに現在インストールされているグローバル、ツールパス、またはローカル ツールをすべて一覧表示します。
[dotnet tool uninstall](dotnet-tool-uninstall.md) | ツールをお使いのコンピューターからアンインストールします。
[dotnet tool update](dotnet-tool-update.md) | コンピューターにインストールされているツールを更新します。

### <a name="additional-tools"></a>その他のツール

.NET Core SDK 2.1.300 以降では、`DotnetCliToolReference` を使用してプロジェクト単位でのみ入手可能であった複数のツールを .NET Core SDK の一部として入手できるようになりました。 これらのツールを次の表に示します。

| ツール                                              | 関数                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| dev-certs                                         | 開発証明書を作成および管理します。                |
| [ef](/ef/core/miscellaneous/cli/dotnet)           | Entity Framework Core コマンドライン ツールです。                    |
| sql-cache                                         | SQL Server キャッシュ コマンドライン ツールです。                         |
| [user-secrets](/aspnet/core/security/app-secrets) | 開発ユーザーのシークレットを管理します。                            |
| [watch](/aspnet/core/tutorials/dotnet-watch)      | ファイルが変化するとコマンドを実行するファイル ウォッチャーを起動します。 |

各ツールの詳細については、`dotnet <tool-name> --help` と入力してください。

## <a name="examples"></a>使用例

新しい .NET Core コンソール アプリケーションを作成します。

```dotnetcli
dotnet new console
```

指定されたディレクトリにプロジェクトとその依存関係をビルドします。

```dotnetcli
dotnet build
```

アプリケーションを実行します。

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a>環境変数

- `DOTNET_ROOT`、`DOTNET_ROOT(x86)`

  .NET Core ランタイムが既定の場所にインストールされていない場合、それらの場所を指定します。 Windows 上の既定の場所は `C:\Program Files\dotnet` です。 Linux と macOS 上の既定の場所は `/usr/share/dotnet` です。 この環境変数は、生成された実行可能ファイル (apphosts) を介してアプリを実行する場合にのみ使用されます。 64 ビット OS 上で 32 ビット実行可能ファイルを実行する場合は、代わりに `DOTNET_ROOT(x86)` が使用されます。

- `DOTNET_PACKAGES`

  グローバル パッケージ フォルダー。 設定されていない場合は、既定で `~/.nuget/packages` (Unix の場合) または `%userprofile%\.nuget\packages` (Windows の場合) になります。

- `DOTNET_SERVICING`

  ランタイムの読み込み時に共有ホストで使用するサービス インデックスの場所を指定します。

- `DOTNET_NOLOGO`

  最初の実行時に .NET Core のウェルカム メッセージとテレメトリ メッセージを表示するかどうかを指定します。 `true` に設定すると、これらのメッセージは表示されません (値 `true`、`1`、または `yes` が受け入れられます)。`false` に設定すると許可されます (値 `false`、`0`、または `no` が受け入れられます)。 設定しない場合、既定値は `false` であり、最初の実行時にメッセージが表示されます。 このフラグはテレメトリに影響しないことに注意してください (テレメトリの送信のオプトアウトについては `DOTNET_CLI_TELEMETRY_OPTOUT` を参照)。

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  .NET Core ツールの使用に関するデータを収集し、Microsoft に送信するかどうかを指定します。 `true` に設定するとテレメトリ機能が無効になります (指定できる値は `true`、`1`、または `yes` です)。 それ以外の場合は `false` に設定します。この場合、テレメトリ機能が有効になります (指定できる値は `false`、`0`、または `no` です)。 設定されていない場合、既定で `false` になり、テレメトリ機能はアクティブになります。

- `DOTNET_MULTILEVEL_LOOKUP`

  .NET Core ランタイム、共有フレームワーク、または SDK がグローバルな場所から解決されるかどうかを指定します。 設定されていない場合、既定値は 1 (論理 `true`) です。 グローバルな場所から解決せず、.NET Core インストールを分離するには、0 (論理 `false`) に設定します。 複数レベルのルックアップの詳細については、「[Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md)」 (複数レベルの SharedFX ルックアップ) を参照してください。

- `DOTNET_ROLL_FORWARD` **.NET Core 3.x SDK 以降で使用できます。**

  ロール フォワード動作を決定します。 詳細については、この記事で前述した `--roll-forward` オプションを参照してください。

- `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **.NET Core 2.x SDK で使用できます。**

  `0` に設定されている場合、マイナー バージョンのロールフォワードを無効にします。 詳細については、「[Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward)」(ロールフォワード) を参照してください。

- `DOTNET_CLI_UI_LANGUAGE`

  `en-us` などのロケール値を使用して、CLI UI の言語を設定します。 サポートされている値は、Visual Studio の場合と同じです。 詳細については、[Visual Studio のインストール ドキュメント](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)のインストーラーの言語を変更する方法に関するセクションを参照してください。 .NET リソース マネージャーの規則が適用されるため、完全一致を選択する必要はありません。`CultureInfo` ツリーで子孫を選択することもできます。 たとえば、`fr-CA` に設定すると、CLI によって `fr` の翻訳が検索され、使用されます。 サポートされていない言語に設定すると、CLI は英語にフォールバックします。

- `DOTNET_DISABLE_GUI_ERRORS`

  GUI 対応の生成された実行可能ファイルの場合、通常は特定のクラスのエラーに対して表示されるダイアログ ポップアップが無効になります。 この場合、`stderr` にのみ書き込まれ、終了します。
  
- `DOTNET_ADDITIONAL_DEPS`

  CLI オプション `--additional-deps` に相当します。

- `DOTNET_RUNTIME_ID`

  検出された RID をオーバーライドします。

- `DOTNET_SHARED_STORE`

  アセンブリの解決がフォールバックする "共有ストア" の場所。

- `DOTNET_STARTUP_HOOKS`

  スタートアップ フックを読み込み、実行するアセンブリの一覧。

- `COREHOST_TRACE`、`COREHOST_TRACEFILE`、`COREHOST_TRACE_VERBOSITY`

  `dotnet.exe`、`hostfxr`、`hostpolicy` などのホスティング コンポーネントからの診断トレースを制御します。

## <a name="see-also"></a>関連項目

- [ランタイム構成ファイル](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [.NET Core ランタイム構成設定](../run-time-config/index.md)
