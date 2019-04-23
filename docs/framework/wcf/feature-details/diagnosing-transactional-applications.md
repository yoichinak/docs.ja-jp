---
title: トランザクション アプリケーションの診断
ms.date: 03/30/2017
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
ms.openlocfilehash: aca5f95e2085dfadf06da35dfd86af72c0b6092d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59101713"
---
# <a name="diagnosing-transactional-applications"></a>トランザクション アプリケーションの診断
このトピックでは、Windows Communication Foundation (WCF) の管理と診断機能を使用して、トランザクション アプリケーションをトラブルシューティングする方法について説明します。  
  
## <a name="performance-counters"></a>[パフォーマンス カウンター]  
 WCF には、トランザクション アプリケーションのパフォーマンスを測定するためのパフォーマンス カウンターの標準セットが用意されています。 詳細については、「[パフォーマンス カウンター](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)」を参照してください。  
  
 パフォーマンス カウンターには次の表に示すように、サービス、エンドポイント、操作の 3 つのレベルがあります。  
  
### <a name="service-performance-counters"></a>サービス パフォーマンス カウンター  
  
|パフォーマンス カウンター|説明|  
|-------------------------|-----------------|  
|トランザクション フロー|このサービスで操作に対して実行されたトランザクションの数です。 このカウンターは、サービスに送信されたメッセージにトランザクションがある場合は常にインクリメントされます。|  
|1 秒あたりのトランザクション フロー|このサービスの操作に対して実行された 1 秒あたりのトランザクションの数です。 このカウンターは、サービスに送信されたメッセージにトランザクションがある場合は常にインクリメントされます。|  
|コミットされたトランザクション操作|このサービスで、結果がコミットされた状態で完了したトランザクション操作の数です。 そのような操作中に実行された作業は完全にコミットされました。 リソースは、操作で実行された作業に応じて更新されます。|  
|1 秒あたりのコミットされたトランザクション操作|このサービスで、結果がコミットされた状態で完了したトランザクション操作の 1 秒あたりの数です。 そのような操作中に実行された作業は完全にコミットされました。 リソースは、操作で実行された作業に応じて更新されます。|  
|中止されたトランザクション操作|このサービスで、結果が中止された状態で完了したトランザクション操作の数です。 そのような操作中に実行された作業はロールバックされました。 リソースは、それぞれの直前の状態に復元されました。|  
|1 秒あたりの中止されたトランザクション操作|このサービスで、結果が中止された状態で完了したトランザクション操作の 1 秒あたりの数です。 そのような操作中に実行された作業はロールバックされました。 リソースは、それぞれの直前の状態に復元されました。|  
|不明なトランザクション操作|このサービスで、結果が不明な状態で完了したトランザクション操作の数です。 結果が不明な作業は中間状態になります。 リソースは、保留中となります。|  
|1 秒あたりの不明なトランザクション操作|このサービスで、結果が不明な状態で完了したトランザクション操作の 1 秒あたりの数です。 結果が不明な作業は中間状態になります。 リソースは、保留中となります。|  
  
### <a name="endpoint-performance-counters"></a>エンドポイントのパフォーマンス カウンター  
  
|パフォーマンス カウンター|説明|  
|-------------------------|-----------------|  
|トランザクション フロー|このエンドポイントでの操作に対して実行されたトランザクションの数。 このカウンターは、エンドポイントに送信されたメッセージにトランザクションがある場合は常にインクリメントされます。|  
|1 秒あたりのトランザクション フロー|毎秒ごとにこのエンドポイントでの操作に対して実行されたトランザクションの数。 このカウンターは、エンドポイントに送信されたメッセージにトランザクションがある場合は常にインクリメントされます。|  
  
### <a name="operation-performance-counters"></a>操作パフォーマンス カウンター  
  
|パフォーマンス カウンター|説明|  
|-------------------------|-----------------|  
|トランザクション フロー|このエンドポイントでの操作に対して実行されたトランザクションの数。 このカウンターは、エンドポイントに送信されたメッセージにトランザクションがある場合は常にインクリメントされます。|  
|1 秒あたりのトランザクション フロー|毎秒ごとにこのエンドポイントでの操作に対して実行されたトランザクションの数。 このカウンターは、エンドポイントに送信されたメッセージにトランザクションがある場合は常にインクリメントされます。|  
  
