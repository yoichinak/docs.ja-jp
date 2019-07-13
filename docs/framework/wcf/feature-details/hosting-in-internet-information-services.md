---
title: インターネット インフォメーション サービスでのホスティング
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 3940d8436ba5441d4e884879213a7a782214cb05
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486748"
---
# <a name="hosting-in-internet-information-services"></a>インターネット インフォメーション サービスでのホスティング
Windows Communication Foundation (WCF) サービスをホストするための 1 つは、インターネット インフォメーション サービス (IIS) アプリケーション内でです。 このホスティング モデルは、ASP.NET と ASP.NET Web サービス (ASMX) Web サービスによって使用されるモデルに似ています。  
  
## <a name="versions-of-iis"></a>IIS バージョン  
 WCF は、次のオペレーティング システムで次のバージョンの IIS でホストできます。  
  
- [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] 上で IIS 5.1 を使用。 この環境は、後で [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] などのサーバー オペレーティング システムに展開される、IIS ホスト型アプリケーションの設計と開発に役立ちます。  
  
- 上の IIS 6.0[!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]します。 IIS 6.0 では、強化されたスケーラビリティ、信頼性、およびアプリケーションの分離を提供する高度なプロセス モデルを提供します。 この環境では、HTTP 通信のみを使用する WCF サービスの運用環境のデプロイに適しています。  
  
- [!INCLUDE[wv](../../../../includes/wv-md.md)] および [!INCLUDE[lserver](../../../../includes/lserver-md.md)] 上で IIS 7.0 を使用。 IIS 7.0 では、IIS 6.0 と同じ高度なプロセス モデルを提供しますが、HTTP 以外のプロトコル経由でアクティベーションとネットワーク通信を許可する Windows プロセス アクティブ化サービス (WAS) を使用します。 この環境では、WCF (HTTP、net.tcp、net.pipe、net.msmq など) でサポートされている任意のネットワーク プロトコル経由で通信する WCF サービスの開発に適しています。 WAS の詳細については、次を参照してください。 [Windows プロセス アクティブ化サービスでのホスティング](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md)します。  
  
- [Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496) NET4 WCF および WF サービス用に環境をホストしている豊富なアプリケーションを提供するには、IIS 7.0 と Windows プロセス アクティブ化サービス (WAS) で動作します。 この利点には、プロセス ライフサイクル管理、プロセス リサイクル、共有ホスティング、迅速な障害保護、プロセスの孤立化、オンデマンド アクティブ化、状態監視などがあります。 詳細については、次を参照してください。 [AppFabric のホスティング機能](https://go.microsoft.com/fwlink/?LinkId=196494)と[AppFabric ホスティングの概念](https://go.microsoft.com/fwlink/?LinkId=196495)します。  
  
## <a name="benefits-of-iis-hosting"></a>IIS ホスティングの利点  
 IIS で WCF サービスをホストすると、いくつかの利点があります。  
  
- IIS でホストされる WCF サービスが展開されているし、IIS のアプリケーション、ASP.NET アプリケーションや ASMX などの他の任意の型と同様に管理します。  
  
- IIS はプロセスのアクティブ化、状態管理、リサイクル機能を提供し、ホストされるアプリケーションの信頼性を向上します。  
  
- ASP.NET のように ASP.NET でホストされる WCF サービスを利用できます ASP.NET の共有ホスティング モデルの改良されたサーバー密度とスケーラビリティのための共通のワーカー プロセスで複数のアプリケーションが存在します。  
  
- IIS でホストされる WCF サービスは、ASP.NET 2.0 は、ホステッド サービスの開発と展開を簡略化として同じの動的なコンパイル モデルを使用します。  
  
 IIS で WCF サービスをホストする場合は、IIS 5.1 および IIS 6.0 の HTTP 通信のみに限定されることに注意してください。 ホスト環境の選択の詳細については、次を参照してください。[ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)します。  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>IIS にホストされた WCF サービスの展開  
 IIS でホストされる WCF サービスの展開の開発とは、次のタスクで構成されます。  
  
- ある IIS、ASP.NET、WCF、および WCF HTTP アクティブ化コンポーネントが正しくインストールされ、登録されていることを確認します。  
  
- 新しい IIS アプリケーションを作成または既存の ASP.NET アプリケーションを再利用します。  
  
- WCF サービスの .svc ファイルを作成します。  
  
- IIS アプリケーションにサービス実装を展開します。  
  
- WCF サービスを構成します。  
  
 これらの各タスクの詳細については、次を参照してください。[インターネット WCF サービスの展開](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)します。  
  
## <a name="wcf-services-and-aspnet"></a>WCF サービスと ASP.NET  
 WCF サービスは、いずれかのサイド ASP.NET を使用した、またはサービスが、ASP.NET Web アプリケーション プラットフォームで提供される機能の活用を実行できる ASP.NET 互換モードでホストされています。 これらの機能の詳細については、次を参照してください。 [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)します。  
  
## <a name="see-also"></a>関連項目

- [ServiceHostFactory を使用したホストの拡張](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)
- [インターネット インフォメーション サービスでホストされる WCF サービスの配置](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)
- [WCF サービスと ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [インターネット インフォメーション サービス ホスティングのベスト プラクティス](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [Windows Communication Foundation での Internet Information Services 7.0 の構成](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)
- [AppFabric のホスティング機能](https://go.microsoft.com/fwlink/?LinkId=201276)
