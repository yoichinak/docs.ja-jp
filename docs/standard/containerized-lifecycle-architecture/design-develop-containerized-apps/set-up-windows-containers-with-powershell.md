---
title: DockerFile で Windows PowerShell コマンドを使用して Windows コンテナー (Docker 標準ベース) を設定するには
description: Windows コンテナーで Docker を使用する場合は、PowerShell を使用する方法について説明します
ms.date: 02/15/2019
ms.openlocfilehash: e91d278aef1365a111e8d67ff04092dfc6a44185
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641582"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a>DockerFile で Windows PowerShell コマンドを使用して Windows コンテナー (Docker 標準ベース) を設定するには

[Windows コンテナー](/virtualization/windowscontainers/about/index)、Docker イメージを既存の Windows アプリケーションを変換し、Docker エコシステムの残りの部分と同じツールで展開したりできます。

Windows コンテナーを使用するには、だけです、DockerFile で Windows PowerShell コマンドを記述する次の例に示すよう。

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

この場合、IIS だけでなく Windows Server Core 基本イメージをインストールする Windows PowerShell を使用しています。

同様の方法で使用することもできます Windows PowerShell コマンド、従来の ASP.NET などの追加コンポーネントを設定する 4.x および .NET 4.6、またはその他の Windows ソフトウェア、次のようにします。

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
>[前へ](visual-studio-tools-for-docker.md)
>[次へ](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)
