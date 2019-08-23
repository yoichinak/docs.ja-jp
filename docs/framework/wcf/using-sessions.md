---
title: セッションの使用
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sessions [WCF]
ms.assetid: 864ba12f-3331-4359-a359-6d6d387f1035
ms.openlocfilehash: 671e650a494d314ec1da1957eaae91e2d1811213
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952837"
---
# <a name="using-sessions"></a>セッションの使用
Windows Communication Foundation (WCF) アプリケーションでは、*セッション*によってメッセージのグループがメッセージ交換に関連付けられます。 WCF セッションは、ASP.NET アプリケーションで使用できるセッションオブジェクトとは異なり、さまざまな動作をサポートし、さまざまな方法で制御できます。 このトピックでは、WCF アプリケーションでセッションが有効にする機能とその使用方法について説明します。  
  
## <a name="sessions-in-windows-communication-foundation-applications"></a>Windows Communication Foundation アプリケーションのセッション  
 サービス コントラクトでセッションが必要であると指定されている場合、すべての呼び出し (つまり、呼び出しをサポートする基本的なメッセージ交換) を同じメッセージ交換の一部にする必要があります。 セッションが許可されるが必須ではないコントラクトの場合、クライアントは、接続した後にセッションを確立できます。また、セッションを確立しないままにしておくこともできます。 セッションが終了したのに、同じチャネルでメッセージが送信されると、例外がスローされます。  
  
 WCF セッションには、次の主要な概念機能があります。  
  
- 呼び出し側アプリケーション (WCF クライアント) によって明示的に開始および終了される。  
  
- セッション中に配信されたメッセージは、受信された順に処理される。  
  
- セッションはメッセージのグループを相互に関連付けて通信を行う。 関連付けにはさまざまな種類があります。 たとえば、あるセッション ベースのチャネルでは、共有ネットワーク接続に基づいてメッセージが相互に関連付けられる一方、別のセッション ベースのチャネルでは、メッセージ本文にある共有タグに基づいてメッセージが相互に関連付けられます。 セッションから派生可能な機能は、相互関連付けの性質によって異なります。  
  
- WCF セッションに関連付けられている一般的なデータストアはありません。  
  
 ASP.NET アプリケーションの<xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType>クラスと、そのクラスによって提供される機能に精通している場合は、そのようなセッションと WCF セッションの間に次の違いがあることがわかります。  
  
- ASP.NET セッションは常にサーバーによって開始されます。  
  
- ASP.NET セッションは暗黙的に順序付けされていません。  
  
- ASP.NET セッションでは、複数の要求にわたって一般的なデータストレージメカニズムが提供します。  
  
 このトピックでは、次の項目について説明します。  
  
- サービス モデル レイヤーにおいてセッション ベースのバインディングを使用する場合の既定の実行動作。  
  
- WCF セッションベースのシステム指定のバインディングによって提供される機能の種類。  
  
- セッションの要件を宣言するコントラクトの作成方法。  
  
- セッションの作成と終了、およびセッションとサービス インスタンスの関係を理解し、制御する方法。  
  
## <a name="default-execution-behavior-using-sessions"></a>セッションを使用した既定の実行動作  
 セッションの開始を試みるバインディングは、 *セッション ベース* のバインディングと呼ばれます。 サービス コントラクトで、セッション ベースのバインディングを要求、許可、または拒否するように指定するときは、サービス コントラクト インターフェイス (またはクラス) の <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> プロパティを <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> 列挙値に設定します。 既定では、このプロパティの値は<xref:System.ServiceModel.SessionMode.Allowed>です。つまり、クライアントが WCF サービス実装でセッションベースのバインディングを使用する場合、サービスは提供されたセッションを確立して使用します。  
  
 WCF サービスがクライアントセッションを受け入れると、既定では次の機能が有効になります。  
  
1. WCF クライアントオブジェクト間のすべての呼び出しは、同じサービスインスタンスによって処理されます。  
  
2. さまざまなセッション ベースのバインディングによって追加機能が提供されます。  
  
