---
title: Docker アプリの開発環境
description: Docker 開発のライフ サイクルをサポートする最も重要な開発ツールのオプションの確認を取得します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 3a2fcbe3b9380083622b6ce72cea4bab17d7c2ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799321"
---
# <a name="development-environment-for-docker-apps"></a>Docker アプリの開発環境

## <a name="development-tools-choices-ide-or-editor"></a>開発ツールの選択:IDE またはエディター

いたとしてもする場合、完全で強力な IDE または軽量でアジャイルなエディターでは、マイクロソフトは、Docker アプリケーションの開発なったときに対応しています。

### <a name="visual-studio-code-and-docker-cli-cross-platform-tools-for-mac-linux-and-windows"></a>Visual Studio Code と Docker CLI (Mac、Linux、および Windows 用のクロス プラットフォーム ツール)

軽量でクロスプラット フォーム対応のエディターが任意の開発言語をサポートしている場合は、Visual Studio Code と Docker CLI を使用することができます。 これらの製品では、開発者のワークフローを合理化するための重要なは、簡単かつ堅牢のエクスペリエンスを提供します。 "Docker for Mac"または"Docker for Windows"(開発環境) をインストールすると、Docker 開発者は、Windows または Linux (ランタイム環境) の両方のアプリを構築するのに 1 つの Docker CLI を使用できます。 さらに、Visual Studio Code エディターから Docker コマンドを実行するには、Dockerfile とショートカット タスク用の IntelliSense での Docker の拡張機能をサポートしています。

> [!NOTE]
>
> Visual Studio Code をダウンロードするには<https://code.visualstudio.com/download>します。
>
> Mac および Windows 用 Docker をダウンロードするには<https://www.docker.com/products/docker>します。

### <a name="visual-studio-with-docker-tools-windows-development-machine"></a>Visual Studio と Docker Tools (Windows 開発用コンピューター)

Visual Studio 2017 (またはそれ以降) を使用することをお勧めします。 有効になっている組み込みの Docker ツールを使用します。 Visual Studio を使用して開発、実行、および選択した Docker 環境で直接アプリケーションを検証することができます。 F5 キーを押して、Docker ホストで直接アプリケーション (1 つのコンテナーまたは複数のコンテナー) をデバッグまたはを編集して、コンテナーを再構築しなくても、アプリを更新するには、Ctrl + F5 キーを押します。 Linux または Windows の Docker コンテナーを作成するための Windows 開発者向けの最も簡単で最も強力な選択肢となります。

### <a name="visual-studio-for-mac-mac-development-machine"></a>Visual Studio for Mac (Mac 開発用コンピューター)

使用することができます[Visual Studio for Mac](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) Docker ベースのアプリケーションを開発するときにします。 Visual Studio for Mac は、Visual Studio Code for mac と比較した場合の高度な IDE を提供しています

## <a name="language-and-framework-choices"></a>言語とフレームワークの選択

ほとんどの最新の言語でマイクロソフトのツールを使用する Docker アプリケーションを開発することができます。 最初のリストを次に示しますが、それに制限されておらず。

- .NET Core および ASP.NET Core
- Node.js
- 移動
- Java
- Ruby
- Python

基本的には、Linux または Windows で Docker でサポートされている最新の言語を使用することができます。

>[!div class="step-by-step"]
>[前へ](deploy-azure-kubernetes-service.md)
>[次へ](docker-apps-inner-loop-workflow.md)
