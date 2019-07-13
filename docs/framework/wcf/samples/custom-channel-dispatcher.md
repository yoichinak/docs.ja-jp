---
title: カスタム チャネル ディスパッチャー
ms.date: 03/30/2017
ms.assetid: 813acf03-9661-4d57-a3c7-eeab497321c6
ms.openlocfilehash: 20574b4c849f312cb2cf55709d8d5e2a9b5dbca7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62003107"
---
# <a name="custom-channel-dispatcher"></a>カスタム チャネル ディスパッチャー
このサンプルでは、<xref:System.ServiceModel.ServiceHostBase> を直接実装することによって、カスタマイズした方法でチャネル スタックを作成する方法と、Web ホスト環境でカスタム チャネル ディスパッチャーを作成する方法を示します。 チャネル ディスパッチャーは、<xref:System.ServiceModel.Channels.IChannelListener> と対話してチャネルを受け入れ、チャネル スタックからメッセージを取得します。 このサンプルには、<xref:System.ServiceModel.Activation.VirtualPathExtension> を使用して Web ホスト環境でチャネル スタックを作成する方法を示す基本的なサンプルも用意されています。  
  
## <a name="custom-servicehostbase"></a>カスタム ServiceHostBase  
 このサンプルは、基本データ型を実装して<xref:System.ServiceModel.ServiceHostBase>の代わりに<xref:System.ServiceModel.ServiceHost>チャネル スタックの一番上のレイヤーを処理するカスタム メッセージで、Windows Communication Foundation (WCF) スタックを実装を交換する方法を示します。 仮想メソッド <xref:System.ServiceModel.ServiceHostBase.InitializeRuntime%2A> をオーバーライドして、チャネル リスナーとチャネル ディスパッチャーを作成します。  
  
 Web ホスト サービスを実装するには、サービス拡張 <xref:System.ServiceModel.Activation.VirtualPathExtension> を <xref:System.ServiceModel.ServiceHostBase.Extensions%2A> コレクションから取得し、<xref:System.ServiceModel.Channels.BindingParameterCollection> に追加します。これにより、トランスポート層で、ホスト環境の設定 (つまり、インターネット インフォメーション サービス (IIS) および Windows プロセス アクティブ化サービス (WAS) の設定) に基づいてチャネル リスナーを構成する方法を認識できるようになります。  
  
## <a name="custom-channel-dispatcher"></a>カスタム チャネル ディスパッチャー  
 カスタム チャネル ディスパッチャーは型 <xref:System.ServiceModel.Dispatcher.ChannelDispatcherBase> を拡張します。 この型はチャネル層のプログラミング ロジックを実装します。 このサンプルでは、要求/応答メッセージ交換パターンでサポートされるのは <xref:System.ServiceModel.Channels.IReplyChannel> だけですが、カスタム チャネル ディスパッチャーは他の種類のチャネルに簡単に拡張できます。  
  
 ディスパッチャーは、まずチャネル リスナーを開き、次にシングルトン応答チャネルを受け入れます。 このチャネルを使用して、無限ループでメッセージ (応答) の送信を開始します。 要求ごとに、応答メッセージを作成し、クライアントに返信します。  
  
## <a name="creating-a-response-message"></a>応答メッセージの作成  
 メッセージ処理は型 `MyServiceManager` で実装されます。 `HandleRequest` メソッドでは、要求がサポートされているかどうか確認するために、メッセージの `Action` ヘッダーが最初にチェックされます。 定義済みの SOAP アクション"http://tempuri.org/HelloWorld/Hello"メッセージのフィルター処理を提供するように定義します。 これはの WCF 実装では、サービス コントラクトの概念に似ています<xref:System.ServiceModel.ServiceHost>します。  
  
 正しい SOAP アクションの場合、サンプルでは、<xref:System.ServiceModel.ServiceHost> の場合と同じように、要求されたメッセージ データを取得し、要求に対して対応する応答を生成します。  
  
 特に、この場合、正しくコンパイルされていることを確認するためにブラウザーからサービスを参照できるように、カスタム HTML メッセージを返して HTTP-GET 動詞を処理します。 SOAP アクションが一致しない場合は、エラー メッセージを返信して、要求がサポートされていないことを示します。  
  
 このサンプルのクライアントは、サービスから何も想定していない通常の WCF クライアントです。 サービスが通常の WCF から取得した内容に一致するように特別設計された、<xref:System.ServiceModel.ServiceHost>実装します。 したがって、クライアントに必要なのはサービス コントラクトだけです。  
  
## <a name="using-the-sample"></a>サンプルの使用  
 クライアント アプリケーションを直接実行すると、次の出力が生成されます。  
  
```Output  
Client is talking to a request/reply WCF service.   
Type what you want to say to the server: Howdy  
Server replied: You said: Howdy. Message id: 1  
Server replied: You said: Howdy. Message id: 2  
Server replied: You said: Howdy. Message id: 3  
Server replied: You said: Howdy. Message id: 4  
Server replied: You said: Howdy. Message id: 5  
```  
  
 HTTP-GET メッセージがサーバーで処理されるように、ブラウザーからサービスを参照することもできます。 この場合、適切に書式設定された HTML テキストが返信されます。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に移動[Windows Communication Foundation (WCF) と .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](https://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプル。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\CustomChannelDispatcher`
