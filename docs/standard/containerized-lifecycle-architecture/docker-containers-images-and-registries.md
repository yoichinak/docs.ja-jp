---
title: Docker コンテナー、イメージ、レジストリ
description: レジストリにアプリケーションを展開する Docker の方法で全体的な再生される重要な役割について説明します。
ms.date: 02/15/2019
ms.openlocfilehash: 7becadc3de16d96f8d6f167cf49c6cdd3bcc0d32
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641324"
---
# <a name="docker-containers-images-and-registries"></a>Docker コンテナー、イメージ、レジストリ

Docker を使用する場合、およびその依存関係コンテナー イメージにアプリまたはサービス、およびパッケージを作成します。 イメージとは、アプリケーションまたはサービスと、その構成と依存関係の静的な表現です。

アプリケーションまたはサービスを実行するために、アプリケーションのイメージはインスタンス化され、コンテナーが作成されます。このコンテナーが Docker ホスト上で実行されます。 コンテナーは、最初に開発環境または PC でテストされます。

イメージのライブラリとして機能する、レジストリにイメージを格納します。 運用環境のオーケストレーターに展開する場合は、レジストリを作成する必要があります。 Docker は [Docker Hub](https://hub.docker.com/) 経由で公開レジストリを保守します。他のベンダーは、[Azure Container Registry](https://azure.microsoft.com/services/container-registry/)を含むさまざまなイメージのコレクション用のレジストリを用意しています。 また、企業は自社の Docker イメージ用に非公開のレジストリをオンプレミスに持つことができます。

図 1-4 は、他のコンポーネントにイメージと Docker でレジストリを関連付ける方法を示しています。 また、ベンダーから提供される複数のレジストリも示しています。

![Docker で基本的な分類:レジストリは、イメージがプルされ、サービスまたは web アプリを実行するコンテナーを構築するために使用および保存は本棚など。 プライベート Docker レジストリ、オンプレミスとパブリック クラウドで。 Docker Hub はエンタープライズ級のソリューションである Docker Trusted Registry と共に Docker によって管理されるパブリック レジストリであり、Azure では Azure Container Registry を提供しています。 AWS や Google などにもコンテナー レジストリがあります。](./media/image4.png)

**図 1-4** Docker の用語と概念の分類

レジストリにイメージを配置する、フレームワーク レベルの依存関係のすべてを含む、静的で不変アプリケーション ビットを格納できます。 バージョンことができますと複数の環境でイメージを展開し、したがって一貫した展開ユニットを提供します。

オンプレミスまたはクラウドでホストされる非公開のイメージ レジストリは、次の場合に推奨されます。

- 機密保持のためにイメージを一般公開して共有することができない場合。

- イメージと選択した展開環境間のネットワーク待機時間を最小限に抑えたい場合。 たとえば、実稼働環境が Azure の場合は、可能性がありますする、イメージを格納する[Azure Container Registry](https://azure.microsoft.com/services/container-registry/)ネットワーク待ち時間が最小限に抑えるようにします。 同様に、実稼働環境がオンプレミスの場合は、同じローカル ネットワーク内でオンプレミスの Docker Trusted Registry を使用できるようにする方法があります。

>[!div class="step-by-step"]
>[前へ](docker-terminology.md)
>[次へ](road-to-modern-applications-based-on-containers.md)
