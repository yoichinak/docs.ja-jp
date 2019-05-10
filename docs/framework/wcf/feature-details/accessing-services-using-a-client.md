---
title: クライアントを使用したサービスへのアクセス
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c8329832-bf66-4064-9034-bf39f153fc2d
ms.openlocfilehash: 9a38ec444c51560cab48db1b39ae331f728fba30
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2019
ms.locfileid: "64635668"
---
# <a name="accessing-services-using-a-client"></a>クライアントを使用したサービスへのアクセス
クライアント アプリケーションは、作成、構成、およびサービスと通信する WCF クライアントまたはチャネル オブジェクトを使用する必要があります。 [WCF Client Overview](../../../../docs/framework/wcf/wcf-client-overview.md)トピックでは、オブジェクトと基本的なクライアントやチャネル オブジェクトを作成すると、それらを使用して必要な手順の概要を説明します。  
  
 このトピックでは、ユーザーのシナリオに応じて役立つ、クライアント アプリケーション、クライアント オブジェクト、およびチャネル オブジェクトに関するいくつかの問題について詳しく説明します。  
  
## <a name="overview"></a>概要  
 ここでは、以下の項目に関連する動作と問題について説明します。  
  
- チャネルとセッションの有効期間  
  
- 例外処理  
  
- ブロックの問題について  
  
- 対話方式によるチャネルの初期化  
  
### <a name="channel-and-session-lifetimes"></a>チャネルとセッションの有効期間  
 Windows Communication Foundation (WCF) アプリケーションには、データグラム チャネルとセッションフル チャネルの 2 つのカテゴリが含まれています。  
  
 A*データグラム*チャネルは、チャネルをすべてのメッセージは相関されません。 データグラム チャネルでは、入出力操作が失敗しても、通常、次の操作は影響を受けないので、同じチャネルの再利用が可能です。 したがって、通常、データグラム チャネルは失敗になりません。  
  
 *セッションの多い*チャンネル、ただし、他のエンドポイントへの接続を使用したチャネルとは。 一方のセッション内のメッセージは、他方の同じセッションと常に関連付けられています。 さらに、セッションが成功したとみなされるためには、セッションの両参加要素が、メッセージ交換要件が満たされたということに同意する必要があります。 両参加要素が同意できない場合、セッション チャネルは失敗になる場合があります。  
  
 クライアントを明示的に開く場合も暗黙的に開く場合も、最初の操作を呼び出します。  
  
> [!NOTE]
>  一般的に、障害が生じたセッションフル チャネルを明示的に検出することは有用ではありません。通知されるタイミングがセッションの実装により異なるためです。 たとえば、<xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> (信頼できるセッションは無効) では TCP 接続のセッションが表面に出るため、サービスまたはクライアントで <xref:System.ServiceModel.ICommunicationObject.Faulted?displayProperty=nameWithType> イベントをリッスンしていれば、ネットワーク エラーが発生すると直ちに通知される可能性があります。 一方、信頼できるセッション (<xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> を有効化したバインディングにより確立される) は、サービスが小さなネットワーク エラーから分離されるように設計されています。 妥当な期間内にセッションの再確立が可能な場合、信頼できるセッション用に構成された、この同じバインディングは、中断が長期間発生し続けるまでエラーにならない場合があります。  
  
 アプリケーション層にチャネルを公開するほとんどのシステム提供のバインディングでは、既定でセッションが使用されますが、<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType> では使用されません。 詳細については、次を参照してください。[を使用してセッション](../../../../docs/framework/wcf/using-sessions.md)します。  
  
