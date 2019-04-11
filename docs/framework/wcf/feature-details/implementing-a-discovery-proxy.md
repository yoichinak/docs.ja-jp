---
title: 探索プロキシの実装
ms.date: 03/30/2017
ms.assetid: dda20e79-8df3-438e-a281-69d779d978ec
ms.openlocfilehash: 5d9296d8ba70d4c9e8d8339fa3a032d9c4c62826
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141004"
---
# <a name="implementing-a-discovery-proxy"></a>探索プロキシの実装
ここでは、探索プロキシの実装に必要な手順について説明します。 探索プロキシは、サービスのリポジトリを格納するスタンドアロンのサービスです。 クライアントは探索プロキシに対し、そのプロキシで認識される探索可能なサービスを問い合わせることができます。 プロキシにサービスを登録する方法は、実装手段によって異なります。 たとえば、探索プロキシが既存のサービス リポジトリに接続でき、その情報を探索可能にできる場合、管理者は管理 API を使用して探索可能なサービスをプロキシに追加することができます。または、探索プロキシにアナウンス機能を使用し、内部キャッシュを更新できます。  
  
 WCF 実装は、プロキシを簡単にビルドできる基本クラスを提供します。 これらの API を利用して、既存のリポジトリの上に探索プロキシをビルドできます。  
  
 ここで実装される探索プロキシは、探索可能にしてクライアントからエンドポイントを検索できるという点で、他の WCF サービスと似ています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [方法: 探索プロキシを実装する](../../../../docs/framework/wcf/feature-details/how-to-implement-a-discovery-proxy.md)  
 探索プロキシを実装する方法について説明します。  
  
 [方法: 探索プロキシで登録される探索可能なサービスの実装する](../../../../docs/framework/wcf/feature-details/discoverable-service-that-registers-with-the-discovery-proxy.md)  
 探索プロキシで登録される探索可能な WCF サービスを実装する方法について説明します。  
  
 [方法: 探索プロキシを使用してサービスを検索するクライアント アプリケーションを実装する](../../../../docs/framework/wcf/feature-details/client-app-discovery-proxy-to-find-a-service.md)  
 サービスの検索、探索プロキシを使用する WCF クライアント アプリケーションを実装する方法について説明します。  
  
 [方法: 探索プロキシをテストする](../../../../docs/framework/wcf/feature-details/how-to-test-the-discovery-proxy.md)  
 前の 3 つのトピックに記述されたコードのテスト方法について説明します。  
  
## <a name="see-also"></a>関連項目

- [WCF Discovery](../../../../docs/framework/wcf/feature-details/wcf-discovery.md)
- [方法: プログラムを使用して探索可能性に WCF サービスとクライアントを追加する](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)
