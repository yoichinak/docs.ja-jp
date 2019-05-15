---
title: NetTcpBinding アプリケーションからピア チャネル アプリケーションへの変換
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: b89afbe59b73288ba357fa55ec5d55c1fb18352b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582787"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>NetTcpBinding アプリケーションからピア チャネル アプリケーションへの変換
[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] を使用するクライアント間の接続は、その接続パラメーターを記述するバインディングを使用して作成できます。 ピア ツー ピア接続を使用する .NET Framework アプリケーションへの変換には、クライアント接続を行うときに、このテクノロジをサポートするバインディングが必要です。 ピア チャネルには、<xref:System.ServiceModel.NetPeerTcpBinding> と呼ばれるバインディングが用意されています。このバインディングは、<xref:System.ServiceModel.NetTcpBinding> と同じような方法で使用できます。 主な違いは、リゾルバー サービスの仕様とセキュリティ設定の定義です。  
  
 アプリケーションでリゾルバーとセキュリティの既定の設定を使用する場合、通常のクライアント/サーバー ベースのアプリケーションは、アプリケーションの構成ファイルでバインディング名を "NetTcpBinding" から "NetPeerTcpBinding" に変更するだけで、ピア チャネルを使用するように変換できます。アプリケーションのコード ベースを変更する必要はありません。  
  
## <a name="see-also"></a>関連項目

- [ピア チャネル アプリケーションの構築](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)
