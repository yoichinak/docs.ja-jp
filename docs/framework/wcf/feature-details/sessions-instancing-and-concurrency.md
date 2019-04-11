---
title: セッション、インスタンス化、およびコンカレンシー
ms.date: 03/30/2017
ms.assetid: 50797a3b-7678-44ed-8138-49ac1602f35b
ms.openlocfilehash: 994b95bb8ebc14a9997e1e9510389fdf16098d12
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229070"
---
# <a name="sessions-instancing-and-concurrency"></a>セッション、インスタンス化、およびコンカレンシー
*"セッション"* とは、2 つのエンドポイント間で送信されるすべてのメッセージを相互に関連付けたものです。 *"インスタンス化"* とは、ユーザー定義のサービス オブジェクトとこれらのオブジェクトに関連する <xref:System.ServiceModel.InstanceContext> オブジェクトの有効期間を制御することです。 また、*コンカレンシー*は、<xref:System.ServiceModel.InstanceContext> で同時に実行されるスレッドの数の制御を表す用語です。  
  
 ここでは、これらの設定とその使用方法、各設定間のさまざまな相互作用について説明します。  
  
## <a name="sessions"></a>セッション  
 サービス コントラクトによって <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> プロパティが <xref:System.ServiceModel.SessionMode.Required?displayProperty=nameWithType>に設定されている場合、すべての呼び出し (つまり、呼び出しをサポートする、基になるメッセージ交換) を同じメッセージ交換の一部にする必要があります。 セッションが許可されるが必須ではないコントラクトの場合、クライアントは、接続した後にセッションを確立できます。また、セッションを確立しないままにしておくこともできます。 セッションが終了したのに、同じセッション ベースのチャネルでメッセージが送信されると、例外がスローされます。  
  
 WCF のセッションでは、次の主な概念の機能があります。  
  
-   呼び出し側アプリケーションによって明示的に開始および終了される。  
  
-   セッション中に配信されたメッセージは、受信された順に処理される。  
  
-   セッションはメッセージのグループを相互に関連付けて通信を行う。 ここで "相互に関連付ける" は、抽象的な意味を持ちます。 たとえば、あるセッション ベースのチャネルでは、共有ネットワーク接続に基づいてメッセージが相互に関連付けられる一方、別のセッション ベースのチャネルでは、メッセージ本文にある共有タグに基づいてメッセージが相互に関連付けられます。 セッションから派生可能な機能は、相互関連付けの性質によって異なります。  
  
-   WCF のセッションに関連付けられた一般的なデータ ストアはありません。  
  
 慣れている場合、<xref:System.Web.SessionState.HttpSessionState?displayProperty=nameWithType>クラス[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]アプリケーションと機能を提供、可能性があります、その種のセッションと WCF のセッションの間の次の相違点に注意してください。  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] セッションは常にサーバーによって開始されます。  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] セッションには、暗黙的に順序付けします。  
  
-   [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] セッションは、要求間で、一般的なデータ ストレージ機構を提供します。  
  
 クライアント アプリケーションとサービス アプリケーションでは、異なる方法でセッションと対話します。 クライアント アプリケーションはセッションを開始し、セッション内で送信されてきたメッセージの受信と処理を行います。 サービス アプリケーションでは、動作を追加するための機能拡張ポイントとしてセッションを使用できます。 これは <xref:System.ServiceModel.InstanceContext> を直接操作する、またはカスタムのインスタンス コンテキスト プロバイダーを実装することで可能になります。  
  
## <a name="instancing"></a>"インスタンス化"  
 インスタンス化動作 ( <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> プロパティを使用して設定します) は、受信メッセージに応答して <xref:System.ServiceModel.InstanceContext> を作成する方法を制御します。 既定では、各 <xref:System.ServiceModel.InstanceContext> は 1 つのユーザー定義サービス オブジェクトに関連付けられています。したがって、(既定では) <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> プロパティを設定することによってもユーザー定義サービス オブジェクトのインスタンス化を制御できます。 インスタンス化モードは <xref:System.ServiceModel.InstanceContextMode> 列挙体によって定義されます。  
  
 次のインスタンス化モードを使用できます。  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerCall>:新しい<xref:System.ServiceModel.InstanceContext>(およびサービス オブジェクト) がクライアント要求ごとに作成されます。  
  
-   <xref:System.ServiceModel.InstanceContextMode.PerSession>:新しい<xref:System.ServiceModel.InstanceContext>(およびサービス オブジェクト) が新しいクライアント セッションごとに作成され、(セッションをサポートするバインディングが必要)、そのセッションの有効期間にわたって保持されます。  
  
