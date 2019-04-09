---
title: '方法: Net.TCP ポート共有サービスを有効にする'
ms.date: 03/30/2017
helpviewer_keywords:
- port sharing [WCF]
- activation services [WCF]
ms.assetid: c9175af4-c27c-4765-bf45-b8f7528a7282
ms.openlocfilehash: 77d1d983da87b37c6267cc38a16db446782797f1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130651"
---
# <a name="how-to-enable-the-nettcp-port-sharing-service"></a>方法: Net.TCP ポート共有サービスを有効にする
Windows Communication Foundation (WCF) は、複数のプロセスで TCP ポート共有が簡単に、Net.TCP ポート共有サービスと呼ばれる Windows サービスを使用します。 このサービスは、WCF の一部としてインストールされますが、サービスのセキュリティ予防措置としてデフォルトが有効でないとようにする必要があります手動で有効にする最初の使用前にします。 このトピックでは、Microsoft 管理コンソール (MMC) スナップインを使用して、Net TCP ポート共有サービスを設定する方法について説明します。  
  
 Net.TCP ポート共有サービスを有効にするし、手動で開始するを参照してください。[方法。ポート共有を使用する WCF サービスを構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)このサービスを使用するサービスを構成する方法についてはします。  
  
 Net.tcp:// ポート共有を使用するサンプルを参照してください、 [Net.TCP ポート共有のサンプル](../../../../docs/framework/wcf/samples/net-tcp-port-sharing-sample.md)します。  
  
### <a name="to-enable-the-nettcp-port-sharing-service-using-mmc"></a>MMC を使用して Net.TCP ポート共有サービスを有効にするには  
  
1.  スタート メニューからコマンド プロンプト ウィンドウを開き、入力のいずれかのサービス管理コンソールを開く`services.msc`またはを実行を開き、入力`services.msc` ボックスにします。  
  
2.  **名前**サービスの一覧の列を右クリックし、 **Net.Tcp Port Sharing Service**を選択し、**プロパティ** メニューから。  
  
3.  サービスの手動起動を有効にする、**プロパティ**ウィンドウを選択、**全般** タブで、し、、**スタートアップの種類**ボックスの 手動とクリックして**適用**します。  
  
4.  サービスの状態 領域で、サービスを開始するには、クリックして、**開始**ボタンをクリックします。 これで、サービスの状態には "開始" が表示されます。  
  
5.  サービスの一覧を返すをクリックして、 **OK**、MMC コンソールを終了するとします。  
  
## <a name="example"></a>例  
  
## <a name="see-also"></a>関連項目

- [Net.TCP ポート共有](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)
- [Net.TCP ポート共有サービスを構成する](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
