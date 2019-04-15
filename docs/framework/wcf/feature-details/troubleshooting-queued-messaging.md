---
title: キューに置かれたメッセージングのトラブルシューティング
ms.date: 03/30/2017
ms.assetid: a5f2836f-018d-42f5-a571-1e97e64ea5b0
ms.openlocfilehash: c85b0701c870fe2b4a3c11dc384e890e1ed001dd
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/09/2019
ms.locfileid: "59322044"
---
# <a name="troubleshooting-queued-messaging"></a>キューに置かれたメッセージングのトラブルシューティング
このセクションには、一般的な質問とトラブルシューティングについては、Windows Communication Foundation (WCF) でキューを使用してが含まれています。  
  
## <a name="common-questions"></a>一般的な質問  
 **Q:** WCF の Beta 1 を使用してと MSMQ 修正プログラムをインストールします。 この修正プログラムを削除する必要がありますか。  
  
 **A:** はい。 この修正プログラムのサポートは終了しています。 WCF は、ここで、修正プログラムは不要 MSMQ で動作します。  
  
 **Q:** MSMQ の 2 つのバインドがある:<xref:System.ServiceModel.NetMsmqBinding>と<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>します。 それぞれの用途を教えてください。  
  
 **A:** 使用して、<xref:System.ServiceModel.NetMsmqBinding>の 2 つの WCF アプリケーション間通信をキューに置かれたトランスポートとして MSMQ を使用する場合。 使用して、<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>新しい WCF アプリケーションとの通信に既存の MSMQ アプリケーションを使用する場合。  
  
 **Q:** MSMQ を使用して、アップグレードする必要は、<xref:System.ServiceModel.NetMsmqBinding>と`MsmqIntegration`バインドしますか?  
  
 **A:** いいえ。 これらは共に [!INCLUDE[wxp](../../../../includes/wxp-md.md)] および [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] 上の MSMQ 3.0 で使用できます。 [!INCLUDE[wv](../../../../includes/wv-md.md)] で MSMQ 4.0 にアップグレードすると、バインディングの特定の機能が使用可能になります。  
  
 **Q:** 機能のうち、<xref:System.ServiceModel.NetMsmqBinding>と<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>バインドが MSMQ 4.0 ではなく MSMQ 3.0 で使用可能ですか?  
  
 **A:** 次の機能は、MSMQ 4.0 が含まれない MSMQ 3.0 で使用できます。  
  
-   カスタム配信不能キューは、MSMQ 4.0 でのみサポートされます。  
  
-   MSMQ 3.0 と 4.0 では、有害メッセージの処理方法が異なります。  
  
-   MSMQ 4.0 のみが、リモート トランザクション読み取りをサポートします。  
  
 詳細については、次を参照してください。 [Windows Vista、Windows Server 2003、および Windows XP でのキュー機能の相違点](../../../../docs/framework/wcf/feature-details/diff-in-queue-in-vista-server-2003-windows-xp.md)します。  
  
 **Q:** もう一方の側でキューによる通信と MSMQ 4.0 の一方の側で MSMQ 3.0 を使用できますか。  
  
 **A:** はい。  
  
 **Q:** 新しい WCF クライアントまたはサーバーと既存の MSMQ アプリケーションを統合します。 使用している MSMQ インフラストラクチャの両方の側をアップグレードする必要がありますか。  
  
 **A:** いいえ。 どちら側も MSMQ 4.0 にアップグレードする必要はありません。  
  