-   <xref:System.ServiceModel.InstanceContextMode.Single>:1 つ<xref:System.ServiceModel.InstanceContext>(およびサービス オブジェクト)、アプリケーションの有効期間のすべてのクライアント要求を処理します。  
  
 既定の <xref:System.ServiceModel.InstanceContextMode> 値 (サービス クラスで明示的に設定された <xref:System.ServiceModel.InstanceContextMode.PerSession> ) を次のコード例に示します。  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]   
public class CalculatorService : ICalculatorInstance   
{   
    ...  
}  
```  
  
 また、 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> プロパティは <xref:System.ServiceModel.InstanceContext> の解放頻度を制御しますが、 <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> プロパティと <xref:System.ServiceModel.ServiceBehaviorAttribute.ReleaseServiceInstanceOnTransactionComplete%2A?displayProperty=nameWithType> プロパティはサービス オブジェクトの解放時期を制御します。  
  
### <a name="well-known-singleton-services"></a>既知のシングルトン サービス  
 単一インスタンス サービス オブジェクトの 1 つのバリエーションとして、サービス オブジェクトをユーザーが自分で作成し、このオブジェクトを使用してサービス ホストを作成すると有用な場合があります。 そのためには、 <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> プロパティを <xref:System.ServiceModel.InstanceContextMode.Single> に設定するか、サービス ホストが開かれたときに例外をスローする必要があります。  
  
 このようなサービスを作成するには、 <xref:System.ServiceModel.ServiceHost.%23ctor%28System.Object%2CSystem.Uri%5B%5D%29?displayProperty=nameWithType> コンストラクターを使用します。 この方法は、シングルトン サービスが使用する特定のオブジェクト インスタンスを提供する場合に、カスタムの <xref:System.ServiceModel.Dispatcher.IInstanceContextInitializer?displayProperty=nameWithType> を実装する代わりに使用できます。 サービス実装の型を作成することが困難な場合 (たとえば、既定のパラメーターなしのコンストラクターが作成されない場合) は、このオーバーロードを使用できます。  
  
 あるオブジェクトをこのコンス トラクターに指定するとと、いくつか機能の動作をインスタンス化 Windows Communication Foundation (WCF) に関連する動作が異なりますに注意してください。 たとえば、シングルトン オブジェクト インスタンスを指定しているときは、 <xref:System.ServiceModel.InstanceContext.ReleaseServiceInstance%2A?displayProperty=nameWithType> を呼び出しても効果はありません。 他のインスタンス解放機構も、同様に無視されます。 <xref:System.ServiceModel.ServiceHost> は常に、すべての操作について <xref:System.ServiceModel.OperationBehaviorAttribute.ReleaseInstanceMode%2A?displayProperty=nameWithType> プロパティが <xref:System.ServiceModel.ReleaseInstanceMode.None?displayProperty=nameWithType> に設定されているかのように動作します。  
  
### <a name="sharing-instancecontext-objects"></a>InstanceContext オブジェクトの共有  
 ユーザーが自ら関連付けを行うことにより、どの <xref:System.ServiceModel.InstanceContext> オブジェクトに、どのセッションフル チャネルまたは呼び出しを関連付けるかを制御することもできます。  
  
## <a name="concurrency"></a>コンカレンシー  
 コンカレンシーは、<xref:System.ServiceModel.InstanceContext> 内で同時にアクティブになるスレッドの数を制御します。 同時実行を制御するには、 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A?displayProperty=nameWithType> と <xref:System.ServiceModel.ConcurrencyMode> 列挙値を使用します。  
  
 選択可能なコンカレンシー モードは次の 3 つです。  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Single>:各インスタンス コンテキストは、一度にインスタンス コンテキスト内でメッセージを処理する 1 つのスレッドの最大値で許可されています。 他のスレッドは、最初のスレッドがインスタンス コンテキストを使用し終えるまで、同じインスタンス コンテキストを使用できません。  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Multiple>:各サービス インスタンスは、メッセージの処理を同時に複数のスレッドを持つことができます。 このコンカレンシー モードを使用するには、サービスの実装がスレッドセーフである必要があります。  
  
-   <xref:System.ServiceModel.ConcurrencyMode.Reentrant>:各サービス インスタンスは、一度に 1 つのメッセージの処理が再入操作の呼び出しを受け入れます。 サービスは、WCF クライアント オブジェクトを通じて呼び出しが場合にのみ、これらの呼び出しを受け入れます。  
  
> [!NOTE]
>  複数のスレッドを安全に使用するコードを理解し、適切に記述することが困難な場合もあります。 <xref:System.ServiceModel.ConcurrencyMode.Multiple> 値や <xref:System.ServiceModel.ConcurrencyMode.Reentrant> 値を使用する前に、これらのモード用にサービスが適切に設計されていることを確認してください。 詳細については、「 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 」を参照してください。  
  
 コンカレンシーの使用は、インスタンス化モードに関連します。 <xref:System.ServiceModel.InstanceContextMode.PerCall>インスタンス化すると、同時実行制御ですが、新しいによって各メッセージが処理されるため<xref:System.ServiceModel.InstanceContext>、そのため、何回も 1 つのスレッドがアクティブにし、<xref:System.ServiceModel.InstanceContext>します。  
  
 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> プロパティを <xref:System.ServiceModel.ConcurrencyMode.Multiple>に設定するコード例を次に示します。  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]   
public class CalculatorService : ICalculatorConcurrency   
{   
    ...  
}  
```  
  
