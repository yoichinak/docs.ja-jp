---
title: Docker ベースのアプリケーションの開発プロセス
description: Docker ベースのアプリケーションの開発のオプションに関する大まかな概要を確認します。 マルチ プラットフォームのサポート (Windows、Mac、Linux) のため、Windows 用 Visual Studio、Visual Studio for Mac、または Visual Studio Code のうち好みのものを使います。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/27/2018
---
# <a name="development-process-for-docker-based-applications"></a>Docker ベースのアプリケーションの開発プロセス

*Visual Studio と Visual Studio Tools for Docker を使用して IDE に重点を置くか、Docker CLI と Visual Studio Code を使用して CLI/エディターに重点を置くか、好みの方法でコンテナー化された .NET アプリケーションを開発します。*

## <a name="development-environment-for-docker-apps"></a>Docker アプリの開発環境

### <a name="development-tool-choices-ide-or-editor"></a>開発ツールの選択:IDE またはエディター

完全で強力な IDE または軽量でアジャイルなエディターのどちらを選んでも、Microsoft では Docker アプリケーションの開発に使用できるツールが用意されています。

**Visual Studio (Windows 版)。** Visual Studio を使って Docker ベースのアプリケーションを開発する場合は、既に組み込まれている Docker 用ツールに付属する Visual Studio 2017 バージョン 15.7 以降を使うことをお勧めします。 Tools for Docker を使用して、ターゲットの Docker 環境で直接アプリケーションの開発、実行、および検証ができます。 F5 キーを押すと、Docker ホスト内で直接アプリケーション (1 つのコンテナー、または複数のコンテナー) を実行してデバックできます。または、CTRL キーを押しながら F5 キーを押すと、コンテナーを再構築しなくても、アプリケーションを編集して更新できます。 これは、Docker ベース アプリを開発する場合の最も強力な選択肢です。

**Visual Studio for Mac。** これは macOS で動作する IDE であり、Xamarin Studio が進化したものです。2017 年中頃から Docker をサポートしています。 これは、強力な IDE を使用したい Mac コンピューターで作業する開発者にとって好ましい選択肢です。

**Visual Studio Code と Docker CLI**。 任意の開発言語をサポートする軽量なクロスプラット フォーム エディターを選択すると、Microsoft Visual Studio Code (VS Code) と Docker CLI を使用することができます。 これは、Mac、Linux、および Windows のクロスプラット フォーム開発アプローチです。 さらに、Visual Studio Code は、Dockerfiles の IntelliSense などの Docker の拡張機能や、エディターから Docker コマンドを実行するショートカット タスクをサポートします。

[Docker Community Edition (CE)](https://www.docker.com/community-edition) ツールをインストールすることで、1 つの Docker CLI を使用して Windows と Linux の両方のアプリを構築することができます。

### <a name="additional-resources"></a>その他の技術情報

- **Visual Studio**。 公式サイト。 \
  [*https://visualstudio.microsoft.com/vs/*](https://visualstudio.microsoft.com/vs/)

- **Visual Studio Code**。 公式サイト。 \
  [*https://code.visualstudio.com/download*](https://code.visualstudio.com/download)

- **Mac および Windows の Docker Community Edition (CE)** \
  [*https://www.docker.com/community-editions*](https://www.docker.com/community-edition)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>.NET 言語および Docker コンテナーのフレームワーク

このガイドの前のセクションで触れたように、Docker コンテナー化された NET アプリケーションを開発する際に、.NET Framework、.NET Core、またはオープン ソースの Mono プロジェクトを使用できます。 Linux または Windows コンテナーをターゲットにする場合、使用している .NET Framework に応じて、C\#、F\#、または Visual Basic で開発できます。 .NET 言語の詳細については、ブログ投稿「[The .NET Language Strategy](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/)」 (.NET 言語戦略) を参照してください。

>[!div class="step-by-step"]
>[前へ](../architect-microservice-container-applications/using-azure-service-fabric.md)
>[次へ](docker-app-development-workflow.md)