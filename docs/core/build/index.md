---
title: ソースから .NET Core をビルドする
description: ソース コードから .NET Core と .NET Core CLI をビルドする方法を説明します。
author: bleroy
ms.date: 06/28/2017
ms.custom: seodec18
ms.openlocfilehash: dcd7c909325eec5a79db74098d7ac880000eafa1
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/28/2019
ms.locfileid: "70105392"
---
# <a name="build-net-core-from-source"></a>ソースから .NET Core をビルドする

ソース コードから .NET Core をビルドできることは、複数の方法において重要なことです。 .NET Core を新しいプラットフォームに簡単に移植でき、製品に対するコントリビューションと修正を有効にすることができ、また、.NET のカスタム バージョンを作成することができます。
この記事では、独自のバージョンの .NET Core をビルドして配布する開発者向けのガイダンスを提供します。

## <a name="build-the-clr-from-source"></a>ソースから CLR をビルドする

.NET CoreCLR のソース コードは、GitHub の [dotnet/coreclr](https://github.com/dotnet/coreclr/) リポジトリにあります。

ビルドは、現在、次の前提条件に依存しています。

- [Git](https://git-scm.com/)
- [CMake](https://cmake.org/)
- [Python](https://www.python.org/)
- C++ コンパイラ。

これらの前提条件をインストールしたら、[dotnet/coreclr リポジトリ](https://github.com/dotnet/coreclr/)の下部にあるビルド スクリプト (Windows の場合は `build.cmd`、Linux と macOS の場合は `build.sh`) を呼び出して、CLR をビルドできます。

コンポーネントのインストールは、オペレーティング システム (OS) によって異なります。 以下の特定の OS のビルド手順を参照してください。

- [Windows](https://github.com/dotnet/coreclr/blob/master/Documentation/building/windows-instructions.md)
- [Linux](https://github.com/dotnet/coreclr/blob/master/Documentation/building/linux-instructions.md)
- [macOS](https://github.com/dotnet/coreclr/blob/master/Documentation/building/osx-instructions.md)
- [FreeBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/freebsd-instructions.md)
- [NetBSD](https://github.com/dotnet/coreclr/blob/master/Documentation/building/netbsd-instructions.md)

OS 間でのクロス ビルドはありません (X64 にビルドされる ARM の場合のみ)。  
特定のプラットフォームのビルドは、そのプラットフォームで行う必要があります。  

ビルドには、次の主な 2 つの `buildTypes` があります。

- デバッグ (既定) - 最小限の最適化と追加のランタイム チェック (アサート) を実行してランタイムをコンパイルします。 最適化レベルを抑えるとともに追加のチェックを行うため、ランタイム実行の速度は低下しますが、デバッグには有用です。 この設定は、開発環境およびテスト環境で推奨されます。
- リリース - 追加のランタイム チェックは実行せず、完全な最適化を行いランタイムをコンパイルします。 実行時間を大きく短縮できますが、ビルドにかかる時間が増大するとともに、デバッグが困難になる可能性があります。 このビルドの種類を選択するには、`release` をビルド スクリプトに渡します。

さらに、既定では、ビルドでランタイムの実行可能ファイルの作成だけでなく、すべてのテストのビルドも行われます。
かなり多くのテストがあり、単に変更を試みる場合には必要のない非常に長い時間を要します。
次の例のように、ビルド スクリプトに `skiptests` 引数を追加することで、これらのテスト ビルドをスキップできます (Unix コンピューターでは `.\build` を `./build.sh` に置き換えます)。

```bat
    .\build skiptests
```

前の例では、開発時のチェック (アサート) を有効にし、最適化を無効にして `Debug` フレーバーをビルドする方法について説明しました。 リリース (フル スピード) フレーバーをビルドするには、次のようにします。

```bat
    .\build release skiptests
```

-? または -help 修飾子を使用すれば、他のビルド オプションを 見つけることができます。

### <a name="using-your-build"></a>ビルドの使用

ビルドでは、リポジトリの下部の `bin` ディレクトリに生成されたすべてのファイルが配置されます。
*bin\Log* ディレクトリには、ビルド時に生成されるログ ファイル (ビルドに失敗した場合に最も役立つ) が含まれています。
実際の出力は、*bin\Product\Windows_NT.x64.Release* などの *bin\Product\[platform].[CPU architecture].[build type]* ディレクトリに配置されます。

ビルドの "生" 出力が役立つ場合もありますが、通常は、前の出力ディレクトリの `.nuget\pkg` サブディレクトリに配置される、NuGet パッケージのみを使用します。

新しいランタイムを使用する場合、次の 2 つの基本的な方法があります。

 1. **dotnet.exe と NuGet を使用して、アプリケーションを作成します**。
    作成した NuGet パッケージと 'dotnet' コマンド ライン インターフェイス (CLI) を使用して、新しいランタイムを使用するプログラムを作成する手順については、「[ビルドの使用](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingYourBuild.md)」を参照してください。 この方法では、ランタイム開発者以外が新しいランタイムを使用する可能性があります。

 2. **corerun.exe を使用し、解凍した DLL を使用してアプリケーションを実行します**。
    このリポジトリでは、NuGet に依存しない corerun.exe という単純なホストの定義も行います。
    実際に使用する必要な DLL を取得する場所をホストに指示する必要があり、これらの DLL は手動で収集する必要があります。
    この方法は、[dotnet/coreclr リポジトリ](https://github.com/dotnet/coreclr)のすべてのテストで使用され、事前の単体テストなどの、クイック ローカル "編集-コンパイル-デバッグ" ループに役立ちます。
    この方法の使用の詳細については、「[Executing .NET Core Apps with CoreRun.exe](https://github.com/dotnet/coreclr/blob/master/Documentation/workflow/UsingCoreRun.md)」 (CoreRun.exe を使用する .NET Core アプリの実行) を参照してください。

## <a name="build-the-cli-from-source"></a>ソースから CLI をビルドする

.NET Core CLI のソース コードは、GitHub の [dotnet/cli](https://github.com/dotnet/cli/) リポジトリにあります。

.NET Core CLI をビルドするには、コンピューターに以下をインストールする必要があります。

- Windows および Linux:
  - パスの git
- macOS:
  - パスの git
  - Xcode
  - Openssl

ビルドするには、Windows の場合は `build.cmd` を、Linux と macOS の場合は `build.sh` をルートから実行します。 テストを実行しない場合は、`build.cmd -t:Compile` または `./build.sh -t:Compile` を実行します。 macOS Sierra で CLI をビルドするには、`export DOTNET_RUNTIME_ID=osx.10.11-x64` を実行して、DOTNET_RUNTIME_ID 環境変数を設定する必要があります。

### <a name="using-your-build"></a>ビルドの使用

*artifacts/{os}-{arch}/stage2* の `dotnet` 実行可能ファイルを使用して、新しくビルドされた CLI を試します。 現在のコンソールから `dotnet` を呼び出す際にビルド出力を使用する場合は、*artifacts/{os}-{arch}/stage2* をパスに追加することもできます。

## <a name="see-also"></a>関連項目

- [.NET Core 共通言語ランタイム (CoreCLR)](https://github.com/dotnet/coreclr/blob/master/README.md)
- [.NET Core CLI 開発者ガイド](https://github.com/dotnet/cli/blob/master/Documentation/project-docs/developer-guide.md)
- [.NET Core の配布パッケージ](./distribution-packaging.md)
