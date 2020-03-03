---
title: マネージド アプリケーションのホスト
ms.date: 03/30/2017
ms.assetid: af70132d-e9e1-4f32-b20f-f0014629758a
ms.openlocfilehash: 1895f6622f7c528979badd741f5994970bbd1a8c
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169801"
---
# <a name="hosting-in-a-managed-application"></a>マネージド アプリケーションのホスト
任意の .NET Framework アプリケーションでは、Windows Communication Foundation (WCF) サービスをホストすることができます。 自己ホスト型サービスは、展開を要するインフラストラクチャが最も少ないので、最も柔軟なホスト オプションです。 しかしも、最も堅牢なホスティング オプションのマネージ アプリケーションでは、高度なホストとインターネット インフォメーション サービス (IIS) や Windows サービスなどの WCF では、ホストの他のオプションの管理機能が提供されないためです。  
  
 自己ホスト型サービスを作成するには、メッセージをリッスンするサービスを開始する <xref:System.ServiceModel.ServiceHost>のインスタンスを作成して開きます。 詳細については、「[方法 :マネージ アプリケーションで WCF サービスをホスト](../../../../docs/framework/wcf/how-to-host-a-wcf-service-in-a-managed-application.md)します。  
  
 コントラクトを定義して、コントラクトを実装する、マネージ アプリケーションの内部でサービスをホストする方法の完全な例を参照してください、[チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)と[セルフホスト](../../../../docs/framework/wcf/samples/self-host.md)します。  
  
 以下に、このホスト オプションを使用する一般的なシナリオについて説明します。  
  
## <a name="console-applications"></a>コンソール アプリケーション  
 自己ホストできるようにするための一般的なシナリオは、コンソール アプリケーション内で実行されている WCF サービスです。 コンソール アプリケーション内部の WCF サービス ホストは、サービスの開発フェーズ中に一般的に便利です。 コンソール アプリケーションにより、アプリケーション内部で起こっている状況を見極めるための情報のデバッグやトレースが容易になり、新しい場所にアプリケーションをコピーして移動することも簡単に行うことができます。  
  
## <a name="rich-client-applications"></a>リッチ クライアント アプリケーション  
 自己ホストできるようにするその他の一般的なシナリオは、Windows Presentation Foundation (WPF) または Windows フォーム (WinForms) に基づくものなどのリッチ クライアント アプリケーションです。 このホスト オプションでは、外部と通信するために、WPF と WinForms アプリケーションなどのリッチ クライアント アプリケーションを簡単にします。 たとえば、WPF を使用して、ユーザー インターフェイスともその他のクライアントに接続して、情報を共有できるようにする WCF サービスをホストするピア ツー ピア コラボレーション クライアントです。  
  
## <a name="see-also"></a>関連項目

- [ホスティング サービス](../../../../docs/framework/wcf/hosting-services.md)
- [チュートリアル入門](../../../../docs/framework/wcf/getting-started-tutorial.md)
