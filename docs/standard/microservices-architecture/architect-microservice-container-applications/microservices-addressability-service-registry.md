---
title: マイクロサービスのアドレス指定能力およびサービス レジストリ
description: マイクロサービス アーキテクチャ内のコンテナー イメージ レジストリの役割を理解します。
ms.date: 09/20/2018
ms.openlocfilehash: 5b601f19b60a8e989977e7135138add7644bd7b6
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639971"
---
# <a name="microservices-addressability-and-the-service-registry"></a>マイクロサービスのアドレス指定能力およびサービス レジストリ

各マイクロサービスには、その場所を解決するために使用する一意の名前 (URL) が付けられています。 ご利用のマイクロサービスは、その実行場所にかかわらず、アドレス指定可能である必要があります。 特定のマイクロサービスをどのコンピューターで実行するかについて考える必要がある場合、事態はすぐに悪化する可能性があります。 DNS が URL を特定のコンピューターに解決するのと同様に、マイクロサービスの現在の場所が探索できるようにマイクロサービスには一意の名前が割り当てられている必要があります。 マイクロサービスには、実行されているインフラストラクチャからマイクロサービスを独立させるためのアドレス指定可能な名前が必要です。 このことは、[サービス レジストリ](https://microservices.io/patterns/service-registry.html)が必要であるために、サービスの展開方法とサービスの検出方法との間には相互作用があることを意味しています。 同様に、コンピューターで障害が発生した場合、レジストリ サービスは、サービスが現在実行されている場所を示すことができなければなりません。

[サービス レジストリ パターン](https://microservices.io/patterns/service-registry.html)は、サービス検出の重要な部分です。 レジストリは、サービス インスタンスのネットワークの場所を含むデータベースです。 サービス レジストリは、可用性が高く、最新の状態である必要があります。 クライアントは、サービス レジストリから取得したネットワークの場所をキャッシュすることが可能です。 ただし、その情報は最終的には期限切れになり、クライアントはサービス インスタンスを検出できなくなります。 したがって、サービス レジストリは、レプリケーション プロトコルを使用して整合性を維持するサーバーのクラスターで構成されます。

一部のマイクロサービスの展開環境 (クラスターと呼ばれ、後のセクションで説明します) には、サービス検出が組み込まれています。 たとえば、Kubernetes (AKS) 環境での Azure Container Service では、サービス インスタンスの登録と登録解除を処理できます。 また、これはサーバー側の検出ルーターの役割を果たす各クラスター ホスト上でプロキシも実行します。 別の例として Azure Service Fabric が挙げられます。これもまた、すぐに使用できる Naming Service を介してサービス レジストリを提供します。

サービス レジストリと API ゲートウェイ パターンとの間には特定のオーバーラップがあり、この問題の解決にも役立っています。 たとえば、[Service Fabric のリバース プロキシ](https://docs.microsoft.com/azure/service-fabric/service-fabric-reverseproxy)は、Service Fabric の Naming Service に基づく API ゲートウェイの実装の種類であり、内部サービスへのアドレス解決を解決するのに役に立ちます。

## <a name="additional-resources"></a>その他の技術情報

- **Chris Richardson。パターン: サービス レジストリ** \
  <https://microservices.io/patterns/service-registry.html>

- **Auth0。サービス レジストリ** \
  <https://auth0.com/blog/an-introduction-to-microservices-part-3-the-service-registry/>

- **Gabriel Schenker。サービス探索** \
  <https://lostechies.com/gabrielschenker/2016/01/27/service-discovery/>

>[!div class="step-by-step"]
>[前へ](maintain-microservice-apis.md)
>[次へ](microservice-based-composite-ui-shape-layout.md)