## <a name="troubleshooting"></a>トラブルシューティング  
 ここでは、一般的なトラブルシューティングの問題に対する解答を示します。 既知の制限である一部の問題は、リリース ノートにも記載されています。  
  
 **Q:** プライベート キューを使用して、次の例外が発生しました: `System.InvalidOperationException`:URL が無効です。 キューの URL に '$' 文字を使用することはできません。 net.msmq://machine/private/queueName の構文を使用して、プライベート キューをアドレス指定してください。  
  
 **A:** 構成とコードでキューの Uniform Resource Identifier (URI) を確認してください。 URI では、"$" 文字を使用できません。 たとえば、OrdersQueue という名前のプライベート キューのアドレスを指定する場合は、URI を net.msmq://localhost/private/ordersQueue と指定してください。  
  
 **Q:** 呼び出す`ServiceHost.Open()`キューに置かれたアプリケーションでは、次の例外をスローします: `System.ArgumentException`:。ベース アドレスは、URI クエリ文字列を含めることはできません。 なぜでしょうか。  
  
 **A:** URI の構成ファイルと、コードでキューを確認します。 MSMQ のキューでは '?' 文字の使用がサポートされていますが、URI はこれを文字列クエリの開始と解釈します。 この問題を回避するには、'?' 文字を含まないキュー名を使用してください。  
  
 **Q:** 送信が成功しましたが、受信側でサービス操作が呼び出されません。 なぜでしょうか。  
  
 **A:** 回答を確認するのに次のチェック ボックスの一覧に取り組みます。  
  
-   トランザクション キューの要件と指定済みの保証が適合することを確認します。 次の原則に注意してください。  
  
    -   メッセージを送信できる持続性のある (データグラムとセッション)「1 回」の保証 (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`)、トランザクション キューだけにします。  
  
    -   "1 回限りの" 配信の保証付きのセッションのみを送信できます。  
  
    -   セッションでトランザクション キューからメッセージを受け取るには、1 つのトランザクションが必要です。  
  
    -   保証なしの揮発性または持続性のメッセージ (ダイアグラムのみ) を送受信する (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`)、非トランザクション キューにのみです。  
  
-   配信不能キューを確認します。 このキューにメッセージが置かれている場合は、メッセージが配信されなかった理由を特定してください。  
  
-   送信キューを確認して、接続性またはアドレス指定の問題を特定します。  
  
 **Q:** カスタム配信不能キューでは、指定したのですが、配信不能キューが見つからない場合は、例外が発生した送信側アプリケーションを起動したとき、または送信元アプリケーションに配信不能キューにアクセス許可がありません。 なぜ、こうなるのでしょうか。  
  
 **A:** カスタム配信不能キューの URI では、最初のセグメントでは、たとえば、net.msmq://localhost/private/myAppdead-letter queue のように"localhost"またはコンピューター名を含める必要があります。  
  
 **Q:** 常に、カスタムの配信不能キューを定義するために必要な既定の配信不能キューではありますか。  
  
 **A:**「1 回限り」の確実性が場合 (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `true`)、既定値がシステム全体のトランザクション配信不能キューには、カスタム配信不能キューを指定しない場合。  
  
 保証がない場合 (<xref:System.ServiceModel.MsmqBindingBase.ExactlyOnce%2A> = `false`)、既定値には、配信不能キューの機能はありません。  
  
 **Q:** メッセージ「EndpointListener 要件では満たせない、ListenerFactory」SvcHost.Open でサービスをスローします。 なぜでしょうか。  
  
 A:  サービス コントラクトを確認してください。 配置を忘れた"IsOneWay =`true`"すべてのサービス操作にします。 キューは、一方向のサービス操作しかサポートしません。  
  
 **Q:** キューにメッセージがあるが、サービス操作が呼び出されません。 何が問題なのでしょうか。  
  
 **A:** サービス ホストに障害があるかを決定します。 確認するには、トレースを調べるか、`IErrorHandler` を実装します。 既定では、有害メッセージが検出された場合、サービス ホストはエラーになります。  
  
 **Q:** キューにメッセージがあるが、Web でホストされるキューに置かれたサービスがアクティブになりません。 なぜでしょうか。  
  
 **A:** 最も一般的な理由は、アクセス許可です。  
  
1. `NetMsmqActivator` プロセスが実行され、そのキューで、`NetMsmqActivator` の ID に読み取りおよびシーク アクセス許可が割り当てられていることを確認してください。  
  
