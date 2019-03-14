---
title: .NET コンテナーで対象とする OS
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | .NET コンテナーで対象とする OS'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 9e1d07e48d88376efb5fbdbdadc999c8dcd5082d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374909"
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

<table>
<thead>
<tr class="header">
<th>イメージ</th>
<th>コメント</th>
</tr>
</thead>
<tbody>
<tr>
<td>microsoft/dotnet:2.2-runtime</td>
<td>.NET Core 2.2 マルチアーキテクチャ:Docker ホストに応じて、Linux と Windows Nano Server をサポートします。</td>
</tr>
<tr class="odd">
<td>microsoft/dotnet:2.2-aspnetcore-runtime</td>
<td><p>ASP.NET Core 2.2 マルチアーキテクチャ:Docker ホストに応じて、Linux と Windows Nano Server をサポートします。</p>
<p>aspnetcore イメージでは、ASP.NET Core 用に 少しの最適化が行われています。</p></td>
</tr>
<tr class="even">
<td>microsoft/dotnet:2.2-aspnetcore-runtime-alpine</td>
<td>Linux Alpine ディストリビューションでの .NET Core 2.2 ランタイムのみ</td>
</tr>
<tr class="odd">
<td>microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1803</td>
<td>Windows Nano Server (Windows Server バージョン 1803) では .NET Core 2.2 ランタイムのみ</td>
</tr>
</tbody>
</table>

> [!div class="step-by-step"]
> [前へ](container-framework-choice-factors.md)
> [次へ](official-net-docker-images.md)