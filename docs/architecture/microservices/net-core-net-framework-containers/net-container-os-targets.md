---
title: .NET コンテナーで対象とする OS
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | .NET コンテナーで対象とする OS'
ms.date: 01/07/2019
ms.openlocfilehash: 7380889374e69ca4d3c981a401af703c19263de5
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039686"
---
# <a name="what-os-to-target-with-net-containers"></a>.NET コンテナーで対象とする OS

Docker でサポートされているオペレーティング システムの多様性と、.NET Framework と .NET Core の違いを考慮し、使用しているフレームワークに応じて特定の OS と特定のバージョンを対象にする必要があります。

Windows の場合、Windows Server Core または Windows Nano Server を使用できます。 これらの Windows バージョンには、.NET Framework または .NET Core で必要になる可能性がある異なる特性 (Windows Server Core の IIS と Nest Server の Kestrel のような自己ホスト型 Web サーバー) があります。

Linux の場合、複数のディストリビューションを利用できます。また、Linux は公式の .NET Docker イメージ (Debian など) でサポートされています。

使用している .NET Framework に応じて使用できる OS のバージョンについては、図 3-1 を参照してください。

![.NET Framework のレガシー アプリケーションをデプロイする場合は、レガシー アプリと IIS と互換性があり、大きなイメージを持っている Windows Server Core をターゲットにする必要があります。 .NET Core アプリケーションをデプロイする場合は、クラウドに最適化され、Kestrel を使用し、小型で起動が速い Windows Nano Server をターゲットにすることができます。 Debian や Alpine などをサポートしている Linux もターゲットにすることができます。 同様に、Kestrel を使用し、小型で起動が速くなります。](./media/image1.png)

**図 3-1.** .NET Framework のバージョンに応じて対象にすることができるオペレーティング システム

別の Linux ディストリビューションを使用したい場合や、Microsoft が提供していないバージョンのイメージが必要な場合は、独自の Docker イメージを作成することもできます。 たとえば、従来の .NET Framework と Windows Server Core 上で実行されている ASP.NET Core を使用してイメージを作成することができます (ただし、Docker の場合はあまり一般的ではないシナリオです)。

Dockerfile ファイルにイメージ名を追加すると、次の例のように、使用するタグに応じてオペレーティング システムとバージョンを選択できます。

| イメージ | コメント |
|-------|----------|
| mcr.microsoft.com/dotnet/core/runtime:2.2 | .NET Core 2.2 マルチアーキテクチャ:Docker ホストに応じて、Linux と Windows Nano Server をサポートします。 |
| mcr.microsoft.com/dotnet/core/aspnet:2.2 | ASP.NET Core 2.2 マルチアーキテクチャ:Docker ホストに応じて、Linux と Windows Nano Server をサポートします。 <br/> aspnetcore イメージでは、ASP.NET Core 用に 少しの最適化が行われています。 |
| mcr.microsoft.com/dotnet/core/aspnet:2.2-alpine | Linux Alpine ディストリビューションでの .NET Core 2.2 ランタイムのみ |
| mcr.microsoft.com/dotnet/core/aspnet:2.2-nanoserver-1803 | Windows Nano Server (Windows Server バージョン 1803) では .NET Core 2.2 ランタイムのみ |

> [!div class="step-by-step"]
> [前へ](container-framework-choice-factors.md)
> [次へ](official-net-docker-images.md)
