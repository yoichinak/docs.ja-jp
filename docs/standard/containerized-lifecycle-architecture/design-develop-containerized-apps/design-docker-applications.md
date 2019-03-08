---
title: Docker アプリケーションを設計します。
description: トピックであるためです、マイクロ サービス アーキテクチャに詳しいガイドへの参照を検索ここでは、このガイドでない詳しく説明します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 858147883b3b4a5a5f487856028fdbfa84f6cca9
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675187"
---
# <a name="design-docker-applications"></a>Docker アプリケーションを設計します。

第 1 章には、コンテナーと Docker に関する基本的な概念が導入されました。 その情報は、開始に必要な情報の基本的なレベルです。 ただし、1 つのサービスまたはコンテナーではなく複数のサービスで構成され、複雑なエンタープライズ アプリケーションを指定できます。 これらの省略可能なユース ケースでは、オーケストレーションの概念デザイン、サービス指向アーキテクチャ (SOA) より高度なマイクロ サービスの概念とコンテナーに追加の手法を把握する必要があります。 このドキュメントのスコープはマイクロ サービスに限定されませんが、Docker アプリケーションのライフ サイクルそのため、ことはできませんを参照してくださいマイクロ サービス アーキテクチャの詳細もコンテナーと Docker を使用して、定期的な SOA、バック グラウンド タスクまたはジョブ、またはできますもためモノリシック アプリケーション展開のアプローチです。

**詳細については**エンタープライズ アプリケーションとマイクロ サービス アーキテクチャの詳細については、ガイドを読む[NET マイクロ サービス。コンテナー化された .NET アプリケーション アーキテクチャ](https://docs.microsoft.com/dotnet/standard/microservices-architecture)をからダウンロードすることもできます。<https://aka.ms/MicroservicesEbook>します。

ただし、DevOps とアプリケーションのライフ サイクルに入る前に、どのようにしようとしている設計を理解し、アプリケーションと、デザインの選択肢は何を構築を必要があります。

>[!div class="step-by-step"]
>[前へ](index.md)
>[次へ](common-container-design-principles.md)
