---
title: ローカル チャネル
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: d6d6a91d12a25051f4eefc98f28e570450fc519d
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044895"
---
# <a name="local-channel"></a>ローカル チャネル
ローカルチャネルは、同じアプリケーションドメイン内の通信に使用される Windows Communication Foundation (WCF) トランスポートチャネルです。 これは、クライアントとサービスが同じアプリケーション ドメイン内で実行されており、通常の WCF チャネル スタックのオーバーヘッド (メッセージのシリアル化と逆シリアル化) を回避する必要がある場合に役に立ちます。  
  
## <a name="demonstrates"></a>使用例  
 ローカル チャネル  
  
## <a name="discussion"></a>説明  
 このサンプルは、2 つのプロジェクト ファイルで構成されます。  
  
- **Localchannel**:現在のアプリケーションドメイン内のローカルチャネルのプログラムによる表現。 このプロジェクトでは、送信側コンポーネントがメッセージをメモリ内キューに入れて、受信側コンポーネントがメッセージをキューから削除して受信します。  
  
- **Clientandservice**:このプロジェクトは、コンソールアプリケーションでサービスをホストし、クライアントを実行して、同じアプリケーションドメイン内からサービスを呼び出します。  
  
 ローカル チャネルのデザインでは、速度を上げるためにチャネル スタックとシリアル化プロセスの両方がスキップされます。 ローカル トランスポート チャネルは、キューを使用してサービス呼び出しをクライアントからサービスに転送し、値をクライアントに返すことによって実装されます。 このサンプルでは、パラメーターと戻り値をシリアル化するのではなく、オブジェクトをコピーします。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. LocalChannel ソリューションをビルドして実行します。  
  
2. サービス ホストが起動し、クライアントがローカル チャネルを使用してサービスを呼び出します。 コンソール ウィンドウが表示され、サービス呼び出しの結果が示されます。  
  
> [!IMPORTANT]
> サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780)にアクセスして、すべての[!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (wcf) とサンプルをダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
