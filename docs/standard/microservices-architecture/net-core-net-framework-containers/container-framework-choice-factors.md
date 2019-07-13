---
title: 意思決定テーブル。 Docker に使用する .NET Frameworks
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | 意思決定テーブル、Docker に使用する .NET Frameworks'
ms.date: 09/11/2018
ms.openlocfilehash: 96b2750e52d64b06444b7f87dea624879f37d3d7
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639178"
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a>意思決定テーブル: Docker に使用する .NET Frameworks

次の意思決定テーブルは、.NET Framework と .NET Core のどちらを使用するかをまとめたものです。 Linux コンテナーには、Linux ベースの Docker ホスト (VM またはサーバー) が必要であり、Windows コンテナーには、Windows Server ベースの Docker ホスト (VM またはサーバー) が必要であることを覚えておいてください。

> [!IMPORTANT]
> 開発用のコンピューターは、Linux または Windows の Docker ホストを 1 つ実行します。 1 つのソリューションで同時に実行してテストしたい関連するマイクロサービスは、同じコンテナー プラットフォームで実行する必要があります。

<table>
<thead>
<tr class="header">
<th><strong>アーキテクチャ/アプリの種類</strong></th>
<th><strong>Linux コンテナー</strong></th>
<th><strong>Windows コンテナー</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>コンテナー上のマイクロサービス</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>モノリシック アプリ</td>
<td>.NET Core</td>
<td><p>.NET Framework</p>
<p>.NET Core</p></td>
</tr>
<tr class="odd">
<td>クラス最高のパフォーマンスとスケーラビリティ</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>Windows Server レガシー アプリ ("ブラウンフィールド") のコンテナーへの移行</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="odd">
<td>コンテナー ベースの新しい開発 ("グリーンフィールド")</td>
<td>.NET Core</td>
<td>.NET Core</td>
</tr>
<tr class="even">
<td>ASP.NET Core</td>
<td>.NET Core</td>
<td><p>.NET Core (推奨)</p>
<p>.NET Framework</p></td>
</tr>
<tr class="odd">
<td>ASP.NET 4 (MVC 5、Web API 2、Web Forms)</td>
<td>--</td>
<td>.NET Framework</td>
</tr>
<tr class="even">
<td>SignalR サービス</td>
<td>.NET Core 2.1 以降のバージョン</td>
<td><p>.NET Framework</p>
<p>.NET Core 2.1 以降のバージョン</p></td>
</tr>
<tr class="odd">
<td>WCF、WF などのレガシ フレームワーク</td>
<td>.NET Core の WCF (WCF クライアント ライブラリのみ)</td>
<td><p>.NET Framework</p>
<p>.NET Core の WCF (WCF クライアント ライブラリのみ)</p></td>
</tr>
<tr class="even">
<td>Azure サービスの使用</td>
<td><p>.NET Core</p>
<p>(最終的に、すべての Azure サービスは .NET Core 用クライアント SDK を提供する予定です)</p></td>
<td><p>.NET Framework</p>
<p>.NET Core</p>
<p>(最終的に、すべての Azure サービスは .NET Core 用クライアント SDK を提供する予定です)</p></td>
</tr>
</tbody>
</table>

>[!div class="step-by-step"]
>[前へ](net-framework-container-scenarios.md)
>[次へ](net-container-os-targets.md)
