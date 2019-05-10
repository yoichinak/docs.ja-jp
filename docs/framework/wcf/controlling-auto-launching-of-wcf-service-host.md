---
title: WCF サービス ホストの自動起動の制御
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 806d85df2a7fff63704db755400b81cc2dc5c37b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652085"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>WCF サービス ホストの自動起動の制御
複数のプロジェクトを含む同じ Visual Studio ソリューション内の別のプロジェクトをデバッグする場合は、WCF サービス ライブラリ プロジェクトでは、Windows Communication Foundation (WCF) サービス ホスト (WcfSvcHost.exe) の自動起動機能を制御できます。  
  
 これを行うで WCF サービス プロジェクトを右クリックし**ソリューション エクスプ ローラー**、選択**プロパティ**、 をクリック**WCF オプション**タブ。**開始 WCF サービス ホスト、同じソリューション内の別のプロジェクトをデバッグするときに** チェック ボックスが既定で有効にします。 同じソリューションで別のプロジェクトのデバッグ時に、この特定のプロジェクトの WCF サービス ホストが起動しないように、ボックスをオフにすることができます。  
  
 この動作は、F5 キーによるデバッグや、このプロジェクトへのサービス参照の追加の機能には影響を与えません。  
  
 このオプションは、次のプロジェクトで使用できます。  
  
- WCF サービス ライブラリ プロジェクト。  
  
- シーケンシャル ワークフロー サービス ライブラリ プロジェクト  
  
- ステート マシン ワークフロー サービス ライブラリ プロジェクト  
  
- 配信サービス ライブラリ プロジェクト  
  
## <a name="see-also"></a>関連項目

- [WCF サービス ホスト (WcfSvcHost.exe)](../../../docs/framework/wcf/wcf-service-host-wcfsvchost-exe.md)
