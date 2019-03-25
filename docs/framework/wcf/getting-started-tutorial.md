---
title: 'チュートリアル: Windows Communication Foundation アプリケーションを概要します。'
description: これらのチュートリアルでは、WCF アプリケーションを作成するための概要を提供します。
ms.date: 01/25/2019
helpviewer_keywords:
- WCF [WCF], get started
- Windows Communication Foundation [WCF], get started
- get started [WCF]
ms.assetid: df939177-73cb-4440-bd95-092a421516a1
ms.openlocfilehash: 66211cfcf2b742e43eccbefb2bc7c4bd1147b05b
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/25/2019
ms.locfileid: "58408861"
---
# <a name="tutorial-get-started-with-windows-communication-foundation-applications"></a>チュートリアル: Windows Communication Foundation アプリケーションを概要します。
次の一連のチュートリアルに、Windows Communication Foundation (WCF) プログラミングの経験を紹介します。 順序でこれらのチュートリアルに従って作業では、WCF アプリケーションの作成に必要な手順の概要を理解するを指定します。 完了したら、実行中の WCF サービスと WCF クライアント サービスを呼び出す必要があります。 

このチュートリアルでは、開発環境として Visual Studio を使用している前提としています。 他の開発環境を使用している場合は、Visual Studio 固有の手順を無視します。 

サンプル WCF アプリケーションをダウンロードして実行できる、次を参照してください。 [Windows Communication Foundation サンプル](samples/index.md)します。 サンプルの概要については、次を参照してください。 [Getting started サンプル](samples/getting-started-sample.md)します。

サービスとクライアントの作成の詳細の詳細については、次を参照してください。[基本的な WCF プログラミング](basic-wcf-programming.md)します。

## <a name="wcf-tutorials"></a>WCF のチュートリアル

最初の 3 つのチュートリアルでは、WCF サービス コントラクトを定義する方法、その実装方法、およびそれをホストする方法について説明します。 作成したサービスは、コンソール アプリケーション内で自己ホスト型です。 Microsoft インターネット インフォメーション サービス (IIS) の下のサービスをホストすることもできます。 詳細については、「[方法 :IIS で WCF サービスをホスト](feature-details/how-to-host-a-wcf-service-in-iis.md)します。 コードを使用して、チュートリアルでは、サービスを構成することもできます[構成ファイル内でサービスを構成する](configuring-services-using-configuration-files.md)します。 

- [チュートリアル: サービス コントラクトを定義します。](how-to-define-a-wcf-service-contract.md)

    WCF コントラクトを作成するには、ユーザー定義のインターフェイスを使用します。 このコントラクトは、サービスが公開する機能を定義します。

- [チュートリアル: サービス コントラクトを実装します。](how-to-implement-a-wcf-contract.md)

    コントラクトを定義した後は、サービス クラスを使用して実装する必要があります。

- [チュートリアル: ホストし、基本的なサービスの実行](how-to-host-and-run-a-basic-wcf-service.md)

    サービスのエンドポイントを構成し、コンソール アプリケーションでサービスをホストします。 アクティブになるサービスの場合は、構成し、ランタイム環境内でホストする必要があります。 この実行時環境では、サービスを作成し、そのコンテキストと有効期間を制御します。

次の 2 つのチュートリアルでは、作成、構成する方法を説明して、使用して、サービス操作を呼び出すクライアント アプリケーションを公開します。 サービスは、クライアント アプリケーションがサービスと通信するために必要な情報を定義したメタデータを公開します。 Visual Studio では、このメタデータにアクセスするプロセスを自動化し、サービスのクライアント アプリケーションの構築に使用します。 Visual Studio を使用しないようにする場合は、使用、 [ServiceModel メタデータ ユーティリティ ツール (*Svcutil.exe*)](servicemodel-metadata-utility-tool-svcutil-exe.md)代わりにします。

- [チュートリアル: クライアントを作成します。](how-to-create-a-wcf-client.md)

    WCF サービスから、WCF クライアント プロキシを作成するためのメタデータを取得します。 サービス参照を追加する Visual Studio を使用してメタデータを取得するか、ServiceModel メタデータ ユーティリティ ツールを使用することができます。 クライアントがサービスへのアクセスに使用するエンドポイントを指定します。

- [チュートリアル: クライアントを使用します。](how-to-use-a-wcf-client.md)

    WCF クライアント プロキシを使用して、サービス操作を呼び出します。

## <a name="reference"></a>参照

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>

## <a name="see-also"></a>関連項目

- [概念の概要](conceptual-overview.md)
- [ドキュメント ガイドします。](guide-to-the-documentation.md)
- [Windows Communication Foundation とは](whats-wcf.md)
- [WCF 機能の詳細](feature-details/index.md)
- [基本的なプログラミング ライフ サイクル](basic-programming-lifecycle.md)
- [クライアントを構築します。](building-clients.md)
- [基本的な WCF プログラミング](basic-wcf-programming.md)
- [方法: 双方向コントラクトを作成します。](feature-details/how-to-create-a-duplex-contract.md)
- [方法: Access services と双方向コントラクト](feature-details/how-to-access-services-with-a-duplex-contract.md)
- [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [方法: Svcutil.exe を使用してメタデータ ドキュメントをダウンロードするには](feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)
- [方法: 構成ファイルを使用して、サービスのメタデータを公開します。](feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [バインドを使用してサービスとクライアントを構成するには](using-bindings-to-configure-services-and-clients.md)
- [入門サンプル](samples/getting-started-sample.md)
- [Windows Communication Foundation サンプル](samples/index.md)
- [自己ホスト](samples/self-host.md)


