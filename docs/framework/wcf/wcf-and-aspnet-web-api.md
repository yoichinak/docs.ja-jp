---
title: WCF と ASP.NET Web API
ms.date: 03/30/2017
ms.assetid: 08ceded3-fd9a-4467-9715-c4cbd9c7228e
ms.openlocfilehash: d805c09bef45932ba006a213343429ae7c9303df
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192005"
---
# <a name="wcf-and-aspnet-web-api"></a>WCF と ASP.NET Web API
WCF は、サービス指向のアプリケーションを構築するための Microsoft の統一プログラミング モデルです。 これを使用して開発者は、プラットフォーム間を統合し、既存のコンポーネントと相互運用する、セキュリティで保護された信頼性の高いトランザクション型のソリューションを構築できます。 [ASP.NET Web API](https://www.asp.net/web-api)をさまざまなブラウザーやモバイル デバイスなどのクライアントに提供される HTTP サービスを構築するが容易にするフレームワークです。 ASP.NET Web API は、.NET Framework に基づいて RESTful アプリケーションを構築するのに最適なプラットフォームです。 このトピックでは、ニーズに最適なテクノロジを決定するのに役立つガイドラインを示します。  
  
## <a name="choosing-which-technology-to-use"></a>使用するテクノロジの選択  
 各テクノロジの主な機能を次の表に示します。  
  
|WCF|ASP.NET Web API|  
|---------|---------------------|  
|複数のトランスポート プロトコル (HTTP、TCP、UDP、およびカスタム トランスポート) をサポートするサービスを構築し、構築したサービスを切り替えることができます。|HTTP のみ。 HTTP のファーストクラスのプログラミング モデル。 さまざまなブラウザー、幅広い顧客にアプローチなどを有効にするモバイル デバイスからのアクセスに適しています。|  
|メッセージの種類が同じ複数のエンコーディング (テキスト、MTOM、およびバイナリ) をサポートするサービスを構築し、構築したサービスを切り替えることができます。|XML や JSON などのさまざまなメディアの種類をサポートする Web API を構築できます。|  
|Reliable Messaging、Transactions、Message Security などの WS-* 標準を使用してサービスを構築できます。|基本プロトコルを使用し、HTTP、Websocket、SSL、JSON、XML などの形式します。 Reliable Messaging や Transactions などの高レベルのプロトコルはサポートされません。|  
|要求/応答、一方向、および双方向の各メッセージ交換パターンをサポートしています。|HTTP は要求/応答ですが、その他のパターンをサポートできる[SignalR](https://github.com/SignalR/SignalR)と Websocket の統合。|  
|WCF SOAP サービスは WSDL で記述でき、スキーマが複雑なサービスの場合でも自動化ツールを使用してクライアント プロキシを生成できます。|スニペットを記述する自動生成された HTML ヘルプ ページから OData で統合された API 用に構造化されたメタデータまで、Web API を記述するためのさまざまな方法があります。|  
|.NET Framework に付属しています。|.NET Framework に付属していますが、オープン ソースであるため、個別のダウンロードとして帯域外でも使用できます。|  
  
 WCF を使用すると、さまざまなトランスポート経由でアクセスできる信頼性の高い、セキュリティで保護された web サービスを作成します。 ASP.NET Web API を使用すると、さまざまなクライアントからアクセスできる HTTP ベースのサービスを作成できます。 ASP.NET Web API は、新しい REST スタイルのサービスを作成および設計する場合に使用します。 WCF では REST スタイルのサービスの作成を一部サポートしていますが、ASP.NET Web API の REST のサポートはより詳細で、以降の REST 機能の強化は ASP.NET Web API で行われる予定です。 既存の WCF サービスがあり、追加の REST エンドポイントを公開する場合は、WCF および <xref:System.ServiceModel.WebHttpBinding> を使用してください。  
  
## <a name="see-also"></a>関連項目

- [Windows Communication Foundation とは](../../../docs/framework/wcf/whats-wcf.md)
- [Windows Communication Foundation の基本概念](../../../docs/framework/wcf/fundamental-concepts.md)