### <a name="the-proper-use-of-sessions"></a>セッションの適切な使用  
 セッションを使用すると、メッセージ交換全体が完了したかどうか、そしてメッセージ交換が成功したと両側が見なしたかどうかを認識できます。 呼び出し側のアプリケーションでは、チャネルを開き、使用して、閉じるまでを 1 つの try ブロック内で処理することをお勧めします。 セッション チャネルが開いているときに、<xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> メソッドを 1 回呼び出して、その呼び出しが正常に返された場合、セッションは成功しています。 この場合の成功とは、バインディングにより指定されているすべての配信保証が満たされ、もう一方の側では <xref:System.ServiceModel.ICommunicationObject.Abort%2A?displayProperty=nameWithType> を呼び出す前にチャネルに対して <xref:System.ServiceModel.ICommunicationObject.Close%2A> を呼び出さなかったことを意味します。  
  
 次のセクションで、このクライアントによる方法の例を示します。  
  
### <a name="handling-exceptions"></a>例外処理  
 クライアント アプリケーションで例外を処理することは簡単です。 try ブロック内部でチャネルを開き、使用して、閉じた場合、例外がスローされない限り、メッセージ交換は正常に行われています。 通常、例外がスローされた場合は、メッセージ交換が中止されます。  
  
> [!NOTE]
>  使用、`using`ステートメント (`Using` Visual Basic で) は推奨されません。 その理由は、`using` ステートメントの最後で例外が発生し、認識する必要のある他の例外がマスクされる可能性があるためです。 詳細については、次を参照してください。[使用終了、中止 WCF クライアントのリソースを解放する](../../../../docs/framework/wcf/samples/use-close-abort-release-wcf-client-resources.md)します。  
  
 次のコード例は、`using` 文ではなく try/catch ブロックを使用する、推奨されるクライアント パターンを示しています。  
  
 [!code-csharp[FaultContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/client.cs#3)]
 [!code-vb[FaultContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/client.vb#3)]  
  
> [!NOTE]
>  <xref:System.ServiceModel.ICommunicationObject.State%2A?displayProperty=nameWithType> プロパティの値を確認すると競合状態になるので、チャネルを再利用するかどうか、またはチャネルを閉じるかどうかを決定するのにこの値を確認することは推奨されません。  
  
 データグラム チャネルを閉じるときに例外が発生しても、データグラム チャネルはエラーになりません。 さらに、非双方向クライアントがセキュリティで保護されたメッセージ交換を使用して認証に失敗した場合、通常、<xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType> がスローされます。 しかし、双方向クライアントがセキュリティで保護されたメッセージ交換を使用して認証に失敗した場合、クライアントは代わりに <xref:System.TimeoutException?displayProperty=nameWithType> を受信します。  
  
 アプリケーション レベルのエラー情報が作業の詳細については、次を参照してください。[を指定すると処理のエラー コントラクトおよびサービスの](../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)します。 [予期される例外](../../../../docs/framework/wcf/samples/expected-exceptions.md)予期される例外を説明し、それらを処理する方法を示しています。 チャネル開発時にエラーを処理する方法の詳細については、次を参照してください。[例外の処理とエラー](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)します。  
  
### <a name="client-blocking-and-performance"></a>クライアントのブロックとパフォーマンス  
 アプリケーションが要求/応答操作を同期的に呼び出す場合、戻り値が受信されるか例外 (<xref:System.TimeoutException?displayProperty=nameWithType> など) がスローされるまで、クライアントはブロックされます。 この動作はローカルの動作と似ています。 アプリケーションは、WCF クライアント オブジェクトまたはチャンネルに対する操作を同期的に起動、ネットワークまたは例外がスローされるまで、チャネル層でデータを書き込むことができますになるまで、クライアントは返しません。 また、一方向メッセージ交換パターン (<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A?displayProperty=nameWithType> が `true` に設定された操作をマークすることで指定される) では、クライアントの応答性が向上する可能性がありますが、バインディングや送信済みのメッセージによっては、一方向操作でもブロックが生じる場合があります。 一方向操作とはメッセージ交換のみを指しています。 詳細については、次を参照してください。[一方向サービス](../../../../docs/framework/wcf/feature-details/one-way-services.md)します。  
  
 メッセージ交換パターンに関係なく、大規模データのチャンクによりクライアント処理が遅延する場合があります。 これらの問題を処理する方法については、次を参照してください。 [Large Data and Streaming](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)します。  
  
 場合は、アプリケーションは、操作が完了するまでより多くの作業を行う必要がありますは、WCF クライアントを実装するサービス コントラクト インターフェイスに非同期メソッド ペアを作成します。 これを行う最も簡単な方法が使用するには、`/async`スイッチ、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)します。 例については、「[方法: サービス操作を非同期的に呼び出す](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)します。  
  
 クライアントのパフォーマンス向上の詳細については、次を参照してください。[中間層クライアント アプリケーション](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)します。  
  
### <a name="enabling-the-user-to-select-credentials-dynamically"></a>ユーザーによる資格情報の動的選択の有効化  
 <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> インターフェイスを使用すると、アプリケーションによりユーザー インターフェイスが表示され、ユーザーが資格情報を選択できるようになります。この資格情報は、タイムアウト タイマーが開始される前に、チャネルの作成に使用されます。  
  
 アプリケーション開発者は、挿入された <xref:System.ServiceModel.Dispatcher.IInteractiveChannelInitializer> を 2 つの方法で利用できます。 クライアント アプリケーションは、いずれかを呼び出すことができます<xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType>または<xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType>(または非同期バージョン)、チャネルを開く前に (、*明示的な*アプローチ) や、最初の操作の呼び出し (、*暗黙的な*アプローチ)。  
  
 暗黙的方法を使用する場合、アプリケーションは最初の操作を <xref:System.ServiceModel.ClientBase%601> または <xref:System.ServiceModel.IClientChannel> 拡張に対して呼び出す必要があります。 アプリケーションが最初の操作以外の何かを呼び出した場合、例外がスローされます。  
  
 明示的方法を使用する場合、アプリケーションで次の手順を順番に実行する必要があります。  
  
1. <xref:System.ServiceModel.ClientBase%601.DisplayInitializationUI%2A?displayProperty=nameWithType> または <xref:System.ServiceModel.IClientChannel.DisplayInitializationUI%2A?displayProperty=nameWithType> (または非同期バージョン) を呼び出します。  
  
2. 初期化子が返された場合は、<xref:System.ServiceModel.ICommunicationObject.Open%2A> オブジェクトまたは <xref:System.ServiceModel.IClientChannel> プロパティで返された <xref:System.ServiceModel.IClientChannel> オブジェクトの <xref:System.ServiceModel.ClientBase%601.InnerChannel%2A?displayProperty=nameWithType> メソッドを呼び出します。  
  
3. 操作を呼び出します。  
  
 製品品質のアプリケーションでは、明示的な方法を採用することによってユーザー インターフェイスのプロセスを制御することをお勧めします。  
  
 暗黙的な方法を使用するアプリケーションでは、ユーザー インターフェイス初期化子が呼び出されますが、このアプリケーションのユーザーがバインディングの送信タイムアウト期間内に応答できない場合、ユーザー インターフェイスが復帰すると例外がスローされます。  
  
## <a name="see-also"></a>関連項目

- [双方向サービス](../../../../docs/framework/wcf/feature-details/duplex-services.md)
- [方法: 一方向のサービスにアクセスし、要求/応答コントラクト](../../../../docs/framework/wcf/feature-details/how-to-access-wcf-services-with-one-way-and-request-reply-contracts.md)
- [方法: Access Services と双方向コントラクト](../../../../docs/framework/wcf/feature-details/how-to-access-services-with-a-duplex-contract.md)
- [方法: WSE 3.0 にアクセス サービス](../../../../docs/framework/wcf/feature-details/how-to-access-a-wse-3-0-service-with-a-wcf-client.md)
- [方法: ChannelFactory を使用します。](../../../../docs/framework/wcf/feature-details/how-to-use-the-channelfactory.md)
- [方法: サービス操作を非同期的に呼び出す](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md)
- [中間層クライアント アプリケーション](../../../../docs/framework/wcf/feature-details/middle-tier-client-applications.md)
