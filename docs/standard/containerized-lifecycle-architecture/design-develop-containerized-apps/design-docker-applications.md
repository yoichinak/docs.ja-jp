---
title: Docker アプリケーションの設計
description: トピックであるためです、マイクロ サービス アーキテクチャに詳しいガイドへの参照を検索ここでは、このガイドでない詳しく説明します。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 1d49f7509c0a12edfe375486429147e8fd240b2d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61799347"
---
# <a name="design-docker-applications"></a>Docker アプリケーションの設計

第 1 章には、コンテナーと Docker に関する基本的な概念が導入されました。 その情報は、開始に必要な情報の基本的なレベルです。 ただし、1 つのサービスまたはコンテナーではなく複数のサービスで構成され、複雑なエンタープライズ アプリケーションを指定できます。 これらの省略可能なユース ケースでは、オーケストレーションの概念デザイン、サービス指向アーキテクチャ (SOA) より高度なマイクロ サービスの概念とコンテナーに追加の手法を把握する必要があります。 このドキュメントのスコープはマイクロ サービスに限定されませんが、Docker アプリケーションのライフ サイクルそのため、ことはできませんを参照してくださいマイクロ サービス アーキテクチャの詳細もコンテナーと Docker を使用して、定期的な SOA、バック グラウンド タスクまたはジョブ、またはできますもためモノリシック アプリケーション展開のアプローチです。

**詳細については**エンタープライズ アプリケーションとマイクロ サービス アーキテクチャの詳細については、ガイドを読む[NET マイクロ サービス。コンテナー化された .NET アプリケーション アーキテクチャ](../../microservices-architecture/index.md)をからダウンロードすることもできます。<https://aka.ms/MicroservicesEbook>します。

ただし、DevOps とアプリケーションのライフ サイクルに入る前に、どのようにしようとしている設計を理解し、アプリケーションと、デザインの選択肢は何を構築を必要があります。

>[!div class="step-by-step"]
>[前へ](index.md)
>[次へ](common-container-design-principles.md)