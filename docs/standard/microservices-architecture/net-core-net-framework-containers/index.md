---
title: Docker コンテナー用 .NET Core と .NET Framework の選択
description: '.NET マイクロサービス: コンテナー化された .NET アプリケーションのアーキテクチャ | Docker コンテナー用 .NET Core と .NET Framework の選択'
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/11/2018
ms.openlocfilehash: e71739b06275d4ee786d246004930d7b66fbc72b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019608"
---
# <a name="choosing-between-net-core-and-net-framework-for-docker-containers"></a>Docker コンテナー用 .NET Core と .NET Framework の選択

.NET を使用してサーバー側のコンテナー化された Docker アプリケーションをビルドする場合に選択できるサポート対象のフレームワークには、[.NET Framework と .NET Core](https://www.microsoft.com/net/download) の 2 つがあります。 それらは多数の .NET プラットフォームのコンポーネントを共有しているため、両者でコードを共有できます。 ただし、それらには基本的な違いがあり、どちらのフレームワークを使用するかは実行内容によって決まります。 このセクションでは、それぞれのフレームワークを選択する場合のガイダンスを提供します。

>[!div class="step-by-step"]
>[前へ](../container-docker-introduction/docker-containers-images-registries.md)
>[次へ](general-guidance.md)