---
title: "IPv6 の自動構成"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 581c1d21-1013-43a3-bf3e-2d9ead62b79c
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: b116e3aa88f919b850d6f79754d25ee10ac974f1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ipv6-auto-configuration"></a>IPv6 の自動構成
IPv6 用の 1 つの重要な目標は、ノードのプラグ アンド プレイをサポートすることです。 つまり、IPv6 ネットワークにノードを接続して、それを人間の操作なしに自動的に構成できる必要があります。  
  
## <a name="type-of-auto-configuration"></a>自動構成の種類  
 IPv6 は、次の種類の自動構成をサポートします。  
  
-   **ステートフルな自動構成** この種類の構成では、ノードのインストールと管理のために IPv6 用動的ホスト構成プロトコル (DHCPv6) サーバーが必要なので、特定のレベルの人間の操作が必要です。 DHCPv6 サーバーは、構成情報を提供するノードのリストを保持します。 また、状態情報も保持するのでサーバーは、各アドレスがどのくらいの時間使用されているか、および再割り当てできるようになるタイミングを知ることができます。  
  
-   **ステートレスな自動構成** この種類の構成は、小規模な組織や個人に適しています。 この場合、各ホストは、受信したルーター アドバタイズの内容からそのアドレスを決定します。 IEEE EUI-64 標準を使用して、アドレスのネットワーク ID 部分を定義しますが、リンク上のホストアドレスの一意性を前提とすることは合理的です。  
  
 アドレスの決定方法に関係なく、ノードは、潜在的なアドレスがローカル リンクに対して一意であることを確認する必要があります。 これは、潜在的なアドレスに近隣要請を送信することによって行われます。 ノードが応答を受信する場合は、アドレスが既に使用されていて別のアドレスを決定する必要があることがわかります。  
  
## <a name="ipv6-mobility"></a>IPv6 モビリティ  
 モバイル デバイスの急増によって、新しい要件が導入されました。デバイスが IPv6 インターネット上の場所を任意に変更しても既存の接続を維持できるようにする必要があります。 この機能を提供するために、モバイル ノードに常に到達できるホーム アドレスが割り当てられます。 モバイル ノードが自宅にあるときは、ホーム リンクに接続し、ホーム アドレスを使用します。 モバイル ノードが自宅から離れた場所にあるときは、ホーム エージェント (通常はルーター) が、モバイル ノードと通信相手のノードの間でメッセージを中継します。  
  
## <a name="see-also"></a>参照  
 [インターネット プロトコル バージョン 6](../../../docs/framework/network-programming/internet-protocol-version-6.md)  
 [ソケット](../../../docs/framework/network-programming/sockets.md)