## <a name="system-provided-session-types"></a>システム指定のセッションの種類  
 セッション ベースのバインディングは、サービス インスタンスと特定のセッションとの既定の関連付けをサポートします。 ただし、前のセッション ベースのインスタンス化制御を有効にすることに加えて、セッション ベースのバインディングごとにサポートされる機能も異なります。  
  
 WCF には、次の種類のセッションベースのアプリケーション動作が用意されています。  
  
- 2 者間の通信で特定のセキュリティ保護されたメッセージ交換について両者の合意が成立している場合、 <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType> は、セキュリティ ベースのセッションをサポートします。 詳細については、「[サービスのセキュリティ保護](../../../docs/framework/wcf/securing-services.md)」を参照してください。 たとえば、セキュリティ セッションと信頼できるセッションの両方のサポートを含む <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType> バインディングは、既定では、メッセージを暗号化してデジタル署名を行うセキュリティで保護されたセッションのみを使用します。  
  
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType> バインディングは、TCP/IP ベースのセッションをサポートしており、すべてのメッセージがソケット レベルの接続によって関連付けられます。  
  
- WS-ReliableMessaging 仕様を実装する <xref:System.ServiceModel.Channels.ReliableSessionBindingElement?displayProperty=nameWithType> 要素は、メッセージを順番に 1 回だけ配信するように構成できる、信頼できるセッションをサポートします。これにより、メッセージ交換時にメッセージが複数のノードを通過する場合でもメッセージが受信されます。 詳細については、「[信頼できるセッション](../../../docs/framework/wcf/feature-details/reliable-sessions.md)」を参照してください。  
  
- <xref:System.ServiceModel.NetMsmqBinding?displayProperty=nameWithType> バインディングは、MSMQ データグラム セッションを提供します。 詳細については、「 [WCF のキュー](../../../docs/framework/wcf/feature-details/queues-in-wcf.md)」を参照してください。  
  
 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> プロパティを設定しても、コントラクトが必要とするセッションの種類は指定されず、コントラクトがセッションを必要とすることだけが指定されます。  
  
## <a name="creating-a-contract-that-requires-a-session"></a>セッションを必要とするコントラクトの作成  
 セッションを必要とするコントラクトを作成するのは、サービス コントラクトで宣言する操作のグループをすべて同じセッション内で実行し、メッセージを順番に配信する必要がある場合です。 サービス コントラクトが必要とするセッションのサポート レベルをアサートするには、サービス コントラクト インターフェイスまたはクラスの <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> プロパティを <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> 列挙値に設定して以下を指定します。  
  
- コントラクトがセッションを必要とするかどうか。  
  
- コントラクトで、クライアントによるセッションの確立を許可するかどうか。  
  
