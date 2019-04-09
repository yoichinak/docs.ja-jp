---
title: 転送
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: 8263093944cf01a38a49b52d71f7a6e54195a3c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145042"
---
# <a name="transfer"></a>転送
このトピックでは、Windows Communication Foundation (WCF) のアクティビティ トレース モデルでの転送について説明します。  
  
## <a name="transfer-definition"></a>転送の定義  
 アクティビティ間の転送は、エンドポイント内の関連アクティビティで発生したイベント間の因果関係を表します。 制御が 2 つのアクティビティ間を流れる場合 (アクティビティの境界を越えたメソッド呼び出しなど)、転送によってこれらのアクティビティが関連付けられます。 WCF では、バイトは、サービスで受信したときに、"リッスン"アクティビティに転送されますバイトを受信アクティビティ メッセージ オブジェクトが作成される場所。 エンド ツー エンドのトレースのシナリオ、および個々 のアクティビティとトレース デザインについては、次を参照してください。[エンド ツー エンドのトレースのシナリオ](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)します。  
  
 転送トレースを出力するには、次の構成コードのように、トレース ソースに `ActivityTracing` を設定します。  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a>転送を使用したエンドポイント内でのアクティビティの関連付け  
 アクティビティと転送により、ユーザーはエラーの根本原因をほぼ突き止めることができます。 たとえば、コンポーネント M と N のアクティビティ M と N の間で、M から N および N から M への転送を行い、M への転送の直後に N でクラッシュが発生した場合、N から M にデータを返したことが原因でクラッシュが発生した可能性があるという結論を下すことができます。  
  
 アクティビティ M とアクティビティ N の間に制御のフローが存在する場合、転送トレースは M から N に出力されます。たとえば、メソッド呼び出しがアクティビティの境界を越えるため、N が M に代わって何らかの処理を実行するとします。 N は既に存在する場合もあれば、作成されている場合もあります。 N が、M に代わって何らかの処理を実行する新しいアクティビティである場合、N は M によって発生します。  
  
 M から N への転送の後に、N から M に転送することはできません。これは、M は N で処理を発生させることはできますが、N がその処理をいつ完了するかまでは追跡しないからです。 実際、N がタスクを完了する前に M が終了する場合があります。 これは、リスナーのアクティビティ (N) を生成し、終了する"ServiceHost を開く"アクティビティ (M) で行われます。 N から M への転送は、N が M に関連する処理を完了したことを意味します。  
  
 N は、M に関連しない他の処理を引き続き実行できます。たとえば、既存の認証システム アクティビティ (N) は、さまざまなログイン アクティビティからのログイン要求 (M) を受信し続けることができます。  
  
 アクティビティ M と N の間に、入れ子のリレーションシップが必ずしも存在するわけではありません。入れ子のリレーションシップが存在しない状況が発生する原因として、2 つのケースが考えられます。 1 つは、アクティビティ M が アクティビティ N を開始したが、N で実行される実際の処理を M が監視しない場合です。もう 1 つは、N が既に存在する場合です。  
  
## <a name="example-of-transfers"></a>転送の例  
 転送の 2 つの例を次に示します。  
  
-   サービス ホストの作成時に、コンストラクターは呼び出し元のコードから制御を取得します。つまり、呼び出し元のコードがコンストラクターに転送されます。 コンストラクターは、必要な処理を終えると、呼び出し元に制御を返します。つまり、コンストラクターから呼び出し元への逆転送が起こります。 これは、入れ子になったリレーションシップの例です。  
  
-   リスナーはトランスポート データの処理を開始するときに、新しいスレッドを作成し、"バイトを受信" アクティビティに、処理の適切なコンテキストとして制御とデータを渡します。 このスレッドが要求の処理を完了しても、"バイトを受信" アクティビティからリスナーには何も渡されません。 この場合、新しいスレッドのアクティビティへの転送はありますが、このアクティビティからの転送はありません。 2 つのアクティビティは関連していますが、入れ子にはなっていません。  
  
## <a name="activity-transfer-sequence"></a>アクティビティ転送シーケンス  
 適切なアクティビティ転送シーケンスには、次の手順が含まれます。  
  
1.  新しい gAId を選択して、新しいアクティビティを開始します。  
  
2.  現在のアクティビティ ID から新しい gAId への転送トレースを出力します。  
  
3.  TLS に新しい ID を設定します。  
  
4.  Start トレースを出力して、新しいアクティビティの開始を示します。  
  
5.  次の手順を実行して、元のアクティビティに戻ります。  
  
6.  元の gAId への転送トレースを出力します。  
  
7.  Stop トレースを出力して、新しいアクティビティの終了を示します。  
  
8.  TLS を以前の gAId に設定します。  
  
 これを実行する方法を次のコード例に示します。 この例は、新しいアクティビティへの転送時にブロック呼び出しが行われることを想定しており、Suspend トレースと Resume トレースが含まれています。  
  
```csharp
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  

// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();   

// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  

// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  

// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  

// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  

// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  

// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);   

// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  

// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  

// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;    

// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a>関連項目

- [トレースの構成](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [サービス トレース ビューアーを使用した相関トレースの表示とトラブルシューティング](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [エンドツーエンドのトレースのシナリオ](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [サービス トレース ビューアー ツール (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
