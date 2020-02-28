---
title: 'チュートリアル: .NET Core グローバル ツールをインストールして使用する'
description: .NET ツールをグローバル ツールとしてインストールして使用する方法について説明します。
ms.date: 02/12/2020
ms.openlocfilehash: 65047af9d8a7f2fd4c1a07f65af3a6ddbf870c5d
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543822"
---
# <a name="tutorial-install-and-use-a-net-core-global-tool-using-the-net-core-cli"></a>チュートリアル: .NET Core CLI を使って .NET Core グローバル ツールをインストールして使用する

**この記事の対象:** ✔️ .NET Core 2.1 SDK 以降のバージョン

このチュートリアルでは、グローバル ツールをインストールして使用する方法について説明します。 [このシリーズの最初のチュートリアル](global-tools-how-to-create.md)で作成されるツールを使用します。

## <a name="prerequisites"></a>必須コンポーネント

* [このシリーズの最初のチュートリアル](global-tools-how-to-create.md)を完了します。

## <a name="use-the-tool-as-a-global-tool"></a>グローバル ツールとしてツールを使用する

1. *botsay-\<name>* プロジェクト フォルダーに [dotnet tool install](dotnet-tool-install.md) コマンドを実行して、パッケージからツールをインストールします。

   ```dotnetcli
   dotnet tool install --global --add-source ./nupkg botsay-<name>
   ```

   `--global` パラメーターでは、PATH 環境変数に自動的に追加される既定の場所にツール バイナリをインストールするように、.NET Core CLI に指示します。

   `--add-source` パラメーターでは、NuGet パッケージへの追加のソース フィードとして *./nupkg* ディレクトリを一時的に使用するように、.NET Core CLI に指示します。 Nuget.org サイト上ではなく、必ず *./nupkg* ディレクトリ内だけで見つかるように、パッケージには一意の名前を付けました。 

   出力には、ツールの呼び出しに使用されたコマンドと、インストールされているバージョンが示されます。

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
   ```

1. ツールを起動します。

   ```console
   botsay hello from the bot
   ```

   > [!NOTE]
   > このコマンドが失敗すると、新しいターミナルを開いて PATH を更新することが必要になる場合があります。

1. [dotnet tool uninstall](dotnet-tool-uninstall.md) コマンドを実行して、ツールを削除します。

   ```dotnetcli
   dotnet tool uninstall -g botsay-<name>
   ```

## <a name="use-the-tool-as-a-global-tool-installed-in-a-custom-location"></a>カスタムの場所にインストールされているグローバル ツールとしてツールを使用する

1. パッケージからツールをインストールします。

   Windows の場合:

   ```dotnetcli
   dotnet tool install --tool-path c:\dotnet-tools --add-source ./nupkg botsay-<name>
   ```

   Linux または macOS の場合:

   ```dotnetcli
   dotnet tool install --tool-path ~/bin --add-source ./nupkg botsay-<name>
   ```

   `--tool-path` パラメーターでは、指定された場所にツール バイナリをインストールするように、.NET Core CLI に指示します。 ディレクトリが存在しなければ、作成されます。 このディレクトリは、PATH 環境変数に自動的に追加されるわけではありません。

   出力には、ツールの呼び出しに使用されたコマンドと、インストールされているバージョンが示されます。

   ```console
   You can invoke the tool using the following command: botsay
   Tool 'botsay-<name>' (version '1.0.0') was successfully installed.
   ```

1. ツールを起動します。

   Windows の場合:

   ```console
   c:\dotnet-tools\botsay hello from the bot
   ```

   Linux または macOS の場合:

   ```console
   ~/bin/botsay hello from the bot
   ```

1. [dotnet tool uninstall](dotnet-tool-uninstall.md) コマンドを実行して、ツールを削除します。

   Windows の場合:

   ```dotnetcli
   dotnet tool uninstall --tool-path c:\dotnet-tools botsay --add-source ./nupkg botsay-<name>
   ```

   Linux または macOS の場合:

   ```dotnetcli
   dotnet tool uninstall --tool-path ~/bin botsay-<name>
   ```

## <a name="troubleshoot"></a>トラブルシューティング

チュートリアルの実行中にエラー メッセージが表示された場合は、「[.NET Core ツールの使用に関する問題のトラブルシューティング](troubleshoot-usage-issues.md)」を参照してください。

## <a name="next-steps"></a>次の手順

このチュートリアルでは、ツールをグローバル ツールとしてインストールして使用しました。 ローカル ツールと同じツールをインストールして使用するには、次のチュートリアルに進んでください。

> [!div class="nextstepaction"]
> [ローカル ツールをインストールして使用する](local-tools-how-to-use.md)