## <a name="windows-management-instrumentation"></a>WMI (Windows Management Instrumentation)  
 WCF では、WCF Windows Management Instrumentation (WMI) プロバイダーを介して実行時に、サービスの検査データを公開します。 WMI データにアクセスする方法の詳細については、次を参照してください。[診断用の Windows Management Instrumentation のを使用して](../../../../docs/framework/wcf/diagnostics/wmi/index.md)します。  
  
 WMI プロパティには、サービスに適用されるトランザクション設定を示す読み取り専用のプロパティが多数あります。 次の表にこれらの設定をすべて示します。  
  
 サービスの `ServiceBehaviorAttribute` には、次のプロパティがあります。  
  
|名前|種類|説明|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|ブール型|現在のトランザクションの完了時に、サービス オブジェクトをリサイクルするかどうかを指定します。|  
|TransactionAutoCompleteOnSessionClose|ブール型|現在のセッションの終了時に、保留中のトランザクションを完了するかどうかを指定します。|  
|TransactionIsolationLevel|<xref:System.Transactions.IsolationLevel> 列挙体の有効な値を含む文字列。|このサービスがサポートするトランザクションの分離レベルを指定します。|  
|TransactionTimeout|<xref:System.DateTime>|トランザクションを完了しなければならない期間を指定します。|  
  
 `ServiceTimeoutsBehavior` には、次のプロパティがあります。  
  
|名前|種類|説明|  
|----------|----------|-----------------|  
|TransactionTimeout|<xref:System.DateTime>|トランザクションを完了しなければならない期間を指定します。|  
  
 バインディングの `TransactionFlowBindingElement` には、次のプロパティがあります。  
  
|名前|種類|説明|  
|----------|----------|-----------------|  
|TransactionProtocol|<xref:System.ServiceModel.TransactionProtocol> 型の有効な値を含む文字列。|トランザクションをフローさせるために使用するトランザクション プロトコルを指定します。|  
|TransactionFlow|ブール型|受信トランザクション フローを有効にするかどうかを指定します。|  
  
 操作の `OperationBehaviorAttribute` には、次のプロパティがあります。  
  
|名前|種類|説明|  
|----------|----------|-----------------|  
|TransactionAutoComplete|ブール型|未処理の例外が発生しなかった場合に、現在のトランザクションを自動的にコミットするかどうかを指定します。|  
|TransactionScopeRequired|ブール型|操作がトランザクションを必要とするかどうかを指定します。|  
  
 操作の `TransactionFlowAttribute` には、次のプロパティがあります。  
  
|名前|種類|説明|  
|----------|----------|-----------------|  
|TransactionFlowOption|<xref:System.ServiceModel.TransactionFlowOption> 列挙体の有効な値を含む文字列。|トランザクション フローが要求される範囲を指定します。|  
  
## <a name="tracing"></a>トレース  
 トレースを使用すると、トランザクション アプリケーションにおけるエラーを監視および分析できます。 トレースは次の方法を使用して有効にできます。  
  
-   標準の WCF トレース  
  
     この種類のトレースは、任意の WCF アプリケーションのトレースと同じです。 詳細については、「 [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)」を参照してください。  
  
-   WS-AtomicTransaction トレース  
  
     WS-AtomicTransaction トレースを使用して有効にすることができます、 [WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)します。 このトレースでは、トランザクションの状態とシステム内の参加要素を把握できます。 内部のサービス モデル トレースも有効にするには、`HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` レジストリ キーを <xref:System.Diagnostics.SourceLevels> 列挙体の有効な値に設定します。 その他の WCF アプリケーションと同じ方法でメッセージ ログを有効にすることができます。  
  
-   `System.Transactions` トレース  
  
     OleTransactions プロトコルを使用する場合、プロトコル メッセージはトレースできません。 <xref:System.Transactions> インフラストラクチャではトレースがサポートされるため (OleTransactions を使用)、ユーザーはトランザクションで発生したイベントを確認できます。 <xref:System.Transactions> アプリケーションのトレースを有効にするには、`App.config` 構成ファイルに次のコードを含めます。  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
         <sources>  
            <source name="System.Transactions" switchValue="Verbose, ActivityTracing">  
               <listeners>  
                  <add name="Text"  
                     type="System.Diagnostics.XmlWriterTraceListener"  
                     initializeData="SysTx.log"  
                     traceOutputOptions="Callstack" />  
               </listeners>  
            </source>  
         </sources>  
         <trace autoflush="true" indentsize="4">  
         </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     WCF を利用またとして、WCF トレースの場合は、これもできます、<xref:System.Transactions>インフラストラクチャ。  
  
## <a name="see-also"></a>関連項目

- [管理と診断](../../../../docs/framework/wcf/diagnostics/index.md)
- [トレースの構成](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [WS-AtomicTransaction 構成ユーティリティ (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
