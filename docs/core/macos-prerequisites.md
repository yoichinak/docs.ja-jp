---
title: Mac における .NET Core の前提条件
description: macOS コンピューターで .NET Core アプリケーションを開発、展開、および実行するために必要なサポート対象 macOS のバージョンと .NET Core の依存関係。
author: guardrex
ms.author: adegeo
ms.custom: updateeachvsrelease
ms.date: 12/14/2018
ms.openlocfilehash: cee57856c75ce4424bee8d96fccfa5a6aee2dbf5
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59317871"
---
# <a name="prerequisites-for-net-core-on-macos"></a>macOS における .NET Core の前提条件

この記事では、macOS コンピューターで .NET Core アプリケーションを開発、展開、および実行するために必要なサポート対象 macOS のバージョンと .NET Core の依存関係を示します。 後述のサポート対象 OS のバージョンと依存関係は、Mac で .NET Core アプリを開発する 3 つの方法 ([好きなエディターでコマンド ラインを使用](tutorials/using-with-xplat-cli.md)、[Visual Studio Code を使用](https://code.visualstudio.com/)、および [Visual Studio for Mac を使用](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)) に適用されます。

## <a name="supported-macos-versions"></a>サポート対象の macOS のバージョン

# [<a name="net-core-2x"></a>.NET Core 2.x](#tab/netcore2x)

.NET Core 2.x は、macOS の次のバージョンでサポートされています。

* macOS 10.12 "Sierra" 以降のバージョン

.NET Core 2.1 と .NET Core 2.2 がサポートされているオペレーティング システム、ディストリビューション、バージョン、サポートされていない OS バージョン、ライフサイクル ポリシー リンクの完全なリストについては、[.NET Core 2.1 がサポートされる OS バージョン](https://github.com/dotnet/core/blob/master/release-notes/2.1/2.1-supported-os.md)と [.NET Core 2.2 がサポートされている OS バージョン](https://github.com/dotnet/core/blob/master/release-notes/2.2/2.2-supported-os.md)に関するページを参照してください。

ダウンロード リンクと詳細については、[.NET Core 2.2 のダウンロード](https://www.microsoft.com/net/download/dotnet-core/2.2)または [.NET Core 2.1](https://www.microsoft.com/net/download/dotnet-core/2.1) のダウンロードのページを参照してください。

# [<a name="net-core-1x"></a>.NET Core 1.x](#tab/netcore1x)

.NET Core 1.x は、macOS の次のバージョンでサポートされています。

* macOS 10.12 "Sierra"
* macOS 10.11 "El Capitan"

.NET Core 1.1 と .NET Core 1.0 がサポートされているオペレーティング システム、ディストリビューション、バージョン、サポートされていない OS バージョン、ライフサイクル ポリシー リンクの完全なリストについては、[.NET Core 1.1 がサポートされる OS バージョン](https://github.com/dotnet/core/blob/master/release-notes/1.1/1.1.md)と [.NET Core 1.0 がサポートされている OS バージョン](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0-supported-os.md)に関するページを参照してください。

ダウンロード リンクと詳細については、[.NET Core 1.1 のダウンロード](https://www.microsoft.com/net/download/dotnet-core/1.1)または [.NET Core 1.0](https://www.microsoft.com/net/download/dotnet-core/1.0) のダウンロードのページを参照してください。

# [<a name="net-core-30"></a>.NET Core 3.0](#tab/netcore30)

.NET Core 3.0 Preview 3 は、macOS の次のバージョンでサポートされています。

* macOS 10.12 "Sierra" 以降のバージョン

.NET Core 3.0 でサポートされているオペレーティング システム、ディストリビューション、バージョン、サポートされていない OS バージョン、ライフサイクル ポリシー リンクの完全なリストについては、[.NET Core 3.0 がサポートされる OS バージョン](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)に関するページを参照してください。

ダウンロード リンクと詳細については、[.NET Core 3.0 のダウンロード](https://www.microsoft.com/net/download/dotnet-core/3.0) ページを参照してください。

---

## <a name="net-core-dependencies"></a>.NET Core の依存関係

# [<a name="net-core-2x"></a>.NET Core 2.x](#tab/netcore2x)

[.NET ダウンロード](https://www.microsoft.com/net/download/core)から .NET Core SDK をダウンロードしてインストールします。 macOS でインストールに関する問題が発生した場合は、[既知の問題](https://github.com/dotnet/core/tree/master/release-notes/2.1)に関するトピックで、インストールされているバージョンに関する記述をご覧ください。

# [<a name="net-core-1x"></a>.NET Core 1.x](#tab/netcore1x)

macOS で実行する場合、.NET Core 1.x には OpenSSL が必要になります。 OpenSSL を取得する簡単な方法は、macOS の [Homebrew ("brew")](https://brew.sh/) パッケージ マネージャーを使用することです。 *brew* をインストールしたら、端末 (コマンド) プロンプトで次のコマンドを実行して OpenSSL をインストールします。

```console
brew update
brew install openssl
mkdir -p /usr/local/lib
ln -s /usr/local/opt/openssl/lib/libcrypto.1.0.0.dylib /usr/local/lib/
ln -s /usr/local/opt/openssl/lib/libssl.1.0.0.dylib /usr/local/lib/
```

[.NET ダウンロード](https://www.microsoft.com/net/download/core)から .NET Core SDK をダウンロードしてインストールします。 macOS でインストールに関する問題が発生した場合は、「[1.0.0 Known Issues (1.0.0 の既知の問題)](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.0-known-issues.md)」と「[1.0.1 Known Issues (1.0.1 の既知の問題)](https://github.com/dotnet/core/blob/master/release-notes/1.0/1.0.1-known-issues.md)」のトピックをご覧ください。

# [<a name="net-core-30"></a>.NET Core 3.0](#tab/netcore30)

[.NET ダウンロード](https://www.microsoft.com/net/download/core)から .NET Core SDK をダウンロードしてインストールします。 macOS でインストールに関する問題が発生した場合は、[リリース ノート](https://github.com/dotnet/core/blob/master/release-notes/3.0/3.0-supported-os.md)のトピックで、インストールされているバージョンに関する記述をご覧ください。

---

## <a name="increase-the-maximum-open-file-limit-net-core-versions-before-net-core-sdk-202"></a>開けるファイルの最大数を増やす (.NET Core SDK 2.0.2 より前のバージョンの .NET Core) 

古いバージョンの .NET Core では (.NET Core SDK 2.0.2 より前)、開けるファイルに関する macOS の既定の最大数では、プロジェクトの復元や単体テストの実行など、一部の .NET Core ワークロードに十分ではないことがあります。

この上限は次の手順で増やすことができます。

1. テキスト エディターを利用し、新しいファイル _/Library/LaunchDaemons/limit.maxfiles.plist_ を作成し、以下のコンテンツでファイルを保存します。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
  <dict>
    <key>Label</key>
    <string>limit.maxfiles</string>
    <key>ProgramArguments</key>
    <array>
      <string>launchctl</string>
      <string>limit</string>
      <string>maxfiles</string>
      <string>2048</string>
      <string>4096</string>
    </array>
    <key>RunAtLoad</key>
    <true/>
    <key>ServiceIPC</key>
    <false/>
  </dict>
</plist>
```

2. 端末ウィンドウで次のコマンドを実行します。

   ```console
   echo 'ulimit -n 2048' | sudo tee -a /etc/profile
   ```

3. Mac を再起動して設定を適用します。

## <a name="visual-studio-for-mac"></a>Visual Studio for Mac

.NET Core SDK を使用して .NET Core アプリケーションを開発する場合は、好きなエディターを使用できます。 ただし、Mac 上の統合開発環境で .NET Core アプリケーションを開発する場合には、[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) を使用できます。 

macOS 上で Visual Studio for Mac を使用して .NET Core で開発を行うには、以下のものが必要です。

* サポートされているバージョンの macOS オペレーティング システム
* OpenSSL (.NET Core 1.x のみ。NET Core 2.x では、macOS でネイティブ利用できるセキュリティ サービスが利用されます。)
* .NET Core SDK for Mac
* [Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
