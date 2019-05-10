---
title: ローカル チャネル
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 11f3e4fe07ffa285f72ba8fd92224a3ba78d238b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64656037"
---
# <a name="local-channel"></a>ローカル チャネル
ローカル チャネルは、同じアプリケーション ドメイン内の通信に使用される Windows Communication Foundation (WCF) トランスポート チャネルです。 これは、クライアントとサービスが同じアプリケーション ドメイン内で実行されており、通常の WCF チャネル スタックのオーバーヘッド (メッセージのシリアル化と逆シリアル化) を回避する必要がある場合に役に立ちます。  
  
## <a name="demonstrates"></a>使用例  
 ローカル チャネル  
  
## <a name="discussion"></a>説明  
 このサンプルは、2 つのプロジェクト ファイルで構成されます。  
  
- **LocalChannel**:現在のアプリケーション ドメイン内のローカル チャネルのプログラム表現。 このプロジェクトでは、送信側コンポーネントがメッセージをメモリ内キューに入れて、受信側コンポーネントがメッセージをキューから削除して受信します。  
  
- **ClientAndService**:このプロジェクトは、コンソール アプリケーションでのサービスをホストし、しを同じアプリケーション ドメイン内からサービスを呼び出すクライアントを実行します。  
  
 ローカル チャネルのデザインでは、速度を上げるためにチャネル スタックとシリアル化プロセスの両方がスキップされます。 ローカル トランスポート チャネルは、キューを使用してサービス呼び出しをクライアントからサービスに転送し、値をクライアントに返すことによって実装されます。 このサンプルでは、パラメーターと戻り値をシリアル化するのではなく、オブジェクトをコピーします。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1. LocalChannel ソリューションをビルドして実行します。  
  
2. サービス ホストが起動し、クライアントがローカル チャネルを使用してサービスを呼び出します。 コンソール ウィンドウが表示され、サービス呼び出しの結果が示されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
