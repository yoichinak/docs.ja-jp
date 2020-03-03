---
title: WCF サービス ホストの自動起動の制御
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 7f21cd7ea600277461146387b962a89ea0a8472b
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320628"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a>WCF サービス ホストの自動起動の制御
複数のプロジェクトを含む同じ Visual Studio ソリューションで別のプロジェクトをデバッグするときに、WCF サービスライブラリプロジェクトの Windows Communication Foundation (WCF) サービスホスト (Wcfsvchost.exe) の自動起動機能を制御できます。  
  
 これを行うには、**ソリューションエクスプローラー**で Wcf サービスプロジェクトを右クリックし、 **[プロパティ]** をクリックして、 **[wcf オプション]** タブをクリックします。既定では、 **[同じソリューションで別のプロジェクトをデバッグするときに WCF サービスホストを開始する]** チェックボックスがオンになっています。 このチェックボックスをオフにすると、同じソリューションで別のプロジェクトがデバッグされるときに、この特定のプロジェクトの WCF サービスホストが起動されないようにすることができます。  
  
 この動作は、F5 キーによるデバッグや、このプロジェクトへのサービス参照の追加の機能には影響を与えません。  
  
 このオプションは、次のプロジェクトで使用できます。  
  
- WCF サービスライブラリプロジェクト。  
  
- シーケンシャル ワークフロー サービス ライブラリ プロジェクト  
  
- ステート マシン ワークフロー サービス ライブラリ プロジェクト  
  
- 配信サービス ライブラリ プロジェクト  
  
## <a name="see-also"></a>関連項目

- [WCF サービス ホスト (WcfSvcHost.exe)](wcf-service-host-wcfsvchost-exe.md)
