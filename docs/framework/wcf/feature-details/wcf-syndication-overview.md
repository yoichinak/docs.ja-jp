---
title: WCF 配信の概要
ms.date: 03/30/2017
ms.assetid: af6d4c39-e5e8-4099-aee6-5261feff9107
ms.openlocfilehash: ef62c4460ff5dd4890de174afda671facee97f2e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189834"
---
# <a name="wcf-syndication-overview"></a>WCF 配信の概要
Windows Communication Foundation (WCF) は、WCF サービスから配信フィードを公開するためのサポートを提供します。 配信は、サーバーがフィードと呼ばれる相互運用可能な形式でアプリケーション データの一部を公開するためのアプリケーション統合の機構です。 フィードはアプリケーション データのコレクションであり、フィード レベルのメタデータ (タイトル、作成者、URL、およびその他のメタデータ) と一連のフィード アイテムから構成されます。 フィード内で、フィード アイテムは通常、発生の逆順に並べられます。 フィード アイテムは、アイテム レベルのメタデータの標準セット (タイトル、URL、作成日時、カテゴリ、およびその他のアイテム レベルのメタデータ) と任意の大きさのアプリケーション固有のデータから構成されます。 配信フィードの 2 つの最も一般的な種類は、RSS Really Simple Syndication () 2.0 と Atom 1.0 では、WCF でサポートされるは。  
  
## <a name="object-model"></a>オブジェクト モデル  
 WCF には、一連の形式に依存しない方法で、フィード、フィード アイテム、および関連するメタデータを操作するための配信に固有のクラスが定義されています: <xref:System.ServiceModel.Syndication.SyndicationFeed>、 <xref:System.ServiceModel.Syndication.SyndicationItem>、 <xref:System.ServiceModel.Syndication.SyndicationPerson>、 <xref:System.ServiceModel.Syndication.SyndicationLink>、およびその他の配信に固有のクラス。 WCF には、配信のサポートなどを提供する WCF REST プログラミング モデル上で構築されるインフラストラクチャ クラスも定義されています: <xref:System.ServiceModel.Syndication.Atom10FeedFormatter>、および<xref:System.ServiceModel.Syndication.Rss20FeedFormatter>します。 フィード フォーマッタ クラスは、オブジェクト モデルの RSS 2.0 と Atom 1.0 に対する双方向のシリアル化をサポートしています。  
  
## <a name="scenarios"></a>シナリオ  
 現在、配信はブログで広く使用されています。ブログの作成者は、さまざまな種類の情報を定期的に公開します。 たとえば、文字、画像、音声などの情報です。 多くの新聞や雑誌でも、配信を使用してニュースや記事を公開しています。 このようなフィードを定期受信することで、ユーザーはこれらのサイトから発信されるすべての最新情報を得ることができます。 配信は一般的にブログや出版社で使用されますが、一連の情報を公開する任意のアプリケーションで使用することもできます。たとえば、配信フィードを使用したバグ データベースの公開が考えられます。 呼ばれる操作を公開する WCF サービスを作成する`CodeDefects`します。 この操作では、調べたいバグを報告した人の電子メール アドレスを指定するパラメーターを使用できます。 クライアントは、次の URL を使用して、操作を呼び出します。`http://someserver/bugDatabase/CodeDefects?user=johndoe`します。  
  
## <a name="syndication-formats"></a>配信フォーマット  
 WCF 配信プラットフォームでは、RSS 2.0 と Atom 1.0 をサポートします。  
  
## <a name="see-also"></a>関連項目

- [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)
