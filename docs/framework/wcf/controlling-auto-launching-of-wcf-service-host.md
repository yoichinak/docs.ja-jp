---
title: WCF サービス ホストの自動起動の制御
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 2fa060e567fba9bb5e6344b2c8fc67fb639ad0f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228498"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>WCF サービス ホストの自動起動の制御
複数のプロジェクトを含む同じ Visual Studio ソリューション内の別のプロジェクトをデバッグする場合は、WCF サービス ライブラリ プロジェクトでは、Windows Communication Foundation (WCF) サービス ホスト (WcfSvcHost.exe) の自動起動機能を制御できます。  
  
 これを行うで WCF サービス プロジェクトを右クリックし**ソリューション エクスプ ローラー**、選択**プロパティ**、 をクリック**WCF オプション**タブ。**開始 WCF サービス ホスト、同じソリューション内の別のプロジェクトをデバッグするときに** チェック ボックスが既定で有効にします。 同じソリューションで別のプロジェクトのデバッグ時に、この特定のプロジェクトの WCF サービス ホストが起動しないように、ボックスをオフにすることができます。  
  
 この動作は、F5 キーによるデバッグや、このプロジェクトへのサービス参照の追加の機能には影響を与えません。  
  
 このオプションは、次のプロジェクトで使用できます。  
  
-   WCF サービス ライブラリ プロジェクト。  
  
-   シーケンシャル ワークフロー サービス ライブラリ プロジェクト  
  
-   ステート マシン ワークフロー サービス ライブラリ プロジェクト  
  
-   配信サービス ライブラリ プロジェクト  
  
## <a name="see-also"></a>関連項目

- [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
