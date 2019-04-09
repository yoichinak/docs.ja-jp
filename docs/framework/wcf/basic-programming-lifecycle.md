---
title: 基本的なプログラミング ライフサイクル
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: 32586ad3ec62630e6abafd33b385788c20155b28
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59178491"
---
# <a name="basic-programming-lifecycle"></a>基本的なプログラミング ライフサイクル
Windows Communication Foundation (WCF) は、アプリケーションまたは異なるアプリケーション プラットフォームで、インターネット経由で、同じコンピューターでがかどうかとの通信を使用できます。 このトピックでは、WCF アプリケーションを構築するために必要なタスクについて説明します。 実際のサンプル アプリケーションでは、次を参照してください。[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)します。  
  
## <a name="the-basic-tasks"></a>基本的なタスク  
 基本的な作業は、次の順序で行います。  
  
1.  サービス コントラクトを定義します。 サービス コントラクトでは、サービスの署名、交換するデータ、およびコントラクトに必要なその他のデータを指定します。 詳細については、次を参照してください。 [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md)します。  
  
2.  コントラクトを実装します。 サービス コントラクトを実装するには、そのコントラクトを実装するクラスを作成し、ランタイムに必要なカスタム動作を指定します。 詳細については、次を参照してください。 [Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md)します。  
  
3.  エンドポイントおよびその他の動作情報を指定して、サービスを構成します。 詳細については、次を参照してください。[サービスを構成する](../../../docs/framework/wcf/configuring-services.md)します。  
  
4.  サービスをホストします。 詳細については、次を参照してください。[ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)します。  
  
5.  クライアント アプリケーションを構築します。 詳細については、次を参照してください。[クライアントを構築する](../../../docs/framework/wcf/building-clients.md)します。  
  
 このセクションのトピックではこの順に従って説明しますが、手順を最初から実行しないシナリオもあります。 たとえば、既存のサービスを使用するクライアントを構築する場合は、手順 5. から開始します。 また、既存のクライアント アプリケーションが使用するサービスを構築する場合は、手順 5. を省略できます。  
  
 サービス コントラクトの作成に慣れているが、参照することも[拡張機能の概要](../../../docs/framework/wcf/introduction-to-extensibility.md)します。 確認して、サービスに関する問題があれば、 [WCF トラブルシューティング クイック スタート](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)を同じまたは類似した問題があるかどうかを確認します。  
  
## <a name="see-also"></a>関連項目

- [サービス コントラクトの実装](../../../docs/framework/wcf/implementing-service-contracts.md)
