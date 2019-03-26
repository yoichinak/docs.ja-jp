---
title: 基本的なプログラミング ライフサイクル
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: d5322dfca1aa006ba2fc85b5dedebd09941f9c0e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499224"
---
# <a name="basic-programming-lifecycle"></a>基本的なプログラミング ライフサイクル
Windows Communication Foundation (WCF) は、アプリケーションまたは異なるアプリケーション プラットフォームで、インターネット経由で、同じコンピューターでがかどうかとの通信を使用できます。 このトピックでは、WCF アプリケーションを構築するために必要なタスクについて説明します。 実際のサンプル アプリケーションでは、[チュートリアル入門](../../../docs/framework/wcf/getting-started-tutorial.md)を参照してください。  
  
## <a name="the-basic-tasks"></a>基本的なタスク  
 基本的な作業は、次の順序で行います。  
  
1.  サービス コントラクトを定義します。 サービス コントラクトでは、サービスの署名、交換するデータ、およびコントラクトに必要なその他のデータを指定します。 詳細については、[Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md)を参照してください。  
  
2.  コントラクトを実装します。 サービス コントラクトを実装するには、そのコントラクトを実装するクラスを作成し、ランタイムに必要なカスタム動作を指定します。 詳細については、[Implementing Service Contracts](../../../docs/framework/wcf/implementing-service-contracts.md)を参照してください。  
  
3.  エンドポイントおよびその他の動作情報を指定して、サービスを構成します。 詳細については、[サービスを構成する](../../../docs/framework/wcf/configuring-services.md)を参照してください。  
  
4.  サービスをホストします。 詳細については、[ホスティング サービス](../../../docs/framework/wcf/hosting-services.md)を参照してください。  
  
5.  クライアント アプリケーションを構築します。 詳細については、[クライアントを構築する](../../../docs/framework/wcf/building-clients.md)を参照してください。  
  
 このセクションのトピックではこの順に従って説明しますが、手順を最初から実行しないシナリオもあります。 たとえば、既存のサービスを使用するクライアントを構築する場合は、手順 5. から開始します。 また、既存のクライアント アプリケーションが使用するサービスを構築する場合は、手順 5. を省略できます。  
  
 サービス コントラクトの作成に慣れているが、参照することも[拡張機能の概要](../../../docs/framework/wcf/introduction-to-extensibility.md)します。 確認して、サービスに関する問題があれば、 [WCF トラブルシューティング クイック スタート](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md)を同じまたは類似した問題があるかどうかを確認します。  
  
## <a name="see-also"></a>関連項目
- [サービス コントラクトの実装](../../../docs/framework/wcf/implementing-service-contracts.md)
