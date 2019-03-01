---
title: Tutorial1 を作業の開始
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], getting started
- Windows Communication Foundation [WCF], getting started
- getting started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: b7ba25795dd69e5bd978c77928f9b9797f4d4e19
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200885"
---
# <a name="getting-started-tutorial"></a>チュートリアル入門
このセクションのトピックはクイック露出を Windows Communication Foundation (WCF) プログラミングの経験を提供するためのものです。 これらは、このトピックに記載されているリストの順番どおりに完了するように設計されています。 このチュートリアルに従って作業では、WCF サービスとクライアント アプリケーションの作成に必要な手順の概要を理解するできます。 サービスは 1 つ以上のエンドポイントを公開し、それぞれのエンドポイントは 1 つ以上のサービス操作を公開します。 *エンドポイント*サービスのサービスの場所、アドレス、クライアントが、サービスと機能を定義するコントラクトと通信する必要がある方法を説明する情報を格納するバインディングを指定します。サービスのクライアントに提供します。

 このチュートリアルの一連のトピックを終了すると、サービスを実行し、クライアントからそのサービスを呼び出すことができるようになります。 最初の 3 つのトピックでは、サービス コントラクトを定義する方法、サービス コントラクトを実装する方法、およびサービスをホストする方法について説明します。 作成したサービスは、コンソール アプリケーション内で自己ホストされます。 また、サービスは、インターネット インフォメーション サービス (IIS) でホストすることもできます。 この方法の詳細については、「[方法 : IIS で WCF サービスをホスト](../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-iis.md)します。 サービスはコードで構成されますが、構成ファイル内で構成することもできます。 構成ファイルの使用の詳細については、次を参照してください。[構成ファイルを使用してサービスを構成する](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)します。

 次の 3 つのトピックでは、クライアント プロキシを作成する方法、クライアント アプリケーションを構成する方法、およびサービスが公開するサービス操作をクライアント プロキシを使って呼び出す方法について説明します。 サービスは、クライアント アプリケーションがサービスと通信するために必要な情報を定義したメタデータを公開します。 Visual Studio 2012 では、このメタデータにアクセスするプロセスを自動化し、構築して、サービスのクライアント アプリケーションを構成することを使用します。 Visual Studio 2012 を使用していない場合は使用できます、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)を構築およびサービスのクライアント アプリケーションを構成します。

このセクションのトピックでは、開発環境として Visual Studio を使用するいると仮定します。 他の開発環境を使用している場合は、Visual Studio 固有の手順を無視します。

ハード_ディスクにダウンロードできるようにしてトピックを参照して、実行するサンプル アプリケーションの[Windows Communication Foundation (WCF) サンプル](./samples/index.md)します。 このトピックでは、具体的を参照、 [Getting Started](../../../docs/framework/wcf/samples/getting-started-sample.md)します。

サービスとクライアントの作成の詳細の詳細については、次を参照してください。[基本的な WCF プログラミング](../../../docs/framework/wcf/basic-wcf-programming.md)します。

## <a name="in-this-section"></a>このセクションの内容
 [方法: サービス コントラクトを定義します。](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)

 ユーザー定義のインターフェイスを使用して WCF コントラクトを作成する方法について説明します。 コントラクトは、サービスが公開する機能を定義します。

 [方法: サービス コントラクトを実装します。](../../../docs/framework/wcf/how-to-implement-a-wcf-contract.md)

 サービス コントラクトを実装する方法について説明します。 コントラクトを定義するは、サービス クラスを使用して実装する必要があります。

 [方法: ホストし、基本的なサービスの実行](../../../docs/framework/wcf/how-to-host-and-run-a-basic-wcf-service.md)

 サービスのエンドポイントをコードで構成する方法と、コンソール アプリケーションでサービスをホストする方法について説明します。 サービスをアクティブにするには、サービスをランタイム環境内で構成してホストする必要があります。 この環境によってサービスが作成され、サービスのコンテキストと有効期間が制御されます。

 [方法: クライアントを作成します。](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)

 WCF サービスからの WCF クライアント プロキシを作成するために使用するメタデータを取得する方法について説明します。 このプロセスは、Visual Studio 内でサービス参照の追加機能を使用します。

 [方法: クライアントを構成します。](../../../docs/framework/wcf/how-to-configure-a-basic-wcf-client.md)

 WCF クライアントの構成方法について説明します。クライアントを構成するには、クライアントがサービスへのアクセスに使用するエンドポイントを指定する必要があります。

 [方法: クライアントを使用します。](../../../docs/framework/wcf/how-to-use-a-wcf-client.md)

 サービス操作を呼び出す、WCF クライアント プロキシを使用する方法について説明します。

## <a name="reference"></a>参照

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="related-sections"></a>関連項目

- [Windows Communication Foundation (WCF) のサンプル](./samples/index.md)
- [基本的なプログラミング ライフサイクル](../../../docs/framework/wcf/basic-programming-lifecycle.md)

## <a name="see-also"></a>関連項目

- [概念](../../../docs/framework/wcf/conceptual-overview.md)
- [ドキュメントのガイド](../../../docs/framework/wcf/guide-to-the-documentation.md)
- [Windows Communication Foundation とは](../../../docs/framework/wcf/whats-wcf.md)
- [WCF 機能の詳細](../../../docs/framework/wcf/feature-details/index.md)
