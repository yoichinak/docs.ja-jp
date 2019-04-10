---
title: Windows サービス アプリケーションのホスト
ms.date: 03/30/2017
ms.assetid: f4199998-27f3-4dd9-aee4-0a4addfa9f24
ms.openlocfilehash: 8e50c39955f9ab72dfa1d52cbc37ab90f1ab0a8a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59335369"
---
# <a name="hosting-in-a-windows-service-application"></a>Windows サービス アプリケーションのホスト
Windows サービス (従来 Windows NT サービスと呼ばれていたもの) が提供するプロセス モデルが特に適しているのは、長い期間にわたって動作し続ける必要があり、どのような形式でもユーザー インターフェイスを表示することのないアプリケーションです。 Windows サービス アプリケーションのプロセスの有効期間を管理するのは、サービス コントロール マネージャー (SCM) です。SCM を使用して、Windows サービス アプリケーションを起動、停止、および一時停止できます。 「常時オン」のアプリケーションの適切なホスティング環境のため、コンピューターの起動時に自動的に開始する、Windows サービスのプロセスを構成することができます。 Windows サービス アプリケーションの詳細については、次を参照してください。 [Windows サービス アプリケーション](https://go.microsoft.com/fwlink/?LinkId=89450)します。  
  
 実行時間の長い Windows Communication Foundation (WCF) サービスをホストしているアプリケーションは、Windows サービスとの特性の多くを共有します。 具体的には、WCF サービスは、実行時間の長いサーバー実行可能ファイルは、ユーザーと直接対話しないのすべてのユーザー インターフェイスを実装しないでください。 そのため、Windows サービス アプリケーションの内部で WCF サービスをホストしているは、実行時間の長い、堅牢な WCF アプリケーションを構築するための 1 つのオプションです。  
  
 多くの場合、WCF の開発者では Windows サービス アプリケーションの内部で、またはインターネット インフォメーション サービス (IIS) または Windows プロセス アクティブ化サービス (WAS) のホスティング環境の内部では、WCF アプリケーションをホストするかどうかを決める必要があります。 次のような場合、Windows サービス上でホストする方法を使用できないか検討してください。  
  
-   アプリケーションを明示的にアクティブ化する必要がある場合。 たとえば、サーバー起動時に自動的にアプリケーションも起動しなければならず、最初に届いたメッセージに応答して動的に起動するのでは困るような場合です。  
  
-   アプリケーションをホストするプロセスが、起動されたらそのまま動作し続けなければならない場合。 一度起動した Windows サービスのプロセスは、サーバー管理者がサービス コントロール マネージャーで明示的にシャットダウンしない限り、そのまま動作し続けます。 IIS や WAS 上でホストするアプリケーションは、動的に起動および停止して、システム リソースを効率よく使うことができます。 しかし、ホストするプロセスの有効期間にわたって明示的に制御しなければならない場合、IIS や WAS ではなく Windows サービスを使う必要があります。  
  
-   WCF サービスは、Windows Server 2003 で実行され、HTTP 以外のトランスポートを使用する必要があります。 Windows Server 2003 では、[!INCLUDE[iis601](../../../../includes/iis601-md.md)] ホスティング環境は HTTP 通信しかできないようになっています。 Windows サービス アプリケーションは、この制限が適用されないし、net.tcp、net.pipe、net.msmq など、トランスポート WCF のサポートを使用できます。  
  
### <a name="to-host-wcf-inside-of-a-windows-service-application"></a>Windows サービス アプリケーションの内部で WCF をホストするには  
  
1. Windows サービス アプリケーションを作成します。 Windows サービス アプリケーションは、<xref:System.ServiceProcess> 名前空間のクラスを使用して、マネージ コードとして記述することができます。 このアプリケーションには、<xref:System.ServiceProcess.ServiceBase> から派生したクラスを 1 つ含める必要があります。  
  
2. WCF サービスの有効期間を Windows サービス アプリケーションの有効期間にリンクします。 通常、ホスティング サービス開始時にアクティブになる、ホスティング、サービスが停止すると、WCF サービスには、エラーが発生したときに、ホスト プロセスをシャット ダウン場合に、メッセージのリッスンを停止する Windows サービス アプリケーションでホストされる WCF サービスをします。 これは次のようにして実装します。  
  
    -   <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> をオーバーライドして、<xref:System.ServiceModel.ServiceHost> のインスタンスを必要な個数開くようにします。 1 つの Windows サービス アプリケーションは、開始時刻と停止をグループとして複数の WCF サービスをホストできます。  
  
    -   オーバーライド<xref:System.ServiceProcess.ServiceBase.OnStop%2A>を呼び出す<xref:System.ServiceModel.Channels.CommunicationObject.Closed>上、<xref:System.ServiceModel.ServiceHost>中に開始された実行中の WCF サービス<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>します。  
  
    -   <xref:System.ServiceModel.Channels.CommunicationObject.Faulted> の <xref:System.ServiceModel.ServiceHost> イベントを定期受信し、エラー時には、<xref:System.ServiceProcess.ServiceController> クラスを使用して Windows サービス アプリケーションをシャットダウンします。  
  
     WCF サービスをホストする Windows サービス アプリケーションが展開され、WCF のない Windows サービス アプリケーションを使用して、としては、同じ方法で管理されています。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceProcess>
- [チュートリアル: コンポーネント デザイナーで Windows サービス アプリケーションの作成](https://go.microsoft.com/fwlink/?LinkId=94875)
- [方法: マネージド Windows サービスで WCF サービスをホストする](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-a-managed-windows-service.md)
- [Windows サービス ホスト](../../../../docs/framework/wcf/samples/windows-service-host.md)
- [サービス アプリケーションのプログラミング アーキテクチャ](https://go.microsoft.com/fwlink/?LinkId=94876)
- [AppFabric のホスティング機能](https://go.microsoft.com/fwlink/?LinkId=201276)