## <a name="sessions-interact-with-instancecontext-settings"></a>InstanceContext 設定と対話するセッション  
 セッションと <xref:System.ServiceModel.InstanceContext> は、コントラクト内の <xref:System.ServiceModel.SessionMode> 列挙値と、チャネルと特定のサービス オブジェクト間の関連付けを制御するサービス実装の <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> プロパティ値の組み合わせに応じて、相互に作用します。  
  
 サービスの <xref:System.ServiceModel.ServiceContractAttribute.SessionMode%2A?displayProperty=nameWithType> プロパティと <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A?displayProperty=nameWithType> プロパティの値の組み合わせが指定されているという条件で、セッションをサポートしている受信チャネルまたはサポートしていない受信チャネルの結果を次の表に示します。  
  
|InstanceContextMode 値|<xref:System.ServiceModel.SessionMode.Required>|<xref:System.ServiceModel.SessionMode.Allowed>|<xref:System.ServiceModel.SessionMode.NotAllowed>|  
|-------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|  
|PerCall|-セッションフル チャネルでの動作:セッションと<xref:System.ServiceModel.InstanceContext>呼び出しごとにします。<br />-セッションレス チャネルでの動作:例外がスローされる。|-セッションフル チャネルでの動作:セッションと<xref:System.ServiceModel.InstanceContext>呼び出しごとにします。<br />-セッションレス チャネルでの動作:<xref:System.ServiceModel.InstanceContext>呼び出しごとにします。|-セッションフル チャネルでの動作:例外がスローされる。<br />-セッションレス チャネルでの動作:<xref:System.ServiceModel.InstanceContext>呼び出しごとにします。|  
|PerSession|-セッションフル チャネルでの動作:セッションと<xref:System.ServiceModel.InstanceContext>各チャネルにします。<br />-セッションレス チャネルでの動作:例外がスローされる。|-セッションフル チャネルでの動作:セッションと<xref:System.ServiceModel.InstanceContext>各チャネルにします。<br />-セッションレス チャネルでの動作:<xref:System.ServiceModel.InstanceContext>呼び出しごとにします。|-セッションフル チャネルでの動作:例外がスローされる。<br />-セッションレス チャネルでの動作:<xref:System.ServiceModel.InstanceContext>呼び出しごとにします。|  
|Single|-セッションフル チャネルでの動作:セッションと 1 つ<xref:System.ServiceModel.InstanceContext>すべての呼び出し。<br />-セッションレス チャネルでの動作:例外がスローされる。|-セッションフル チャネルでの動作:セッションと<xref:System.ServiceModel.InstanceContext>作成された、またはユーザー指定のシングルトン。<br />-セッションレス チャネルでの動作:<xref:System.ServiceModel.InstanceContext>作成された、またはユーザー指定のシングルトン。|-セッションフル チャネルでの動作:例外がスローされる。<br />-セッションレス チャネルでの動作:<xref:System.ServiceModel.InstanceContext>各作成したシングルトンまたはユーザー指定のシングルトン。|  
  
## <a name="see-also"></a>関連項目

- [セッションの使用](../../../../docs/framework/wcf/using-sessions.md)
- [方法: セッションを必要とするサービスを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-service-that-requires-sessions.md)
- [方法: サービスのインスタンス化を制御する](../../../../docs/framework/wcf/feature-details/how-to-control-service-instancing.md)
- [コンカレンシー](../../../../docs/framework/wcf/samples/concurrency.md)
- ["インスタンス化"](../../../../docs/framework/wcf/samples/instancing.md)
- [セッション](../../../../docs/framework/wcf/samples/session.md)