- コントラクトでセッションを禁止するかどうか。  
  
 ただし、 <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A> プロパティを設定しても、コントラクトが必要とするセッション ベースの動作の種類は指定されません。 このメソッドは、サービスの構成済みバインディング (通信チャネルを作成する) がサービスの実装時にセッションを確立するかどうかを確認するように WCF に指示します。 ここでもバインディングは、選択する任意の種類のセッション ベースの動作 (セキュリティ セッション、トランスポート セッション、信頼できるセッション、またはこれらの一定の組み合わせ) によってこの要件を満たすことができます。 正確な動作は、選択した <xref:System.ServiceModel.SessionMode?displayProperty=nameWithType> 値によって決まります。 サービスの構成済みバインディングが <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A>の値に一致しない場合は、例外がスローされます。 セッションをサポートするバインディングと、それが作成するチャネルは、セッション ベースのバインディングまたはチャネルと呼ばれます。  
  
 次のサービス コントラクトは、 `ICalculatorSession` のすべての操作をセッション内で交換する必要があることを指定しています。 `Equals` メソッドを除き、どの操作も呼び出し元に値を返しません。 ただし、 `Equals` メソッドはパラメーターを受け取らないため、データが既に他の操作に渡されているセッション内では、ゼロ以外の値しか返すことができません。 このコントラクトでは、セッションが正常に機能する必要があります。 特定のクライアントに関連付けられているセッションがないと、サービス インスタンスは、そのクライアントが以前に送信したデータを知ることができません。  
  
 [!code-csharp[S_Service_Session#1](../../../samples/snippets/csharp/VS_Snippets_CFX/s_service_session/cs/service.cs#1)]
 [!code-vb[S_Service_Session#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_service_session/vb/service.vb#1)]  
  
 サービスがセッションを許可した場合は、クライアントがセッションを開始するとセッションが確立され、使用されますが、許可しない場合は、セッションが確立されません。  
  
## <a name="sessions-and-service-instances"></a>セッションとサービス インスタンス  
 WCF で既定のインスタンス化動作を使用する場合、WCF クライアントオブジェクト間のすべての呼び出しは、同じサービスインスタンスによって処理されます。 そのため、アプリケーション レベルでは、セッションは、ローカル呼び出し動作と同様のアプリケーション動作を有効にすると考えることができます。 たとえば、ローカル オブジェクトを作成するときは、次のような流れになります。  
  
- コンストラクターが呼び出されます。  
  
- WCF クライアントオブジェクト参照に対する後続の呼び出しは、すべて同じオブジェクトインスタンスによって処理されます。  
  
- オブジェクト参照が破棄されると、デストラクターが呼び出されます。  
  
 既定のサービス インスタンス動作を使用している限り、セッションでは、クライアントとサービス間で同様の動作が有効になります。 サービス コントラクトがセッションを必要としたり、サポートしたりする場合は、 <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A> プロパティと <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A> プロパティを設定することで、1 つ以上のコントラクト操作をセッションの開始または終了としてマークできます。  
  
 *開始操作* は、新しいセッションの最初の操作として呼び出す必要がある操作です。 開始操作以外の操作は、少なくとも 1 つの開始操作が呼び出された後にしか呼び出すことはできません。 そのため、サービス インスタンスの開始に適した入力をクライアントから取得するように設計された開始操作を宣言することで、サービスに対する一種のセッション コンストラクターを作成できます (ただし、状態はセッションに関連付けられ、サービス オブジェクトに関連付けられません)。  
  
 *終了操作*は、開始操作とは逆に、既存のセッションの最終メッセージとして呼び出す必要がある操作です。 既定では、WCF は、サービスが関連付けられているセッションが閉じられた後に、サービス オブジェクトとそのコンテキストを再利用します。 そのため、サービス インスタンスの終了に適した関数を実行するように設計された終了操作を宣言することで、一種のデストラクターを作成できます。  
  
> [!NOTE]
> 既定の動作は、ローカルのコンストラクターとデストラクターに似ていますが、あくまで似ているだけです。 すべての WCF サービス操作は、開始または終了操作、またはその両方を同時に実行できます。 さらに既定では、開始操作は、任意の順序で何回でも呼び出すことができます。そのため、 <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType> オブジェクトを操作することでサービス インスタンスの有効期間を明示的に制御しない限り、セッションが確立されインスタンスに関連付けられた後に、追加セッションは作成されません。 また、状態はセッションに関連付けられ、サービス オブジェクトには関連付けられません。  
  
 たとえば`ICalculatorSession` 、前の例で使用したコントラクトでは、wcf クライアントオブジェクトは、他`Clear`の操作の前に最初に操作を呼び出し、次の wcf クライアントオブジェクトとのセッションは、を呼び出すときに終了する必要があります。`Equals`操作。 次のコード例は、この要件を強制的に適用するコントラクトを示しています。 セッションを開始するにはまず`Clear` を呼び出す必要があります。 `Equals` を呼び出すとセッションが終了します。  
  
 [!code-csharp[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/csharp/VS_Snippets_CFX/sca.isinitiatingisterminating/cs/service.cs#1)]
 [!code-vb[SCA.IsInitiatingIsTerminating#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/sca.isinitiatingisterminating/vb/service.vb#1)]  
  
 サービスは、クライアントとのセッションを開始しません。 WCF クライアントアプリケーションでは、セッションベースのチャネルの有効期間とセッション自体の有効期間の間に直接的な関係が存在します。 そのため、クライアントは、新しいセッション ベースのチャネルを作成することによって新しいセッションを作成し、セッション ベースのチャネルを正常に閉じることによって、既存のセッションを破棄します。 クライアントは、次のいずれかを呼び出してサービス エンドポイントとのセッションを開始します。  
  
- <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> の呼び出しによって返されるチャネルの <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>。  
  
- <xref:System.ServiceModel.ClientBase%601.Open%2A?displayProperty=nameWithType>[ServiceModel メタデータユーティリティツール (svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)によって生成される WCF クライアントオブジェクト。  
  
- どちらの種類の WCF クライアントオブジェクトの開始操作 (既定では、すべての操作が開始されます)。 最初の操作が呼び出されると、WCF クライアントオブジェクトは自動的にチャネルを開き、セッションを開始します。  
  
 通常は、クライアントが次のいずれかを呼び出して、サービス エンドポイントとのセッションを終了します。  
  
- <xref:System.ServiceModel.ICommunicationObject.Close%2A?displayProperty=nameWithType> の呼び出しによって返されるチャネルの <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType>。  
  
- <xref:System.ServiceModel.ClientBase%601.Close%2A?displayProperty=nameWithType>Svcutil.exe によって生成される WCF クライアントオブジェクト。  
  
- どちらの種類の WCF クライアントオブジェクトに対しても終了操作 (既定では、操作は終了しません。コントラクトは、終了操作を明示的に指定する必要があります)。 最初の操作が呼び出されると、WCF クライアントオブジェクトは自動的にチャネルを開き、セッションを開始します。  
  
 たとえば、「[方法:[既定のサービス動作](../../../docs/framework/wcf/samples/default-service-behavior.md)と[インスタンス](../../../docs/framework/wcf/samples/instancing.md)化のサンプルだけでなく、セッション](../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)を必要とするサービスを作成します。  
  
 クライアントとセッションの詳細については、「 [WCF クライアントを使用したサービスへのアクセス](../../../docs/framework/wcf/feature-details/accessing-services-using-a-client.md)」を参照してください。  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>InstanceContext 設定と対話するセッション  
 コントラクト内の <xref:System.ServiceModel.SessionMode> 列挙と、チャネルと特定のサービス オブジェクト間の関連付けを制御する <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> プロパティの間には相互作用があります。 詳細については、「[セッション、インスタンス化、および同時実行](../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)」を参照してください。  
  
### <a name="sharing-instancecontext-objects"></a>InstanceContext オブジェクトの共有  
 ユーザーが自ら関連付けを行うことにより、どの <xref:System.ServiceModel.InstanceContext> オブジェクトに、どのセッション ベースのチャネルまたは呼び出しを関連付けるかを制御することもできます。 
  
## <a name="sessions-and-streaming"></a>セッションとストリーミング  
 大量のデータを転送する場合、WCF のストリーミング転送モードは、メッセージをメモリ内でバッファー処理して処理する既定の動作に代わるものです。 セッション ベースのバインディングでストリーミングを呼び出すと、予期しない動作を引き起こすことがあります。 すべてのストリーミング呼び出しは単一のチャネル (データグラム チャネル) を通じて行われますが、このチャネルは使用されるバインディングがセッションを使用するように構成されている場合であっても、セッションをサポートしません。 セッション ベースのバインディングによって複数のクライアントが同一のサービス オブジェクトに対してストリーミング呼び出しを行う場合、このサービス オブジェクトのコンカレンシー モードが単一に設定され、インスタンス コンテキスト モードが `PerSession` に設定されていると、すべての呼び出しがこのデータグラム チャネルを通過する必要があるため、同時に処理される呼び出しは 1 つに限られることになります。 そのため、1 つ以上のクライアントがタイムアウトとなる可能性があります。サービス オブジェクトの `InstanceContextMode` を `PerCall` に設定するか、またはコンカレンシー モードを複数に設定することで、この問題を回避できます。  
  
> [!NOTE]
> この場合、利用可能になる "セッション" は 1 つしかないため、MaxConcurrentSessions は効力を失います。  
  
## <a name="see-also"></a>関連項目

- <xref:System.ServiceModel.OperationContractAttribute.IsInitiating%2A>
- <xref:System.ServiceModel.OperationContractAttribute.IsTerminating%2A>
