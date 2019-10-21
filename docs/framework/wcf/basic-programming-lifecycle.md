---
title: 基本的なプログラミング ライフサイクル
ms.date: 03/30/2017
helpviewer_keywords:
- service creation [WCF]
ms.assetid: 7cf21bfe-23bd-46aa-8033-609f851dbf76
ms.openlocfilehash: fe578ba3c655c9c9ea8398b9b2e4d4f974153c8e
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320824"
---
# <a name="basic-programming-lifecycle"></a>基本的なプログラミング ライフサイクル
Windows Communication Foundation (WCF) を使用すると、アプリケーションは、同じコンピューター上、インターネット上、または異なるアプリケーションプラットフォーム上にあるかどうかを通信できます。 このトピックでは、WCF アプリケーションの構築に必要なタスクの概要を示します。 実際のサンプルアプリケーションについては、[はじめにチュートリアル](getting-started-tutorial.md)を参照してください。  
  
## <a name="the-basic-tasks"></a>基本的なタスク  
 基本的な作業は、次の順序で行います。  
  
1. サービス コントラクトを定義します。 サービス コントラクトでは、サービスの署名、交換するデータ、およびコントラクトに必要なその他のデータを指定します。 詳細については、 「[サービス コントラクトの設計](designing-service-contracts.md)」を参照してください。  
  
2. コントラクトを実装します。 サービス コントラクトを実装するには、そのコントラクトを実装するクラスを作成し、ランタイムに必要なカスタム動作を指定します。 詳細については、「[サービス コントラクトの実装](implementing-service-contracts.md)」を参照してください。  
  
3. エンドポイントおよびその他の動作情報を指定して、サービスを構成します。 詳細については、「[サービスの構成](configuring-services.md)」を参照してください。  
  
4. サービスをホストします。 詳細については、「[ホスティングサービス](hosting-services.md)」を参照してください。  
  
5. クライアント アプリケーションを構築します。 詳細については、「[クライアントの構築](building-clients.md)」を参照してください。  
  
 このセクションのトピックではこの順に従って説明しますが、手順を最初から実行しないシナリオもあります。 たとえば、既存のサービスを使用するクライアントを構築する場合は、手順 5. から開始します。 また、既存のクライアント アプリケーションが使用するサービスを構築する場合は、手順 5. を省略できます。  
  
 サービスコントラクトの開発に慣れたら、「[拡張機能の概要」を](introduction-to-extensibility.md)参照することもできます。 サービスで問題が発生した場合は、 [WCF トラブルシューティングクイックスタート](wcf-troubleshooting-quickstart.md)をチェックして、他の問題が同一または類似しているかどうかを確認してください。  
  
## <a name="see-also"></a>関連項目

- [サービス コントラクトの実装](implementing-service-contracts.md)
