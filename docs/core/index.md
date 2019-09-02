---
title: .NET Core のガイド
description: .NET Core は、Windows、Linux、および Mac アプリを作成するためのモジュール型の高性能な .NET 実装です。 ここでは、.NET Core の概要について説明します。
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: db4daa8c78a181f0599c4c75ccd31f46ee278e63
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202827"
---
# <a name="net-core-guide"></a>.NET Core のガイド

[.NET Core](about.md) は、Microsoft および .NET コミュニティによって [GitHub](https://github.com/dotnet/core) 上で管理されている、[オープンソース](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)の汎用的な開発プラットフォームです。 クロスプラットフォーム (Windows、macOS、Linux をサポート) であり、デバイス、クラウド、および IoT アプリケーションを構築するために使用できます。

特徴、サポートされる言語とフレームワーク、キー API など、.NET Core について詳しくは、「[About .NET Core](about.md)」(.NET Core について) をご覧ください。

「[.NET Core チュートリアル](tutorials/index.md)」では、単純な .NET Core アプリケーションを作成する方法を学習できます。 最初のアプリを、ほんの数分で起動および実行できます。 ブラウザーで .NET Core を使用してみる場合は、[C# における数値](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)に関するオンライン チュートリアルをご覧ください。

## <a name="download-net-core-22"></a>.NET Core 2.2 のダウンロード

[.NET Core  2.2 SDK](https://www.microsoft.com/net/download) をダウンロードして、Windows、macOS、または Linux マシンで .NET Core をお試しください。 Docker コンテナーを使用する方がよければ、[dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) にアクセスしてください。

別の .NET Core バージョンを探している場合も、すべての .NET Core バージョンを [.NET Core のダウンロード](https://www.microsoft.com/net/download/archives)で入手できます。

## <a name="net-core-22"></a>.NET Core 2.2

最新バージョンは [.NET Core 2.2](whats-new/dotnet-core-2-2.md) です。 新機能には、フレームワーク依存の配置、スタートアップ フック、Azure SQL での AAD 認証、Windows ARM32 のサポートが含まれます。

## <a name="create-your-first-application"></a>最初のアプリケーションの作成

.NET Core SDK をインストールしたらコマンド プロンプトを開きます。 次の `dotnet` コマンドを入力し、C# アプリケーションを作成して実行します。

```console
dotnet new console
dotnet run
```

次の出力が表示されます。

```output
Hello World!
```

## <a name="support"></a>サポート

.NET Core は、Microsoft Windows、macOS、Linux で[サポート](https://www.microsoft.com/net/support/policy)されています。 年に数回、通常は毎月、セキュリティと品質向上のために更新されます。

.NET Core のバイナリ形式の配布は、Azure 内のマイクロソフトが管理するサーバーで構築されてテストされ、他のすべてのマイクロソフト製品と同様にサポートされます。

Red Hat Enterprise Linux (RHEL) では [.NET Core は Red Hat によってサポート](http://redhatloves.net/)されます。 Red Hat がソースから .NET Core をビルドして、[Red Hat ソフトウェア コレクション](https://developers.redhat.com/products/softwarecollections/overview/)で使用できるようにします。 Red Hat とマイクロソフトが共同して、.NET Core が RHEL 上で適切に動作するようにします。