2. `NetMsmqActivator` がリモート コンピューター上のキューを監視している場合は、`NetMsmqActivator` が制限付きトークンの下で実行されていないことを確認してください。 無制限のトークンを使用して `NetMsmqActivator` を実行するには、以下を実行します。  
  
    ```  
    sc sidtype NetMsmqActivator unrestricted  
    ```  
  
 関連する Web ホストの問題のないセキュリティ以外を参照してください。[キューに置かれたアプリケーションの web ホスト](../../../../docs/framework/wcf/feature-details/web-hosting-a-queued-application.md)します。  
  
 **Q:** アクセスのセッションを最も簡単な方法とは何ですか。  
  
 **A:** オートコンプリートの設定 =`true`最後に、対応する操作では、セッションで、メッセージし、オートコンプリートの設定 =`false`残りのすべてのサービス操作にします。  
  
 **Q:** MSMQ によく寄せられる質問に対する回答はどこで入手できますか。  
  
 **A:** MSMQ の詳細については、次を参照してください。 [Microsoft メッセージ キュー](https://go.microsoft.com/fwlink/?LinkId=87810)します。  
  
 **Q:** サービスはスロー理由、`ProtocolException`両方を含むキューからの読み取りがセッション メッセージをキューに置かれ、データグラム メッセージをキューに登録しますか?  
  
 **A:** までキューに置かれたセッションのメッセージの基本的な違いがあるし、キューに置かれたデータグラム メッセージはで構成されます。 このため、キューを使用するセッション メッセージを読み取ろうとするサービスは、キューを使用するデータグラム メッセージを受信できず、キューを使用するデータグラム メッセージを読み取ろうとするサービスは、セッション メッセージを受信できません。 これら両方の種類のメッセージを同じキューから読み取ろうとすると、次の例外がスローされます。  
  
```  
System.ServiceModel.MsmqPoisonMessageException: The transport channel detected a poison message. This occurred because the message exceeded the maximum number of delivery attempts or because the channel detected a fundamental problem with the message. The inner exception may contain additional information.   
---> System.ServiceModel.ProtocolException: An incoming MSMQ message contained invalid or unexpected .NET Message Framing information in its body. The message cannot be received. Ensure that the sender is using a compatible service contract with a matching SessionMode.  
```  
  
 アプリケーションが同じコンピューターからキューを使用するセッション メッセージとキューを使用するデータグラム メッセージの両方を送信する場合は、任意のカスタム配信不能キューだけでなくシステム配信不能キューで特にこの問題が発生する可能性があります。 メッセージを正常に送信できない場合、メッセージは配信不能キューに移されます。 このような場合は、セッション メッセージとデータグラム メッセージの両方が配信不能キューに置かれる可能性があります。 実行時にキューから読み取るときに両方の種類のメッセージを分離することはできません。そのため、アプリケーションでは、キューを使用するセッション メッセージとキューを使用するデータグラム メッセージの両方を同じコンピューターから送信しないでください。  
  
### <a name="msmq-integration-specific-troubleshooting"></a>MSMQ 統合:特定のトラブルシューティング  
 **Q:** メッセージを送信するとき、またはサービス ホストを開くと、スキームが正しくないことを示すエラーが発生します。 なぜでしょうか。  
  
 **A:** MSMQ 統合バインディングを使用する場合は、msmq.formatname スキームを使用する必要があります。 たとえば、msmq.formatname:DIRECT=OS:.\private$\OrdersQueue などです。 ただし、カスタム配信不能キューを指定するときは、net.msmq スキームを使用する必要があります。  
  
 **Q:** Public または private 形式名を使用し、でサービス ホストを開くときに[!INCLUDE[wv](../../../../includes/wv-md.md)]エラーが発生します。 なぜでしょうか。  
  
 **A:** WCF 統合チャネル[!INCLUDE[wv](../../../../includes/wv-md.md)]有害なメッセージを処理するため、アプリケーションのメイン キューのサブキューを開くことができるかどうかを確認します。 サブキューの名前は、リスナーに渡される msmq.formatname URI から派生します。 MSMQ でのサブキュー名は、直接形式名に限定されます。 そのためにエラーが発生します。 キュー URI を直接形式名に変更してください。  
  
 **Q:** MSMQ アプリケーションからメッセージを受信するときに、メッセージはキューに配置し、受信側の WCF アプリケーションでは読み取りません。 なぜでしょうか。  
  
 **A:** メッセージ本文が含まれるかどうかを確認します。 メッセージに本文がない場合、MSMQ 統合チャネルはメッセージを無視します。 例外を通知する `IErrorHandler` を実装し、トレースを確認してください。  
  
### <a name="security-related-troubleshooting"></a>セキュリティ関連のトラブルシューティング  
 **Q:** ワークグループ モードで既定のバインディングを使用するサンプルを実行すると、メッセージは送信されたようですが、受信側で受信することはありません。  
  
 **A:** 既定では、メッセージは、Active Directory ディレクトリ サービスを必要とする MSMQ 内部証明書を使用して署名されます。 ワークグループ モードでは、Active Directory が使用できないため、メッセージに署名できません。 したがって、メッセージが配信不能キューに置かれ、「署名が不良です」などのエラーの原因が示されます。  
  
 この問題を回避するには、セキュリティを無効にします。 これは、設定で<xref:System.ServiceModel.NetMsmqSecurity.Mode%2A>  =  <xref:System.ServiceModel.NetMsmqSecurityMode.None>ようにワークグループ モードで動作します。  
  
 また、<xref:System.ServiceModel.MsmqTransportSecurity> プロパティから <xref:System.ServiceModel.NetMsmqSecurity.Transport%2A> を取得し、それを <xref:System.ServiceModel.MsmqAuthenticationMode.Certificate> に設定して、クライアント証明書を設定する方法もあります。  
  
 さらに、MSMQ と Active Directory 統合をインストールして回避することもできます。  
  
 **Q:** 既定のバインディングでメッセージを送信するとき (トランスポート セキュリティが有効)、キューを Active Directory で「内部証明書が見つかりません」メッセージが表示されます。 これを修復する方法を教えてください。  
  
 **A:** つまり、送信側の Active Directory で証明書を更新する必要があります。 これを行うには、開く**コントロール パネルの **、**管理ツール**、**コンピュータの管理**、右クリック**MSMQ**を選択します **。プロパティ**します。 選択、**ユーザー証明書** タブでをクリックし、 **Renew**ボタンをクリックします。  
  
 **Q:** 使用してメッセージを送信するとき<xref:System.ServiceModel.MsmqAuthenticationMode.Certificate>し、「無効な証明書」メッセージが表示、使用する証明書を指定します。 これを修復する方法を教えてください。  
  
 **A:** 証明書モードでローカル コンピューターの証明書ストアを使用することはできません。 証明書スナップインを使用して、コンピューターの証明書ストアから現在のユーザー ストアに証明書をコピーする必要があります。 証明書スナップインを開くには、以下を実行します。  
  
1. をクリックして**開始**を選択します**実行**、型`mmc`、 をクリック**OK**します。  
  
2. **Microsoft 管理コンソール**、オープン、**ファイル**メニュー選択し、**スナップインの追加と削除**します。  
  
3. **スナップインの追加と削除**ダイアログ ボックスで、をクリックして、**追加**ボタンをクリックします。  
  
4. **スタンドアロン スナップインの追加**ダイアログ ボックスで選択証明書とクリック**追加**します。  
  
5. **証明書**スナップイン ダイアログ ボックスで、 **ユーザー アカウント** をクリック**完了**します。  
  
6. 次に、2 つ目の証明書スナップインの前の手順を使用して、この時間を選択を追加**コンピューター アカウント** をクリック**次**します。  
  
7. 選択**ローカル コンピューター**  をクリック**完了**します。 これで、コンピューターの証明書ストアから現在のユーザー ストアに証明書をドラッグ アンド ドロップできます。  
  
 **Q:** サービスは、ワークグループ モードで別のコンピューター上のキューから読み取り、ときに「アクセス拒否」例外が発生します。  
  
 **A:** キューにアクセスするリモート アプリケーション、ワークグループ モードでアプリケーションは、キューにアクセスする権限が必要があります。 キューのアクセス制御リスト (ACL) に「匿名ログイン」を追加し、読み取りアクセス許可を付与します。  
  
 **Q:** ネットワーク サービス クライアント (またはドメイン アカウントがない任意のクライアント) は、キューに置かれたメッセージを送信するときに、無効な証明書で、送信が失敗します。 これを修復する方法を教えてください。  
  
 **A:** バインド構成を確認します。 既定のバインディングでは、メッセージに署名するために MSMQ トランスポート セキュリティを有効にしています。 これを無効にしてください。  
  
### <a name="remote-transacted-receives"></a>リモート トランザクション受信  
 **Q:** キューがある場合は、machine (リモート トランザクション受信シナリオ) コンピューター B 上のキューからメッセージを読み取りとの WCF サービス、メッセージがキューから読み取ることができません。 トレース情報を示します、受信、メッセージ「トランザクションをインポートできません」が失敗しました これを解決するにはどうすればでしょうか。  
  
 **A:** これには、次の理由が考えられます。  
  
-   ドメイン モードの場合、リモート トランザクション受信には、Microsoft 分散トランザクション コーディネーター (MSDTC) ネットワーク アクセスが必要です。 できるようにこれを使用して**コンポーネントの追加/削除**します。  
  
     ![有効にするかを示すスクリーン ショット ネットワーク DTC アクセスします。](./media/troubleshooting-queued-messaging/enable-distributed-transaction-coordinator-access.jpg)  
  
-   トランザクション マネージャーと通信するための認証モードを確認します。 ワークグループ モードの場合は、「認証が必要な」を選択する必要があります。 ドメイン モードの場合は、「相互認証が必要です」を選択する必要があります。  
  
     ![XA トランザクションを有効にする](../../../../docs/framework/wcf/feature-details/media/4f3695e0-fb0b-4c5b-afac-75f8860d2bb0.jpg "4f3695e0-fb0b-4c5b-afac-75f8860d2bb0")  
  
-   MSDTC が内の例外の一覧であることを確認、**インターネット接続ファイアウォール**設定します。  
  
-   [!INCLUDE[wv](../../../../includes/wv-md.md)] を使用していることを確認します。 [!INCLUDE[wv](../../../../includes/wv-md.md)] 上の MSMQ は、リモート トランザクション読み取りをサポートします。 以前の Windows リリース上の MSMQ は、リモート トランザクション読み取りをサポートしません。  
  
 **Q:** キューから読み取るサービスは、ネットワーク サービスでなど、Web でホスト、アクセス拒否例外が発生する理由が発生します、キューから読み取るときにでしょうか。  
  
 **A:** ネットワーク サービス読み取りアクセスは、キューのネットワーク サービスは、キューから読み取れるようにする ACL に追加する必要があります。  
  
 **Q:** MSMQ アクティベーション サービスを使用してリモート コンピューター上のキュー内のメッセージに基づいてアプリケーションをアクティブ化できますか。  
  
 **A:** はい。 これには、ネットワーク サービスとして動作するように MSMQ アクティベーション サービスを構成し、リモート コンピューター上のキューへのネットワーク サービス アクセスを追加する必要があります。  
  
## <a name="using-custom-msmq-bindings-with-receivecontext-enabled"></a>ReceiveContext を有効にしたカスタム MSMQ バインディングの使用  
 <xref:System.ServiceModel.Channels.ReceiveContext> を有効にしてカスタム MSMQ バインディングを使用すると、ネイティブの MSMQ が非同期の <xref:System.ServiceModel.Channels.ReceiveContext> 受信の I/O 完了をサポートしないために、着信メッセージの処理にスレッド プール内のスレッドが使用されます。 これは、このようなメッセージの処理に <xref:System.ServiceModel.Channels.ReceiveContext> の内部トランザクションが使用され、MSMQ が非同期処理をサポートしないためです。 この問題を回避するには、<xref:System.ServiceModel.Description.SynchronousReceiveBehavior> をエンドポイントに追加して同期処理を強制するか、<xref:System.ServiceModel.Description.DispatcherSynchronizationBehavior.MaxPendingReceives%2A> を 1 に設定します。
