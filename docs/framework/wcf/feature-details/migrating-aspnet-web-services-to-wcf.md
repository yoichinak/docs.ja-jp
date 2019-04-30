---
title: ASP.NET Web サービスを WCF に移行する
ms.date: 03/30/2017
ms.assetid: 1adbb931-f0b1-47f3-9caf-169e4edc9907
ms.openlocfilehash: 703088cdaae69d90d71fb950912538ea0662229b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948097"
---
# <a name="migrating-aspnet-web-services-to-wcf"></a>ASP.NET Web サービスを WCF に移行する
ASP.NET には Web サービスを構築するための .NET Framework クラス ライブラリとツールが用意されています。また、インターネット インフォメーション サービス (IIS) 内でサービスをホストする機能も用意されています。 Windows Communication Foundation (WCF) は、.NET Framework クラス ライブラリ、ツール、および Web サービスで使用されるものも含め、任意のプロトコルを使用して通信するためにソフトウェア エンティティを有効にするためのホスティング機能を提供します。  ASP.NET Web サービスの WCF へ移行するには、新しい機能と WCF に固有の機能強化を活用するために、アプリケーションができます。  
  
 WCF では、ASP.NET Web サービスと比較したいくつかの重要な利点があります。 ASP.NET Web サービスのツールは、Web サービスを構築するためだけですが、WCF には、ソフトウェア エンティティが相互に通信を行う必要があるときに使用できるツールが用意されています。 これにより、さまざまなソフトウェア通信シナリオを実現するために開発者が知っておく必要があるテクノロジの数が少なくて済むため、ソフトウェア開発プロジェクトが完了するまでの時間だけでなく、ソフトウェア開発リソースのコストが削減されます。  
  
 WCF は、Web サービス開発プロジェクトの場合でも、ASP.NET Web サービスのサポートよりも多くの Web サービス プロトコルをサポートします。 これらの追加プロトコルにより、特に信頼できるセッションとトランザクションという点で、より洗練されたソリューションが実現されます。  
  
 WCF では、ASP.NET Web サービスのメッセージの転送を複数のプロトコルをサポートしています。 ASP.NET Web サービスでは、HTTP (ハイパーテキスト転送プロトコル) を使用したメッセージの送信しかサポートしていません。 WCF では、HTTP、だけでなく、伝送制御プロトコル (TCP)、名前付きパイプ、および Microsoft メッセージ キュー (MSMQ) を使用してメッセージの送信をサポートしています。 それと、WCF は追加のトランスポート プロトコルをサポートするために拡張できます。 そのため、WCF を使用して開発されたソフトウェアはさまざまな投資に対する潜在的な戻り値を増やすことが、その他のソフトウェアと連携するように適合できます。  
  
 WCF はくらい豊富な機能を展開するためを示し、ASP.NET Web サービス アプリケーションの管理を提供します。 WCF 構成エディターでの提供も ASP.NET には、構成システムに加えて、中継ぎ局、トレース ビューアー、メッセージ ログ、パフォーマンス カウンターを膨大な数の任意の数を受信者への送信者からのアクティビティ トレースとWindows Management Instrumentation のサポート。  
  
 を使用しているか、いくつかのオプションがある ASP.NET Web サービスの使用を検討している場合にサービス、ASP.NET Web の基準とした WCF のこれらの潜在的なメリットを考えてみます。  
  
- ASP.NET Web サービスを使用し、WCF によって提供される利点をしないに進みます。  
  
- 引き続き、将来いつか WCF を採用することを目的として、ASP.NET Web サービスを使用します。 このセクションのトピックでは、可能性と将来の WCF アプリケーションの新しい ASP.NET Web サービス アプリケーションを使用することを最大化する方法を説明します。 このセクションのトピックでは、新しい ASP.NET Web の WCF に移行しやすくためのサービスを構築する方法も説明します。 ただし、サービスのセキュリティ保護することが重要な信頼性やトランザクション保証が必要な場合、またはカスタムの場合は、管理機能が構築する必要があるし、WCF を採用することをお勧めします。 WCF は、まさにこのようなシナリオのために設計されています。  
  
- 既存の ASP.NET Web サービス アプリケーションを維持しながら、新しい開発のためには、WCF を採用します。 おそらくこれが最適な選択です。 それを使用する既存のアプリケーションの変更のコストを引き出しつつ、WCF の利点が得られます。 このシナリオで新しい WCF アプリケーションと共存できます既存の ASP.NET アプリケーション。 新しい WCF アプリケーションが既存の ASP.NET Web サービスを使用できなくなり、WCF の ASP.NET 互換モードにより、既存の ASP.NET アプリケーションに新しい処理機能をプログラムには、WCF を使用できます。  
  
- WCF を採用し、既存の ASP.NET Web サービス アプリケーションを WCF に移行します。 このオプションを WCF によって提供される機能と既存のアプリケーションを強化するために、または新しい内の既存の ASP.NET Web サービスの機能より強力な WCF アプリケーションを再現することができます。  
  
> [!NOTE]
>  WCF サービスがホストされている場合は注意する必要がありますが iis 5.x と ASP.NET をアンインストールします。 WCF サービスが IIS によってホストされている場合、ASP.NET がアンインストールされて、5.x では、サービスのコードを要求できます。 IIS を実行しているオペレーティング システム上の ASP.NET がアンインストール 5.x と WCF がアンインストールされ、.svc 拡張子の付いたファイルはテキスト ファイルと見なされる、ソース コードを含む、内容が、要求元に返されます。  
  
 このセクションは、これらのオプションの詳細について説明します、WCF を ASP.NET Web サービスを比較しますおよびでは、ASP.NET Web サービスのコードを WCF に移行する方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [Windows Communication Foundation の採用を予測します。将来の移行を簡略化](../../../../docs/framework/wcf/feature-details/anticipating-adopting-wcf-migration.md)
- [Windows Communication Foundation の採用を予測します。将来的な統合を簡略化](../../../../docs/framework/wcf/feature-details/anticipating-adopting-the-wcf-easing-future-integration.md)
- [Windows Communication Foundation の採用](../../../../docs/framework/wcf/feature-details/adopting-wcf.md)
- [使用目的と使用標準に基づく ASP.NET Web サービスと WCF との比較](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
- [開発者の視点から見た ASP.NET Web サービスと WCF との比較](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-development.md)
