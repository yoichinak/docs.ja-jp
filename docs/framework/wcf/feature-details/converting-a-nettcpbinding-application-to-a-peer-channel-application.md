---
title: NetTcpBinding アプリケーションからピア チャネル アプリケーションへの変換
ms.date: 03/30/2017
ms.assetid: d4137292-a923-4b8f-8594-42276f2d3ce2
ms.openlocfilehash: 2daeb28ee984e6df576fc3da0aacc9d5f7497c96
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59077499"
---
# <a name="converting-a-nettcpbinding-application-to-a-peer-channel-application"></a>NetTcpBinding アプリケーションからピア チャネル アプリケーションへの変換
[!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] を使用するクライアント間の接続は、その接続パラメーターを記述するバインディングを使用して作成できます。 ピアツーピア接続を使用するように [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] アプリケーションを変換するには、クライアントを接続するときにこのテクノロジをサポートするバインディングが必要です。 ピア チャネルには、<xref:System.ServiceModel.NetPeerTcpBinding> と呼ばれるバインディングが用意されています。このバインディングは、<xref:System.ServiceModel.NetTcpBinding> と同じような方法で使用できます。 主な違いは、リゾルバー サービスの仕様とセキュリティ設定の定義です。  
  
 アプリケーションでリゾルバーとセキュリティの既定の設定を使用する場合、通常のクライアント/サーバー ベースのアプリケーションは、アプリケーションの構成ファイルでバインディング名を "NetTcpBinding" から "NetPeerTcpBinding" に変更するだけで、ピア チャネルを使用するように変換できます。アプリケーションのコード ベースを変更する必要はありません。  
  
## <a name="see-also"></a>関連項目

- [ピア チャネル アプリケーションの構築](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
- [システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)
