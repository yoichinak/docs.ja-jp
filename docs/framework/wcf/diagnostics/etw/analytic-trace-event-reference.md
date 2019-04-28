---
title: 分析トレース イベント リファレンス
ms.date: 03/30/2017
helpviewer_keywords:
- analytic tracing [WCF]. reference
ms.assetid: e44540cf-44a1-4efc-b965-7fbfd2131d73
ms.openlocfilehash: 0f8b4c15f2afefbc62b98dca66dcf3ccc31b1dc0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753037"
---
# <a name="analytic-trace-event-reference"></a>分析トレース イベント リファレンス
次の表は、イベント レベル、識別子、および WCF 分析トレースに関連付けられたメッセージを定義します。  
  
## <a name="event-reference"></a>イベント リファレンス  
  
|イベント ID|イベント レベル|イベント メッセージ|キーワード|  
|--------------|-----------------|-------------------|--------------|  
|[131 - BufferPoolAllocation](../../../../../docs/framework/wcf/diagnostics/etw/131-bufferpoolallocation.md)|詳細|プールが %1 バイトを割り当てています。|インフラストラクチャ|  
|[132 - BufferPoolChangeQuota](../../../../../docs/framework/wcf/diagnostics/etw/132-bufferpoolchangequota.md)|詳細|BufferPool のサイズ: %1、クォータの変更: %2。|インフラストラクチャ|  
|[133 - ActionItemScheduled](../../../../../docs/framework/wcf/diagnostics/etw/133-actionitemscheduled.md)|詳細|IO スレッド スケジューラのコールバックが呼び出されました。|インフラストラクチャ|  
|[134 - ActionItemCallbackInvoked](../../../../../docs/framework/wcf/diagnostics/etw/134-actionitemcallbackinvoked.md)|詳細|IO スレッド スケジューラのコールバックが呼び出されました。|インフラストラクチャ|  
|[201 - ClientMessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/201-clientmessageinspectorafterreceiveinvoked.md)|情報|ディスパッチャーが型 '%1' の ClientMessageInspector で 'AfterReceiveReply' を呼び出しました。|Troubleshooting、ServiceModel|  
|[202 - ClientMessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/202-clientmessageinspectorbeforesendinvoked.md)|情報|ディスパッチャーが型 '%1' の ClientMessageInspector で 'BeforeSendRequest' を呼び出しました。|Troubleshooting、ServiceModel|  
|[203 - ClientParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/203-clientparameterinspectoraftercallinvoked.md)|情報|ディスパッチャーが 型 '%1' の ClientParameterInspector で 'AfterCall' を呼び出しました。|Troubleshooting、ServiceModel|  
|[204 - ClientParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/204-clientparameterinspectorbeforecallinvoked.md)|情報|ディスパッチャーが型 '%1' の ClientParameterInspector で 'BeforeCall' を呼び出しました。|Troubleshooting、ServiceModel|  
|[205 - OperationInvoked](../../../../../docs/framework/wcf/diagnostics/etw/205-operationinvoked.md)|情報|OperationInvoker が '%1' メソッドを呼び出しました。|EndToEndMonitoring、Troubleshooting、ServiceModel|  
|[206 - ErrorHandlerInvoked](../../../../../docs/framework/wcf/diagnostics/etw/206-errorhandlerinvoked.md)|情報|ディスパッチャーが型 '%1' の ErrorHandler を呼び出し、種類 '%3' の例外がスローされました。  ErrorHandled == '%2'。|Troubleshooting、ServiceModel|  
|[207 - FaultProviderInvoked](../../../../../docs/framework/wcf/diagnostics/etw/207-faultproviderinvoked.md)|情報|ディスパッチャーが型 '%1' の FaultProvider を呼び出し、種類 '%2' の例外がスローされました。|Troubleshooting、ServiceModel|  
|[208 - MessageInspectorAfterReceiveInvoked](../../../../../docs/framework/wcf/diagnostics/etw/208-messageinspectorafterreceiveinvoked.md)|情報|ディスパッチャーが型 '%1' の MessageInspector で 'AfterReceiveReply' を呼び出しました。|Troubleshooting、ServiceModel|  
|[209 - MessageInspectorBeforeSendInvoked](../../../../../docs/framework/wcf/diagnostics/etw/209-messageinspectorbeforesendinvoked.md)|情報|ディスパッチャーが型 '%1' の MessageInspector で 'BeforeSendRequest' を呼び出しました。|Troubleshooting、ServiceModel|  
|[210 - MessageThrottleExceeded](../../../../../docs/framework/wcf/diagnostics/etw/210-messagethrottleexceeded.md)|警告|スロットル '%1' の '%2' の制限に達しました。|HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel|  
|[211 - ParameterInspectorAfterCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/211-parameterinspectoraftercallinvoked.md)|情報|ディスパッチャーが型 '%1' の ParameterInspector で 'AfterCall' を呼び出しました。|Troubleshooting、ServiceModel|  
|[212 - ParameterInspectorBeforeCallInvoked](../../../../../docs/framework/wcf/diagnostics/etw/212-parameterinspectorbeforecallinvoked.md)|情報|ディスパッチャーが型 '%1' の ParameterInspector で 'BeforeCall' を呼び出しました。|Troubleshooting、ServiceModel|  
|[213 - ServiceHostStarted](../../../../../docs/framework/wcf/diagnostics/etw/213-servicehoststarted.md)|LogAlways (常にログ)|ServiceHost は '%1' で開始されています。|HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel|  
|[214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md)|情報|OperationInvoker がメソッド '%1' への呼び出しを完了しました。  メソッド呼び出し時間は '%2' ミリ秒でした。|HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel|  
|[215 - MessageReceivedByTransport](../../../../../docs/framework/wcf/diagnostics/etw/215-messagereceivedbytransport.md)|情報|トランスポートが '%1' からメッセージを受信しました。|Troubleshooting、ServiceModel|  
|[216 - MessageSentByTransport](../../../../../docs/framework/wcf/diagnostics/etw/216-messagesentbytransport.md)|情報|トランスポートが '%1' にメッセージを送信しました。|Troubleshooting、ServiceModel|  
|[217 - ClientOperationPrepared](../../../../../docs/framework/wcf/diagnostics/etw/217-clientoperationprepared.md)|情報|クライアントは '%2' コントラクトと関連付けられている Action '%1' を実行しています。 メッセージは '%3' に送信されます。|Troubleshooting、ServiceModel|  
|[218 - ClientOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/218-clientoperationcompleted.md)|情報|クライアントは '%1' コントラクトと関連付けられている Action '%1' の実行を完了しました。 メッセージは '%3' に送信されました。|Troubleshooting、ServiceModel|  
|[219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md)|Error|メッセージの処理中に種類 '%2' のハンドルされない例外がスローされました。  完全な例外 ToString: %1。|HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel|  
|[220 - MessageSentToTransport](../../../../../docs/framework/wcf/diagnostics/etw/220-messagesenttotransport.md)|情報|ディスパッチャーがトランスポートにメッセージを送信しました。 関連付け ID == '%1'。|EndToEndMonitoring、Troubleshooting、ServiceModel|  
|[221 - MessageReceivedFromTransport](../../../../../docs/framework/wcf/diagnostics/etw/221-messagereceivedfromtransport.md)|情報|ディスパッチャーがトランスポートからメッセージを受信しました。 関連付け ID == '%1'。|EndToEndMonitoring、Troubleshooting、ServiceModel|  
|[222 - OperationFailed](../../../../../docs/framework/wcf/diagnostics/etw/222-operationfailed.md)|警告|OperationInvoker によって呼び出されたメソッド '%1' で、ハンドルされない例外がスローされました。 メソッド呼び出し時間は '%2' ミリ秒でした。|HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel|  
|[223 - OperationFaulted](../../../../../docs/framework/wcf/diagnostics/etw/223-operationfaulted.md)|警告|OperationInvoker によって呼び出されたメソッド '%1' で FaultException がスローされました。 メソッド呼び出し時間は '%2' ミリ秒でした。|HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel|  
|[224 - MessageThrottleAtSeventyPercent](../../../../../docs/framework/wcf/diagnostics/etw/224-messagethrottleatseventypercent.md)|警告|スロットル '%1' の '%2' の制限は 70% です。|HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel|  
|[226 - IdleServicesClosed](../../../../../docs/framework/wcf/diagnostics/etw/226-idleservicesclosed.md)|LogAlways (常にログ)|アクティブ化された合計 %2 個のサービスのうち、アイドル状態の %1 個のサービスが閉じられました。|HealthMonitoring WebHost|  
|[301 - UserDefinedErrorOccurred](../../../../../docs/framework/wcf/diagnostics/etw/301-userdefinederroroccurred.md)|Error|名前: '%1'、参照: '%2'、ペイロード: %3|UserEvents、HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel|  
|[302 - UserDefinedWarningOccurred](../../../../../docs/framework/wcf/diagnostics/etw/302-userdefinedwarningoccurred.md)|警告|名前: '%1'、参照: '%2'、ペイロード: %3|UserEvents、HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel|  
|[303 - UserDefinedInformationEventOccured](../../../../../docs/framework/wcf/diagnostics/etw/303-userdefinedinformationeventoccured.md)|情報|名前: '%1'、参照: '%2'、ペイロード: %3|UserEvents、HealthMonitoring、EndToEndMonitoring、Troubleshooting、ServiceModel|  
|[401- StopSignPostEvent](../../../../../docs/framework/wcf/diagnostics/etw/401-stopsignpostevent.md)|情報|アクティビティの境界|トラブルシューティング|  
|[402 - StartSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/402-startsignpostevent.md)|情報|アクティビティの境界|トラブルシューティング|  
|[403 - SuspendSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/403-suspendsignpostevent.md)|情報|アクティビティの境界|トラブルシューティング|  
|[404 - ResumeSignpostEvent](../../../../../docs/framework/wcf/diagnostics/etw/404-resumesignpostevent.md)|情報|アクティビティの境界|トラブルシューティング|  
|[451 - MessageLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/451-messageloginfo.md)|情報|%1|Troubleshooting、WCFMessageLogging|  
|[452 - MessageLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/452-messagelogwarning.md)|警告|%1|Troubleshooting、WCFMessageLogging|  
|[499 - TransferEmitted](../../../../../docs/framework/wcf/diagnostics/etw/499-transferemitted.md)|LogAlways (常にログ)|転送イベントが作成されました。|Troubleshooting、UserEvents、EndToEndMonitoring、ServiceModel、WFTracking、ServiceHost、WCFMessageLogging|  
|[501 - CompilationStart](../../../../../docs/framework/wcf/diagnostics/etw/501-compilationstart.md)|情報|コンパイルを開始します|WebHost|  
|[502 - CompilationStop](../../../../../docs/framework/wcf/diagnostics/etw/502-compilationstop.md)|情報|コンパイルを終了します|WebHost|  
|[503 - ServiceHostFactoryCreationStart](../../../../../docs/framework/wcf/diagnostics/etw/503-servicehostfactorycreationstart.md)|情報|ServiceHostFactory が作成を開始します|WebHost|  
|[504 - ServiceHostFactoryCreationStop](../../../../../docs/framework/wcf/diagnostics/etw/504-servicehostfactorycreationstop.md)|情報|ServiceHostFactory が作成を終了します|WebHost|  
|[505 - CreateServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/505-createservicehoststart.md)|情報|CreateServiceHost を開始します|WebHost|  
|[506 - CreateServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/506-createservicehoststop.md)|情報|CreateServiceHost を終了します|WebHost|  
|[507 - HostedTransportConfigurationManagerConfigInitStart](../../../../../docs/framework/wcf/diagnostics/etw/507-hostedtransportconfigurationmanagerconfiginitstart.md)|情報|HostedTransportConfigurationManager が構成の初期化を開始します|WebHost|  
|[508 - HostedTransportConfigurationManagerConfigInitStop](../../../../../docs/framework/wcf/diagnostics/etw/508-hostedtransportconfigurationmanagerconfiginitstop.md)|情報|HostedTransportConfigurationManager が構成の初期化を終了します|WebHost|  
|[509 - ServiceHostOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/509-servicehostopenstart.md)|情報|HostedTransportConfigurationManager が構成の初期化を終了します|ServiceHost|  
|[510 - ServiceHostOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/510-servicehostopenstop.md)|情報|ServiceHost Open が完了しました。|ServiceHost|  
|[513 - WebHostRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/513-webhostrequeststart.md)|情報|AppDomain '%1' からの仮想パス '%2' で要求を受信しました。|WebHost|  
|[514 - WebHostRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/514-webhostrequeststop.md)|情報|WebHostRequest を停止します。|WebHost|  
|[601 - CBAEntryRead](../../../../../docs/framework/wcf/diagnostics/etw/601-cbaentryread.md)|詳細|ServiceActivation 要素の相対アドレス: '%1'、標準化相対アドレス '%2' を処理しました。||  
|[602 - CBAMatchFound](../../../../../docs/framework/wcf/diagnostics/etw/602-cbamatchfound.md)|詳細|受信要求が、アドレス '%1' の ServiceActivation 要素と一致します。||  
|[603 - AspNetRoutingService](../../../../../docs/framework/wcf/diagnostics/etw/603-aspnetroutingservice.md)|詳細|受信要求が、アドレス %1 の Asp.Net ルートで定義された WCF サービスと一致します。|RoutingServices|  
|[604 - AspNetRoute](../../../../../docs/framework/wcf/diagnostics/etw/604-aspnetroute.md)|詳細|serviceType '%2' および serviceHostFactoryType '%3' の新しい Asp.Net ルート '%1' が追加されます。|RoutingServices|  
|[605 - IncrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/605-incrementbusycount.md)|詳細|IncrementBusyCount が呼び出されました。 ソース: %1|WebHost|  
|[606 - DecrementBusyCount](../../../../../docs/framework/wcf/diagnostics/etw/606-decrementbusycount.md)|詳細|DecrementBusyCount が呼び出されました。 ソース: %1|WebHost|  
|[701 - ServiceChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/701-servicechannelopenstart.md)|詳細|ServiceChannelOpen を開始しました。|WebHost|  
|[702 - ServiceChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/702-servicechannelopenstop.md)|情報|ServiceChannelOpen が完了しました。|ServiceModel|  
|[703 - ServiceChannelCallStart](../../../../../docs/framework/wcf/diagnostics/etw/703-servicechannelcallstart.md)|情報|ServiceChannelCall を開始しました。|ServiceModel|  
|[704 - ServiceChannelBeginCallStart](../../../../../docs/framework/wcf/diagnostics/etw/704-servicechannelbegincallstart.md)|情報|ServiceChannel の非同期呼び出しを開始しました。|ServiceModel|  
|[706 - HttpSendMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/706-httpsendmessagestart.md)|詳細|HTTP 送信要求を開始します。|HTTP|  
|[707 - HttpSendStop](../../../../../docs/framework/wcf/diagnostics/etw/707-httpsendstop.md)|詳細|HTTP 送信要求を停止します。|HTTP|  
|[708 - HttpMessageReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/708-httpmessagereceivestart.md)|詳細|HTTP トランスポートからメッセージを受信しました。|HTTP|  
|[709 - DispatchMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/709-dispatchmessagestart.md)|情報|メッセージのディスパッチを開始しました。|ServiceModel|  
|[710 - HttpContextBeforeProcessAuthentication](../../../../../docs/framework/wcf/diagnostics/etw/710-httpcontextbeforeprocessauthentication.md)|詳細|メッセージのディスパッチの認証を開始します|ServiceModel|  
|[711 - DispatchMessageBeforeAuthorization](../../../../../docs/framework/wcf/diagnostics/etw/711-dispatchmessagebeforeauthorization.md)|詳細|メッセージのディスパッチの承認を開始します|ServiceModel|  
|[712 - DispatchMessageStop](../../../../../docs/framework/wcf/diagnostics/etw/712-dispatchmessagestop.md)|情報|メッセージのディスパッチが完了しました|ServiceModel|  
|[715 - ClientChannelOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/715-clientchannelopenstart.md)|情報|ServiceChannel Open を開始します。|ServiceModel|  
|[716 - ClientChannelOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/716-clientchannelopenstop.md)|情報|ServiceChannel Open を停止します。|ServiceModel|  
|[717 - HttpSendStreamedMessageStart](../../../../../docs/framework/wcf/diagnostics/etw/717-httpsendstreamedmessagestart.md)|情報|ストリーム メッセージの HTTP 送信を開始しました。|HTTP|  
|[1400 - ChannelInitializationTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1400-channelinitializationtimeout.md)|Error|1%|ServiceModel|  
|[1401 - CloseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1401-closetimeout.md)|Error|1%|ServiceModel|  
|[1402 - IdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1402-idletimeout.md)|Error|%1 接続プール キー: %2|ServiceModel|  
|[1403 - LeaseTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1403-leasetimeout.md)|情報|%1 接続プール キー: %2|ServiceModel|  
|[1405 - OpenTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1405-opentimeout.md)|Error|%1|ServiceModel|  
|[1406 - ReceiveTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1406-receivetimeout.md)|Error|%1|ServiceModel|  
|[1407 - SendTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1407-sendtimeout.md)|Error|%1|ServiceModel|  
|[1409 - InactivityTimeout](../../../../../docs/framework/wcf/diagnostics/etw/1409-inactivitytimeout.md)|情報|%1|ServiceModel|  
|[1416 - MaxReceivedMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1416-maxreceivedmessagesizeexceeded.md)|Error|%1|クォータ|  
|[1417 - MaxSentMessageSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1417-maxsentmessagesizeexceeded.md)|Error|%1|クォータ|  
|[1418 - MaxOutboundConnectionsPerEndpointExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1418-maxoutboundconnectionsperendpointexceeded.md)|情報|%1|クォータ|  
|[1419 - MaxPendingConnectionsExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1419-maxpendingconnectionsexceeded.md)|情報|%1|クォータ|  
|[1420 - ReaderQuotaExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1420-readerquotaexceeded.md)|Error|%1|クォータ|  
|[1422 - NegotiateTokenAuthenticatorStateCacheExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1422-negotiatetokenauthenticatorstatecacheexceeded.md)|Error|%1|クォータ|  
|[1423 - NegotiateTokenAuthenticatorStateCacheRatio](../../../../../docs/framework/wcf/diagnostics/etw/1423-negotiatetokenauthenticatorstatecacheratio.md)|詳細|トークン認証システムのネゴシエートの状態のキャッシュ比率: %1/%2|クォータ|  
|[1424 - SecuritySessionRatio](../../../../../docs/framework/wcf/diagnostics/etw/1424-securitysessionratio.md)|詳細|セキュリティ セッションの比率: %1/%2|クォータ|  
|[1430 - PendingConnectionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1430-pendingconnectionsratio.md)|詳細|保留中の接続の比率: %1/%2|クォータ|  
|[1431 - ConcurrentCallsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1431-concurrentcallsratio.md)|詳細|同時セッションの比率: %1/%2|クォータ|  
|[1432 - ConcurrentSessionsRatio](../../../../../docs/framework/wcf/diagnostics/etw/1432-concurrentsessionsratio.md)|詳細|同時セッションの比率: %1/%2|クォータ|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|詳細|エンドポイントごとの送信接続の比率: %1/%2|クォータ|  
|[1433 - OutboundConnectionsPerEndpointRatio](../../../../../docs/framework/wcf/diagnostics/etw/1433-outboundconnectionsperendpointratio.md)|詳細|エンドポイントごとの送信接続の比率: %1/%2|クォータ|  
|[1436 - PendingMessagesPerChannelRatio](../../../../../docs/framework/wcf/diagnostics/etw/1436-pendingmessagesperchannelratio.md)|詳細|チャネルごとの保留メッセージの比率: %1/%2|クォータ|  
|[1438 - ConcurrentInstancesRatio](../../../../../docs/framework/wcf/diagnostics/etw/1438-concurrentinstancesratio.md)|詳細|同時インスタンスの比率: %1/%2|クォータ|  
|[1439 - PendingAcceptsAtZero](../../../../../docs/framework/wcf/diagnostics/etw/1439-pendingacceptsatzero.md)|情報|保留中の受け入れはありません|クォータ|  
|[1441 - MaxSessionSizeReached](../../../../../docs/framework/wcf/diagnostics/etw/1441-maxsessionsizereached.md)|警告|1%|クォータ|  
|[1442 - ReceiveRetryCountReached](../../../../../docs/framework/wcf/diagnostics/etw/1442-receiveretrycountreached.md)|警告|ID '%1' の MSMQ メッセージが受信再試行回数に達しました|クォータ|  
|[1443 - MaxRetryCyclesExceededMsmq](../../../../../docs/framework/wcf/diagnostics/etw/1443-maxretrycyclesexceededmsmq.md)|Error|ID '%1' の MSMQ メッセージが最大再試行サイクルを超えました|クォータ|  
|[1445 - ReadPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1445-readpoolmiss.md)|詳細|新しい '%1' を作成しました|クォータ|  
|[1446 - WritePoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/1446-writepoolmiss.md)|詳細|新しい '%1' を作成しました|クォータ|  
|[1451 - MaxRetryCyclesExceeded](../../../../../docs/framework/wcf/diagnostics/etw/1451-maxretrycyclesexceeded.md)|Error|1%|クォータ|  
|[3300 - ReceiveContextCompleteFailed](../../../../../docs/framework/wcf/diagnostics/etw/3300-receivecontextcompletefailed.md)|警告|%1 を完了できませんでした。|チャネル|  
|[3301 - ReceiveContextAbandonFailed](../../../../../docs/framework/wcf/diagnostics/etw/3301-receivecontextabandonfailed.md)|警告|%1 を破棄できませんでした。|チャネル|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|警告|受信コンテキストでエラーが発生しました。|ServiceModel|  
|[3303 - ReceiveContextAbandonWithException](../../../../../docs/framework/wcf/diagnostics/etw/3303-receivecontextabandonwithexception.md)|情報|例外 %2 が発生したため、%1 が破棄されました。|チャネル|  
|[3305 - ClientBaseCachedChannelFactoryCount](../../../../../docs/framework/wcf/diagnostics/etw/3305-clientbasecachedchannelfactorycount.md)|情報|キャッシュされたチャネル ファクトリの数は '%1' です。  最大で '%2' 個のチャネル ファクトリをキャッシュできます。|ServiceModel|  
|[3306 - ClientBaseChannelFactoryAgedOutofCache](../../../../../docs/framework/wcf/diagnostics/etw/3306-clientbasechannelfactoryagedoutofcache.md)|情報|キャッシュが上限の '%1' に達したため、チャネル ファクトリがキャッシュから削除されました。|ServiceModel|  
|[3307 - ClientBaseChannelFactoryCacheHit](../../../../../docs/framework/wcf/diagnostics/etw/3307-clientbasechannelfactorycachehit.md)|情報|キャッシュで見つかった一致するチャネル ファクトリが使用されました。|ServiceModel|  
|[3308 - ClientBaseUsingLocalChannelFactory](../../../../../docs/framework/wcf/diagnostics/etw/3308-clientbaseusinglocalchannelfactory.md)|情報|キャッシュのチャネル ファクトリは使用されません (つまり、インスタンスのキャッシュは無効になっています)。|ServiceModel|  
|[3309 - QueryCompositionExecuted](../../../../../docs/framework/wcf/diagnostics/etw/3309-querycompositionexecuted.md)|情報|'%1' を使用したクエリの構成が要求 URI: '%2' で実行されました。|ServiceModel|  
|[3310 - DispatchFailed](../../../../../docs/framework/wcf/diagnostics/etw/3310-dispatchfailed.md)|Error|'%1' 操作のディスパッチでエラーが発生しました。|ServiceModel|  
|[3311 - DispatchSuccessful](../../../../../docs/framework/wcf/diagnostics/etw/3311-dispatchsuccessful.md)|情報|'%1' 操作が正常にディスパッチされました。|ServiceModel|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|情報|サイズ '%1' バイトのメッセージがエンコーダーによって読み取られました。|チャネル|  
|[3312 - MessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3312-messagereadbyencoder.md)|情報|サイズ '%1' バイトのメッセージがエンコーダーによって書き込まれました。|チャネル|  
|[3314 - SessionIdleTimeout](../../../../../docs/framework/wcf/diagnostics/etw/3314-sessionidletimeout.md)|Error|URI: '%1' へのアイドル チャネルのセッションを中止しています。|ServiceModel|  
|[3319 - SocketAcceptEnqueued](../../../../../docs/framework/wcf/diagnostics/etw/3319-socketacceptenqueued.md)|詳細|接続の受け入れを開始しました。|TCP|  
|[3320 - SocketAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3320-socketaccepted.md)|詳細|ListenerId:%1 が SocketId:%2 を受け入れました。|TCP|  
|[3321 - ConnectionPoolMiss](../../../../../docs/framework/wcf/diagnostics/etw/3321-connectionpoolmiss.md)|詳細|%1 のプールに使用可能な接続がありません。%2 個の接続がビジー状態です。|チャネル|  
|[3322 - DispatchFormatterDeserializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3322-dispatchformatterdeserializerequeststart.md)|詳細|ディスパッチャーが要求メッセージのシリアル化解除を開始しました。|ServiceModel|  
|[3323 - DispatchFormatterDeserializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3323-dispatchformatterdeserializerequeststop.md)|詳細|ディスパッチャーが要求メッセージのシリアル化解除を完了しました。|ServiceModel|  
|[3324 - DispatchFormatterSerializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3324-dispatchformatterserializereplystart.md)|詳細|ディスパッチャーが応答メッセージのシリアル化を開始しました。|ServiceModel|  
|[3325 - DispatchFormatterSerializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3325-dispatchformatterserializereplystop.md)|詳細|ディスパッチャーが応答メッセージのシリアル化を完了しました。|ServiceModel|  
|[3326 - ClientFormatterSerializeRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3326-clientformatterserializerequeststart.md)|詳細|クライアント要求のシリアル化を開始しました。|ServiceModel|  
|[3327 - ClientFormatterSerializeRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3327-clientformatterserializerequeststop.md)|詳細|クライアントが要求メッセージのシリアル化を完了しました。|ServiceModel|  
|[3328 - ClientFormatterDeserializeReplyStart](../../../../../docs/framework/wcf/diagnostics/etw/3328-clientformatterdeserializereplystart.md)|詳細|クライアントが応答メッセージのシリアル化解除を開始しました。|ServiceModel|  
|[3329 - ClientFormatterDeserializeReplyStop](../../../../../docs/framework/wcf/diagnostics/etw/3329-clientformatterdeserializereplystop.md)|詳細|クライアントが応答メッセージのシリアル化解除を完了しました。|ServiceModel|  
|[3330 - SecurityNegotiationStart](../../../../../docs/framework/wcf/diagnostics/etw/3330-securitynegotiationstart.md)|詳細|セキュリティ ネゴシエーションを開始しました。|セキュリティ|  
|[3331 - SecurityNegotiationStop](../../../../../docs/framework/wcf/diagnostics/etw/3331-securitynegotiationstop.md)|詳細|セキュリティ ネゴシエーションが完了しました。|セキュリティ|  
|[3332 - SecurityTokenProviderOpened](../../../../../docs/framework/wcf/diagnostics/etw/3332-securitytokenprovideropened.md)|詳細|SecurityTokenProvider のオープンが完了しました。|セキュリティ|  
|[3333 - OutgoingMessageSecured](../../../../../docs/framework/wcf/diagnostics/etw/3333-outgoingmessagesecured.md)|詳細|送信メッセージがセキュリティで保護されました。|セキュリティ|  
|[3334 - IncomingMessageVerified](../../../../../docs/framework/wcf/diagnostics/etw/3334-incomingmessageverified.md)|詳細|受信メッセージが確認されました。|セキュリティ ServiceModel|  
|[3335 - GetServiceInstanceStart](../../../../../docs/framework/wcf/diagnostics/etw/3335-getserviceinstancestart.md)|詳細|サービス インスタンスの取得を開始しました。|ServiceModel|  
|[3336 - GetServiceInstanceStop](../../../../../docs/framework/wcf/diagnostics/etw/3336-getserviceinstancestop.md)|詳細|サービス インスタンスが取得されました。|ServiceModel|  
|[3337 - ChannelReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3337-channelreceivestart.md)|詳細|ChannelHandlerId:%1 - メッセージ受信ループを開始しました。|チャネル|  
|[3338 - ChannelReceiveStop](../../../../../docs/framework/wcf/diagnostics/etw/3338-channelreceivestop.md)|詳細|ChannelHandlerId:%1 - メッセージ受信ループを停止しました。|チャネル|  
|[3339 - ChannelFactoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3339-channelfactorycreated.md)|詳細|ChannelFactory が作成されました。|ServiceModel|  
|[3340 - PipeConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3340-pipeconnectionacceptstart.md)|詳細|%1 でパイプ接続の受け入れを開始しました。|チャネル|  
|[3341 - PipeConnectionAcceptStop](../../../../../docs/framework/wcf/diagnostics/etw/3341-pipeconnectionacceptstop.md)|詳細|パイプ接続を受け入れました。|チャネル|  
|[3342 - EstablishConnectionStart](../../../../../docs/framework/wcf/diagnostics/etw/3342-establishconnectionstart.md)|詳細|%1 の接続の確立を開始しました。|チャネル|  
|[3343 - EstablishConnectionStop](../../../../../docs/framework/wcf/diagnostics/etw/3343-establishconnectionstop.md)|詳細|接続が確立されました。|チャネル|  
|[3345 - SessionPreambleUnderstood](../../../../../docs/framework/wcf/diagnostics/etw/3345-sessionpreambleunderstood.md)|詳細|'%1' のセッション プリアンブルが認識されました。|チャネル|  
|[3346 - ConnectionReaderSendFault](../../../../../docs/framework/wcf/diagnostics/etw/3346-connectionreadersendfault.md)|Error|接続リーダーがエラー '%1' を送信しています。|チャネル|  
|[3347 - SocketAcceptClosed](../../../../../docs/framework/wcf/diagnostics/etw/3347-socketacceptclosed.md)|詳細|ソケットの受け入れを終了しました。|TCP|  
|[3348 - ServiceHostFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3348-servicehostfaulted.md)|重大|サービス ホストが途中終了しました。|TCP|  
|[3349 - ListenerOpenStart](../../../../../docs/framework/wcf/diagnostics/etw/3349-listeneropenstart.md)|詳細|'%1' のリスナーを開いています。|チャネル|  
|[3350 - ListenerOpenStop](../../../../../docs/framework/wcf/diagnostics/etw/3350-listeneropenstop.md)|詳細|リスナーのオープンが完了しました。|チャネル|  
|[3351 - ServerMaxPooledConnectionsQuotaReached](../../../../../docs/framework/wcf/diagnostics/etw/3351-servermaxpooledconnectionsquotareached.md)|詳細|サーバーのプールされた接続の最大クォータに達しました。|クォータ|  
|[3352 - TcpConnectionTimedOut](../../../../../docs/framework/wcf/diagnostics/etw/3352-tcpconnectiontimedout.md)|Error|リモート アドレス %2 への SocketId:%1 がタイムアウトしました。|TCP|  
|[3353 - TcpConnectionResetError](../../../../../docs/framework/wcf/diagnostics/etw/3353-tcpconnectionreseterror.md)|警告|リモート アドレス %2 への SocketId:%1 で接続リセット エラーが発生しました。|TCP|  
|[3354 - ServiceSecurityNegotiationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/3354-servicesecuritynegotiationcompleted.md)|詳細|サービス セキュリティ ネゴシエーションが完了しました。|セキュリティ|  
|[3355 - SecurityNegotiationProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3355-securitynegotiationprocessingfailure.md)|Error|セキュリティ ネゴシエーション処理が失敗しました。|セキュリティ|  
|[3356 - SecurityIdentityVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3356-securityidentityverificationsuccess.md)|詳細|セキュリティ検証が成功しました。|セキュリティ|  
|[3357 - SecurityIdentityVerificationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3357-securityidentityverificationfailure.md)|Error|セキュリティ検証に失敗しました。|セキュリティ|  
|[3358 - PortSharingDuplicatedSocket](../../../../../docs/framework/wcf/diagnostics/etw/3358-portsharingduplicatedsocket.md)|詳細|%1 のソケットが複製されました。|ActivationServices|  
|[3359 - SecurityImpersonationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3359-securityimpersonationsuccess.md)|詳細|セキュリティの偽装に成功しました。|セキュリティ|  
|[3360 - SecurityImpersonationFailure](../../../../../docs/framework/wcf/diagnostics/etw/3360-securityimpersonationfailure.md)|警告|セキュリティの偽装に失敗しました。|セキュリティ|  
|[3361 - HttpChannelRequestAborted](../../../../../docs/framework/wcf/diagnostics/etw/3361-httpchannelrequestaborted.md)|警告|HTTP チャネルの要求が中止されました。|HTTP|  
|[3362 - HttpChannelResponseAborted](../../../../../docs/framework/wcf/diagnostics/etw/3362-httpchannelresponseaborted.md)|警告|HTTP チャネルの応答が中止されました。|HTTP|  
|[3363 - HttpAuthFailed](../../../../../docs/framework/wcf/diagnostics/etw/3363-httpauthfailed.md)|警告|HTTP 認証に失敗しました。|HTTP|  
|[3364 - SharedListenerProxyRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/3364-sharedlistenerproxyregisterstart.md)|詳細|URI '%1' の SharedListenerProxy の登録を開始しました。|ActivationServices|  
|[3365 - SharedListenerProxyRegisterStop](../../../../../docs/framework/wcf/diagnostics/etw/3365-sharedlistenerproxyregisterstop.md)|詳細|SharedListenerProxy の登録を停止します。|ActivationServices|  
|[3366 - SharedListenerProxyRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/3366-sharedlistenerproxyregisterfailed.md)|Error|SharedListenerProxy の登録は状態 '%1' で失敗しました。|ActivationServices|  
|[3367 - ConnectionPoolPreambleFailed](../../../../../docs/framework/wcf/diagnostics/etw/3367-connectionpoolpreamblefailed.md)|Error|ConnectionPoolPreambleFailed。|チャネル|  
|[3368 - SslOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3368-ssloninitiateupgrade.md)|詳細|SslOnAcceptUpgradeStart|セキュリティ|  
|[3369 - SslOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3369-sslonacceptupgrade.md)|詳細|SslOnAcceptUpgradeStop|セキュリティ|  
|[3370 - BinaryMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3370-binarymessageencodingstart.md)|詳細|BinaryMessageEncoder がメッセージのエンコードを開始しました。|チャネル|  
|[3371 - MtomMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3371-mtommessageencodingstart.md)|詳細|MtomMessageEncoder がメッセージのエンコードを開始しました。|チャネル|  
|[3372 - TextMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3372-textmessageencodingstart.md)|詳細|TextMessageEncoder がメッセージのエンコードを開始しました。|チャネル|  
|[3373 - BinaryMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3373-binarymessagedecodingstart.md)|詳細|BinaryMessageEncoder がメッセージのデコードを開始しました。|チャネル|  
|[3374 - MtomMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3374-mtommessagedecodingstart.md)|詳細|MtomMessageEncoder がメッセージのデコードを開始しました。|チャネル|  
|[3375 - TextMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/3375-textmessagedecodingstart.md)|詳細|TextMessageEncoder がメッセージのデコードを開始しました。|チャネル|  
|[3376 - HttpResponseReceiveStart](../../../../../docs/framework/wcf/diagnostics/etw/3376-httpresponsereceivestart.md)|情報|HTTP トランスポートがメッセージの受信を開始しました。|HTTP|  
|[3377 - SocketReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3377-socketreadstop.md)|詳細|SocketId:%1 が '%3' から '%2' バイトを読み取りました。|TCP|  
|[3378 - SocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3378-socketasyncreadstop.md)|詳細|SocketId:%1 が '%3' から '%2' バイトを読み取りました。|TCP|  
|[3379 - SocketWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3379-socketwritestart.md)|詳細|SocketId:%1 が '%3' に '%2' バイトを書き込んでいます。|TCP|  
|[3380 - SocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3380-socketasyncwritestart.md)|詳細|SocketId:%1 が '%3' に '%2' バイトを書き込んでいます。|TCP|  
|[3381 - SequenceAcknowledgementSent](../../../../../docs/framework/wcf/diagnostics/etw/3381-sequenceacknowledgementsent.md)|詳細|SessionId:%1 の受信確認が送信されました。|チャネル|  
|[3382 - ClientReliableSessionReconnect](../../../../../docs/framework/wcf/diagnostics/etw/3382-clientreliablesessionreconnect.md)|情報|SessionId:%1 を再接続します。|チャネル|  
|[3383 - ReliableSessionChannelFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3383-reliablesessionchannelfaulted.md)|情報|SessionId:%1 でエラーが発生しました。|チャネル|  
|[3384 - WindowsStreamSecurityOnInitiateUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3384-windowsstreamsecurityoninitiateupgrade.md)|詳細|WindowsStreamSecurity がセキュリティ アップグレードを開始しています。|セキュリティ|  
|[3385 - WindowsStreamSecurityOnAcceptUpgrade](../../../../../docs/framework/wcf/diagnostics/etw/3385-windowsstreamsecurityonacceptupgrade.md)|詳細|Windows ストリーミング セキュリティがアップグレードを受け入れています。|セキュリティ|  
|[3386 - SocketConnectionAbort](../../../../../docs/framework/wcf/diagnostics/etw/3386-socketconnectionabort.md)|警告|SocketId:%1 を中止しています。|TCP|  
|[3388 - HttpGetContextStart](../../../../../docs/framework/wcf/diagnostics/etw/3388-httpgetcontextstart.md)|詳細|HttpGetContext を開始します。|HTTP|  
|[3389 - ClientSendPreambleStart](../../../../../docs/framework/wcf/diagnostics/etw/3389-clientsendpreamblestart.md)|詳細|クライアントがプリアンブルの送信を開始します。|チャネル|  
|[3390 - ClientSendPreambleStop](../../../../../docs/framework/wcf/diagnostics/etw/3390-clientsendpreamblestop.md)|詳細|クライアントがプリアンブルの送信を停止します。|チャネル|  
|[3391 - HttpMessageReceiveFailed](../../../../../docs/framework/wcf/diagnostics/etw/3391-httpmessagereceivefailed.md)|警告|HTTP メッセージの受信に失敗しました。|HTTP|  
|[3392 - TransactionScopeCreate](../../../../../docs/framework/wcf/diagnostics/etw/3392-transactionscopecreate.md)|情報|LocalIdentifier:'%1' および DistributedIdentifier:'%2' の TransactionScope を作成しています。|ServiceModel|  
|[3393 - StreamedMessageReadByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3393-streamedmessagereadbyencoder.md)|情報|エンコーダーによってストリーム メッセージが読み取られました。|チャネル|  
|[3394 - StreamedMessageWrittenByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3394-streamedmessagewrittenbyencoder.md)|情報|エンコーダーによってストリーム メッセージが書き込まれました。|チャネル|  
|[3395 - MessageWrittenAsynchronouslyByEncoder](../../../../../docs/framework/wcf/diagnostics/etw/3395-messagewrittenasynchronouslybyencoder.md)|情報|エンコーダーによってメッセージが非同期で書き込まれました。|チャネル|  
|[3396 - BufferedAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3396-bufferedasyncwritestart.md)|情報|BufferId:%1 から基になるストリームへの '%2' バイトの書き込みが完了しました。|チャネル|  
|[3397 - BufferedAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3397-bufferedasyncwritestop.md)|情報|エンコーダーによってメッセージが非同期で書き込まれました。|チャネル|  
|[3398 - PipeSharedMemoryCreated](../../../../../docs/framework/wcf/diagnostics/etw/3398-pipesharedmemorycreated.md)|詳細|パイプ共有メモリが '%1' に作成されました。|チャネル|  
|[3399 - NamedPipeCreated](../../../../../docs/framework/wcf/diagnostics/etw/3399-namedpipecreated.md)|詳細|NamedPipe '%1' が作成されました。|チャネル|  
|[3401 - SignatureVerificationStart](../../../../../docs/framework/wcf/diagnostics/etw/3401-signatureverificationstart.md)|詳細|署名の検証を開始しました。|セキュリティ|  
|[3402 - SignatureVerificationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3402-signatureverificationsuccess.md)|詳細|署名の検証に成功しました|セキュリティ|  
|[3403 - WrappedKeyDecryptionStart](../../../../../docs/framework/wcf/diagnostics/etw/3403-wrappedkeydecryptionstart.md)|詳細|ラップされたキーの解読を開始しました。|セキュリティ|  
|[3404 - WrappedKeyDecryptionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3404-wrappedkeydecryptionsuccess.md)|詳細|ラップされたキーの解読に成功しました。|セキュリティ|  
|[3405 - EncryptedDataProcessingStart](../../../../../docs/framework/wcf/diagnostics/etw/3405-encrypteddataprocessingstart.md)|詳細|暗号化されたデータの処理を開始しました。|セキュリティ|  
|[3406 - EncryptedDataProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/3406-encrypteddataprocessingsuccess.md)|詳細|暗号化されたデータの処理に成功しました。|セキュリティ|  
|[3407 - HttpPipelineProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3407-httppipelineprocessinboundrequeststart.md)|詳細|http メッセージ ハンドラーは、受信要求の処理を開始しました。|HTTP|  
|[3408 - HttpPipelineBeginProcessInboundRequestStart](../../../../../docs/framework/wcf/diagnostics/etw/3408-httppipelinebeginprocessinboundrequeststart.md)|詳細|http メッセージ ハンドラーは、受信要求の非同期処理を開始しました。|HTTP|  
|[3409 - HttpPipelineProcessInboundRequestStop](../../../../../docs/framework/wcf/diagnostics/etw/3409-httppipelineprocessinboundrequeststop.md)|詳細|http メッセージ ハンドラーは、受信要求の処理を完了しました。|HTTP|  
|[3410 - HttpPipelineFaulted](../../../../../docs/framework/wcf/diagnostics/etw/3410-httppipelinefaulted.md)|警告|http メッセージ ハンドラーに障害があります。|HTTP|  
|[3411 - HttpPipelineTimeoutException](../../../../../docs/framework/wcf/diagnostics/etw/3411-httppipelinetimeoutexception.md)|Error|WebSocket の接続がタイムアウトしました。|HTTP|  
|[3412 - HttpPipelineProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3412-httppipelineprocessresponsestart.md)|詳細|http メッセージ ハンドラーは、応答の処理を開始しました。|HTTP|  
|[3413 - HttpPipelineBeginProcessResponseStart](../../../../../docs/framework/wcf/diagnostics/etw/3413-httppipelinebeginprocessresponsestart.md)|詳細|http メッセージ ハンドラーは、応答の非同期処理を開始しました。|HTTP|  
|[3414 - HttpPipelineProcessResponseStop](../../../../../docs/framework/wcf/diagnostics/etw/3414-httppipelineprocessresponsestop.md)|詳細|http メッセージ ハンドラーは、応答の処理を完了しました。|HTTP|  
|[3415 - WebSocketConnectionRequestSendStart](../../../../../docs/framework/wcf/diagnostics/etw/3415-websocketconnectionrequestsendstart.md)|詳細|'%1' への WebSocket 接続要求の送信を開始します。|HTTP|  
|[3416 - WebSocketConnectionRequestSendStop](../../../../../docs/framework/wcf/diagnostics/etw/3416-websocketconnectionrequestsendstop.md)|詳細|WebSocketId:%1 の接続要求を送信しました。|HTTP|  
|[3417 - WebSocketConnectionAcceptStart](../../../../../docs/framework/wcf/diagnostics/etw/3417-websocketconnectionacceptstart.md)|詳細|WebSocket 接続の受け入れを開始します。|HTTP|  
|[3418 - WebSocketConnectionAccepted](../../../../../docs/framework/wcf/diagnostics/etw/3418-websocketconnectionaccepted.md)|詳細|WebSocketId:%1 の接続を受け入れました。|HTTP|  
|[3419 - WebSocketConnectionDeclined](../../../../../docs/framework/wcf/diagnostics/etw/3419-websocketconnectiondeclined.md)|Error|WebSocket 接続が状態コード '%1' で拒否されました|HTTP|  
|[3420 - WebSocketConnectionFailed](../../../../../docs/framework/wcf/diagnostics/etw/3420-websocketconnectionfailed.md)|Error|WebSocket 接続要求が失敗しました: '%1'|HTTP|  
|[3421 - WebSocketConnectionAborted](../../../../../docs/framework/wcf/diagnostics/etw/3421-websocketconnectionaborted.md)|Error|WebSocketId:%1 の接続が中止されました。|HTTP|  
|[3422 - WebSocketAsyncWriteStart](../../../../../docs/framework/wcf/diagnostics/etw/3422-websocketasyncwritestart.md)|詳細|WebSocketId:%1 が '%3' に '%2' バイトを書き込んでいます。|HTTP|  
|[3423 - WebSocketAsyncWriteStop](../../../../../docs/framework/wcf/diagnostics/etw/3423-websocketasyncwritestop.md)|詳細|WebSocketId:%1 が非同期書き込みを停止します。|HTTP|  
|[3424 - WebSocketAsyncReadStart](../../../../../docs/framework/wcf/diagnostics/etw/3424-websocketasyncreadstart.md)|詳細|WebSocketId:%1 が読み取りを開始します。|HTTP|  
|[3425 - WebSocketAsyncReadStop](../../../../../docs/framework/wcf/diagnostics/etw/3425-websocketasyncreadstop.md)|詳細|WebSocketId:%1 が '%3' から '%2' バイトを読み取りました。|HTTP|  
|[3426 - WebSocketCloseSent](../../../../../docs/framework/wcf/diagnostics/etw/3426-websocketclosesent.md)|詳細|WebSocketId:%1 が、終了ステータス '%3' の終了メッセージを '%2' に送信しています。|HTTP|  
|[3427 - WebSocketCloseOutputSent](../../../../../docs/framework/wcf/diagnostics/etw/3427-websocketcloseoutputsent.md)|詳細|WebSocketId:%1 が、終了ステータス '%3' の終了出力メッセージを '%2' に送信しています。|HTTP|  
|[3428 - WebSocketConnectionClosed](../../../../../docs/framework/wcf/diagnostics/etw/3428-websocketconnectionclosed.md)|詳細|WebSocketId:%1 の接続を終了しました。|HTTP|  
|[3429 - WebSocketCloseStatusReceived](../../../../../docs/framework/wcf/diagnostics/etw/3429-websocketclosestatusreceived.md)|詳細|WebSocketId:%1 が、状態 '%2' の接続終了メッセージを受信しました。|HTTP|  
|[3430 - WebSocketUseVersionFromClientWebSocketFactory](../../../../../docs/framework/wcf/diagnostics/etw/3430-websocketuseversionfromclientwebsocketfactory.md)|詳細|型 '%1' のクライアント WebSocket ファクトリから WebSocketVersion を使用しています。|HTTP|  
|[3431 - WebSocketCreateClientWebSocketWithFactory](../../../../../docs/framework/wcf/diagnostics/etw/3431-websocketcreateclientwebsocketwithfactory.md)|詳細|型 '%1' のファクトリでクライアント WebSocket を作成しています。|HTTP|  
|[3553 - XamlServicesLoadStart](../../../../../docs/framework/wcf/diagnostics/etw/3553-xamlservicesloadstart.md)|情報|XamlServicesLoad が開始します|WebHost|  
|[3554 - XamlServicesLoadStop](../../../../../docs/framework/wcf/diagnostics/etw/3554-xamlservicesloadstop.md)|情報|XamlServicesLoad が停止します|WebHost|  
|[3555 - CreateWorkflowServiceHostStart](../../../../../docs/framework/wcf/diagnostics/etw/3555-createworkflowservicehoststart.md)|情報|CreateWorkflowServiceHost が開始します|WebHost|  
|[3556 - CreateWorkflowServiceHostStop](../../../../../docs/framework/wcf/diagnostics/etw/3556-createworkflowservicehoststop.md)|情報|CreateWorkflowServiceHost が停止します|WebHost|  
|[3558 - ServiceActivationStart](../../../../../docs/framework/wcf/diagnostics/etw/3558-serviceactivationstart.md)|情報|サービスのアクティブ化を開始します|WebHost|  
|[3559 - ServiceActivationStop](../../../../../docs/framework/wcf/diagnostics/etw/3559-serviceactivationstop.md)|情報|サービスのアクティブ化を停止します|WebHost|  
|[3560 - ServiceActivationAvailableMemory](../../../../../docs/framework/wcf/diagnostics/etw/3560-serviceactivationavailablememory.md)|詳細|使用可能なメモリ (バイト): %1|クォータ|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|情報|ルーティング サービスがクライアント '%1' を終了しています。|RoutingServices|  
|[3800 - RoutingServiceClosingClient](../../../../../docs/framework/wcf/diagnostics/etw/3800-routingserviceclosingclient.md)|警告|ルーティング サービスのクライアント '%1' が途中終了しました。|RoutingServices|  
|[3802 - RoutingServiceCompletingOneWay](../../../../../docs/framework/wcf/diagnostics/etw/3802-routingservicecompletingoneway.md)|情報|ルーティング サービスの一方向メッセージを完了しています。|RoutingServices|  
|[3803 - RoutingServiceProcessingFailure](../../../../../docs/framework/wcf/diagnostics/etw/3803-routingserviceprocessingfailure.md)|Error|アドレス '%1' のエンドポイントでメッセージを処理しているときにルーティング サービスでエラーが発生しました。|RoutingServices|  
|[3804 - RoutingServiceCreatingClientForEndpoint](../../../../../docs/framework/wcf/diagnostics/etw/3804-routingservicecreatingclientforendpoint.md)|情報|ルーティング サービスが、エンドポイント: '%1' のクライアントを作成しています。|RoutingServices|  
|[3805 - RoutingServiceDisplayConfig](../../../../../docs/framework/wcf/diagnostics/etw/3805-routingservicedisplayconfig.md)|詳細|ルーティング サービスは、RouteOnHeadersOnly: %1、SoapProcessingEnabled: %2、EnsureOrderedDispatch: %3 に構成されています。|RoutingServices|  
|[3807 - RoutingServiceCompletingTwoWay](../../../../../docs/framework/wcf/diagnostics/etw/3807-routingservicecompletingtwoway.md)|情報|ルーティング サービスの要求応答メッセージを完了しています。|RoutingServices|  
|[3809 - RoutingServiceMessageRoutedToEndpoints](../../../../../docs/framework/wcf/diagnostics/etw/3809-routingservicemessageroutedtoendpoints.md)|詳細|ルーティング サービスにより、ID: '%1' のメッセージが %2 エンドポイント リストにルーティングされました。|RoutingServices|  
|[3810 - RoutingServiceConfigurationApplied](../../../../../docs/framework/wcf/diagnostics/etw/3810-routingserviceconfigurationapplied.md)|情報|新しい RoutingConfiguration がルーティング サービスに適用されました。|RoutingServices|  
|[3815 - RoutingServiceProcessingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3815-routingserviceprocessingmessage.md)|情報|ルーティング サービスが、トランザクション: %4 で受信された ID: '%1'、アクション: '%2'、着信 URL: '%3' のメッセージを処理しています。|RoutingServices|  
|[3816 - RoutingServiceTransmittingMessage](../../../../../docs/framework/wcf/diagnostics/etw/3816-routingservicetransmittingmessage.md)|情報|ルーティング サービスが、ID: '%1' [operation %2] のメッセージを '%3' に転送しています。|RoutingServices|  
|[3817 - RoutingServiceCommittingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3817-routingservicecommittingtransaction.md)|情報|ルーティング サービスが、ID: '%1' のトランザクションをコミットしています。|RoutingServices|  
|[3818 - RoutingServiceDuplexCallbackException](../../../../../docs/framework/wcf/diagnostics/etw/3818-routingserviceduplexcallbackexception.md)|Error|ルーティング サービスのコンポーネント %1 で二重コールバックの例外が発生しました。|RoutingServices|  
|[3819 - RoutingServiceMovedToBackup](../../../../../docs/framework/wcf/diagnostics/etw/3819-routingservicemovedtobackup.md)|情報|ID: '%1' [operation %2] のルーティング サービス メッセージがバックアップ エンドポイント '%3' に移動されました。|RoutingServices|  
|[3820 - RoutingServiceCreatingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3820-routingservicecreatingtransaction.md)|情報|ルーティング サービスが、メッセージを処理するために ID '%1' の新しいトランザクションを作成しました。|RoutingServices|  
|[3821 - RoutingServiceCloseFailed](../../../../../docs/framework/wcf/diagnostics/etw/3821-routingserviceclosefailed.md)|警告|発信クライアント '%1' を終了しているときにルーティング サービスでエラーが発生しました。|RoutingServices|  
|[3822 - RoutingServiceSendingResponse](../../../../../docs/framework/wcf/diagnostics/etw/3822-routingservicesendingresponse.md)|情報|ルーティング サービスが、Action '%1' を含む応答メッセージを返送しています。|RoutingServices|  
|[3823 - RoutingServiceSendingFaultResponse](../../../../../docs/framework/wcf/diagnostics/etw/3823-routingservicesendingfaultresponse.md)|警告|ルーティング サービスが、Action '%1' を含むエラー応答メッセージを返送しています。|RoutingServices|  
|[3824 - RoutingServiceCompletingReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3824-routingservicecompletingreceivecontext.md)|詳細|ルーティング サービスが、ID: '%1' のメッセージに対して ReceiveContext.Complete を呼び出しています。|RoutingServices|  
|[3825 - RoutingServiceAbandoningReceiveContext](../../../../../docs/framework/wcf/diagnostics/etw/3825-routingserviceabandoningreceivecontext.md)|警告|ルーティング サービスが、ID: '%1' のメッセージに対して ReceiveContext.Abandon を呼び出しています。|RoutingServices|  
|[3826 - RoutingServiceUsingExistingTransaction](../../../../../docs/framework/wcf/diagnostics/etw/3826-routingserviceusingexistingtransaction.md)|詳細|ルーティング サービスは、既存のトランザクション '%1' を使用してメッセージを送信します。|RoutingServices|  
|[3827 - RoutingServiceTransmitFailed](../../../../../docs/framework/wcf/diagnostics/etw/3827-routingservicetransmitfailed.md)|警告|'%1' への送信中にルーティング サービスでエラーが発生しました。|RoutingServices|  
|[3828 - RoutingServiceFilterTableMatchStart](../../../../../docs/framework/wcf/diagnostics/etw/3828-routingservicefiltertablematchstart.md)|情報|ルーティング サービス MessageFilterTable の照合が開始します。|RoutingServices|  
|[3829 - RoutingServiceFilterTableMatchStop](../../../../../docs/framework/wcf/diagnostics/etw/3829-routingservicefiltertablematchstop.md)|情報|ルーティング サービス MessageFilterTable の照合が停止します。|RoutingServices|  
|[3830 - RoutingServiceAbortingChannel](../../../../../docs/framework/wcf/diagnostics/etw/3830-routingserviceabortingchannel.md)|詳細|ルーティング サービスがチャネル '%1' で中止を呼び出しています。|RoutingServices|  
|[3831 - RoutingServiceHandledException](../../../../../docs/framework/wcf/diagnostics/etw/3831-routingservicehandledexception.md)|詳細|ルーティング サービスが例外を処理しました。|RoutingServices|  
|[3832 - RoutingServiceTransmitSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/3832-routingservicetransmitsucceeded.md)|情報|ルーティング サービスが、ID: '%1 [operation %2] のメッセージを '%3' に正常に送信しました。|RoutingServices|  
|[4001 - TransportListenerSessionsReceived](../../../../../docs/framework/wcf/diagnostics/etw/4001-transportlistenersessionsreceived.md)|詳細|'%1' でトランスポート リスナー セッションを受信しました|ActivationServices|  
|[4002 - FailFastException](../../../../../docs/framework/wcf/diagnostics/etw/4002-failfastexception.md)|重大|FailFastException。|ActivationServices|  
|[4003 - ServiceStartPipeError](../../../../../docs/framework/wcf/diagnostics/etw/4003-servicestartpipeerror.md)|Error|サービス開始パイプ エラー。|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|詳細|セッション ディスパッチを開始しました。|ActivationServices|  
|[4008 - DispatchSessionStart](../../../../../docs/framework/wcf/diagnostics/etw/4008-dispatchsessionstart.md)|警告|'%1' のセッション ディスパッチに失敗しました。保留セッション キューがいっぱいです。保留中の項目が '%2' 個あります。|ActivationServices|  
|[4011 - MessageQueueRegisterStart](../../../../../docs/framework/wcf/diagnostics/etw/4011-messagequeueregisterstart.md)|詳細|メッセージ キューの登録を開始します。|ActivationServices|  
|[4012 - MessageQueueRegisterAbort](../../../../../docs/framework/wcf/diagnostics/etw/4012-messagequeueregisterabort.md)|Error|URI:'%2' のメッセージ キューの登録が状態:'%1' で中止されました。|ActivationServices|  
|[4013 - MessageQueueUnregisterSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4013-messagequeueunregistersucceeded.md)|詳細|URI:'%1' のメッセージ キューの登録解除に成功しました。|ActivationServices|  
|[4014 - MessageQueueRegisterFailed](../../../../../docs/framework/wcf/diagnostics/etw/4014-messagequeueregisterfailed.md)|Error|URI:'%1' のメッセージ キューの登録が状態:'%2' で失敗しました。|ActivationServices|  
|[4015 - MessageQueueRegisterCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4015-messagequeueregistercompleted.md)|情報|URI '%1' のメッセージ キューの登録が完了しました。|ActivationServices|  
|[4016 - MessageQueueDuplicatedSocketError](../../../../../docs/framework/wcf/diagnostics/etw/4016-messagequeueduplicatedsocketerror.md)|Error|メッセージ キューがソケットの複製に失敗しました。|ActivationServices|  
|[4019 - MessageQueueDuplicatedSocketComplete](../../../../../docs/framework/wcf/diagnostics/etw/4019-messagequeueduplicatedsocketcomplete.md)|詳細|MessageQueueDuplicatedSocketComplete|ActivationServices|  
|[4020 - TcpTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4020-tcptransportlistenerlisteningstart.md)|詳細|TCP トランスポート リスナーが URI: '%1' でリッスンを開始しています。|ActivationServices|  
|[4021 - TcpTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4021-tcptransportlistenerlisteningstop.md)|詳細|TCP トランスポート リスナーがリッスンしています。|ActivationServices|  
|[4022 - WebhostUnregisterProtocolFailed](../../../../../docs/framework/wcf/diagnostics/etw/4022-webhostunregisterprotocolfailed.md)|Error|エラー コード:%1|ActivationServices|  
|[4023 - WasCloseAllListenerChannelInstancesCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4023-wasclosealllistenerchannelinstancescompleted.md)|情報|WAS がすべてのリスナー チャネル インスタンスのクローズを完了しました。|ActivationServices|  
|[4024 - WasCloseAllListenerChannelInstancesFailed](../../../../../docs/framework/wcf/diagnostics/etw/4024-wasclosealllistenerchannelinstancesfailed.md)|Error|エラー コード:%1|ActivationServices|  
|[4025 - OpenListenerChannelInstanceFailed](../../../../../docs/framework/wcf/diagnostics/etw/4025-openlistenerchannelinstancefailed.md)|Error|エラー コード:%1|ActivationServices|  
|[4026 - WasConnected](../../../../../docs/framework/wcf/diagnostics/etw/4026-wasconnected.md)|詳細|WAS が接続されました。|ActivationServices|  
|[4027 - WasDisconnected](../../../../../docs/framework/wcf/diagnostics/etw/4027-wasdisconnected.md)|詳細|WAS の接続が解除されました。|ActivationServices|  
|[4028 - PipeTransportListenerListeningStart](../../../../../docs/framework/wcf/diagnostics/etw/4028-pipetransportlistenerlisteningstart.md)|詳細|パイプ トランスポート リスナーが URI:%1 でリッスンを開始します。|ActivationServices|  
|[4029 - PipeTransportListenerListeningStop](../../../../../docs/framework/wcf/diagnostics/etw/4029-pipetransportlistenerlisteningstop.md)|詳細|パイプ トランスポート リスナーがリッスンを停止します。|ActivationServices|  
|[4030 - DispatchSessionSuccess](../../../../../docs/framework/wcf/diagnostics/etw/4030-dispatchsessionsuccess.md)|情報|セッション ディスパッチに成功しました。|ActivationServices|  
|[4031 - DispatchSessionFailed](../../../../../docs/framework/wcf/diagnostics/etw/4031-dispatchsessionfailed.md)|Error|セッション ディスパッチに失敗しました。|ActivationServices|  
|[4032 - WasConnectionTimedout](../../../../../docs/framework/wcf/diagnostics/etw/4032-wasconnectiontimedout.md)|重大|WAS の接続がタイムアウトしました。|ActivationServices|  
|[4033 - RoutingTableLookupStart](../../../../../docs/framework/wcf/diagnostics/etw/4033-routingtablelookupstart.md)|詳細|ルーティング テーブルの参照を開始しました。|ActivationServices|  
|[4034 - RoutingTableLookupStop](../../../../../docs/framework/wcf/diagnostics/etw/4034-routingtablelookupstop.md)|詳細|ルーティング テーブルの参照が完了しました。|ActivationServices|  
|[4035 - PendingSessionQueueRatio](../../../../../docs/framework/wcf/diagnostics/etw/4035-pendingsessionqueueratio.md)|詳細|保留セッション キューの比率: %1/%2|クォータ|  
|[4600 - MessageLogEventSizeExceeded](../../../../../docs/framework/wcf/diagnostics/etw/4600-messagelogeventsizeexceeded.md)|警告|メッセージが ETW イベントのサイズを上回っているため、メッセージをログに記録できませんでした|WCFMessageLogging|  
|[4801 - DiscoveryClientInClientChannelFailedToClose](../../../../../docs/framework/wcf/diagnostics/etw/4801-discoveryclientinclientchannelfailedtoclose.md)|警告|DiscoveryClientChannel 内で作成された DiscoveryClient を閉じることができず、異常終了しました。|探索|  
|[4802 - DiscoveryClientProtocolExceptionSuppressed](../../../../../docs/framework/wcf/diagnostics/etw/4802-discoveryclientprotocolexceptionsuppressed.md)|情報|DiscoveryClient を閉じているときに ProtocolException が抑制されました。 その理由として、DiscoveryService がまだ DiscoveryClient に応答を送信しようとしていることが考えられます。|探索|  
|[4803 - DiscoveryClientReceivedMulticastSuppression](../../../../../docs/framework/wcf/diagnostics/etw/4803-discoveryclientreceivedmulticastsuppression.md)|情報|DiscoveryClient は DiscoveryProxy からマルチキャスト抑制メッセージを受け取りました。|探索|  
|[4804 - DiscoveryMessageReceivedAfterOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4804-discoverymessagereceivedafteroperationcompleted.md)|情報|messageId='%2' の %1 メッセージは、対応する %3 操作が完了したため、DiscoveryClient によってドロップされました。|探索|  
|[4805 - DiscoveryMessageWithInvalidContent](../../../../../docs/framework/wcf/diagnostics/etw/4805-discoverymessagewithinvalidcontent.md)|警告|messageId='%2' の %1 メッセージは、無効なコンテンツがあったため、ドロップされました。|探索|  
|[4806 - DiscoveryMessageWithInvalidRelatesToOrOperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/4806-discoverymessagewithinvalidrelatestooroperationcompleted.md)|警告|messageId='%2' および relatesTo='%3' の %1 メッセージは、対応する %4 操作が完了したか、relatesTo 値が無効であるため、DiscoveryClient によってドロップされました。|探索|  
|[4807 - DiscoveryMessageWithInvalidReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4807-discoverymessagewithinvalidreplyto.md)|警告|messageId='%1' の探索要求メッセージは、無効な ReplyTo アドレスがあったため、ドロップされました。|探索|  
|[4808 - DiscoveryMessageWithNoContent](../../../../../docs/framework/wcf/diagnostics/etw/4808-discoverymessagewithnocontent.md)|警告|%1 メッセージは、コンテンツがなかったため、ドロップされました。|探索|  
|[4809 - DiscoveryMessageWithNullMessageId](../../../../../docs/framework/wcf/diagnostics/etw/4809-discoverymessagewithnullmessageid.md)|警告|%1 メッセージは、メッセージ ヘッダーに必要な MessageId プロパティが含まれていなかったため、ドロップされました。|探索|  
|[4810 - DiscoveryMessageWithNullMessageSequence](../../../../../docs/framework/wcf/diagnostics/etw/4810-discoverymessagewithnullmessagesequence.md)|警告|messageId='%2' の %1 メッセージは、DiscoveryMessageSequence プロパティがなかったため、DiscoveryClient によってドロップされました。|探索|  
|[4811 - DiscoveryMessageWithNullRelatesTo](../../../../../docs/framework/wcf/diagnostics/etw/4811-discoverymessagewithnullrelatesto.md)|警告|messageId='%2' の %1 メッセージは、メッセージ ヘッダーに必要な RelatesTo プロパティが含まれていなかったため、DiscoveryClient によってドロップされました。|探索|  
|[4812 - DiscoveryMessageWithNullReplyTo](../../../../../docs/framework/wcf/diagnostics/etw/4812-discoverymessagewithnullreplyto.md)|警告|messageId='%1' の探索要求メッセージは、ReplyTo アドレスがなかったため、ドロップされました。|探索|  
|[4813 - DuplicateDiscoveryMessage](../../../../../docs/framework/wcf/diagnostics/etw/4813-duplicatediscoverymessage.md)|警告|messageId='%2' の %1 メッセージは、重複していたため、ドロップされました。|探索|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|情報|EndpointAddress='%1' および ListenUri='%2' のエンドポイントの探索が無効になりました。|探索|  
|[4814 - EndpointDiscoverabilityDisabled](../../../../../docs/framework/wcf/diagnostics/etw/4814-endpointdiscoverabilitydisabled.md)|情報|EndpointAddress='%1' および ListenUri='%2' のエンドポイントの探索が有効になりました。|探索|  
|[4816 - FindInitiatedInDiscoveryClientChannel](../../../../../docs/framework/wcf/diagnostics/etw/4816-findinitiatedindiscoveryclientchannel.md)|詳細|エンドポイントを探索するために、Find 操作が DiscoveryClientChannel で開始されました。|探索|  
|[4817 - InnerChannelCreationFailed](../../../../../docs/framework/wcf/diagnostics/etw/4817-innerchannelcreationfailed.md)|警告|DiscoveryClientChannel は、EndpointAddress='%1' および Via='%2' の探索されたエンドポイントを使用して、チャネルを作成できませんでした。 DiscoveryClientChannel は、次に使用可能な探索されたエンドポイントを使用します。|探索|  
|[4818 - InnerChannelOpenFailed](../../../../../docs/framework/wcf/diagnostics/etw/4818-innerchannelopenfailed.md)|警告|DiscoveryClientChannel は、EndpointAddress='%1' および Via='%2' の探索されたエンドポイントを使用して、チャネルを開くことができませんでした。 DiscoveryClientChannel は、次に使用可能な探索されたエンドポイントを使用します。|探索|  
|[4819 - InnerChannelOpenSucceeded](../../../../../docs/framework/wcf/diagnostics/etw/4819-innerchannelopensucceeded.md)|情報|DiscoveryClientChannel は正常にエンドポイントを探索し、それを使用してチャネルを開きました。 クライアントは EndpointAddress='%1' および Via='%2' を使用して、サービスに接続されています。|探索|  
|[4820 - SynchronizationContextReset](../../../../../docs/framework/wcf/diagnostics/etw/4820-synchronizationcontextreset.md)|情報|SynchronizationContext は DiscoveryClientChannel によって、元の値 %1 にリセットされました。|探索|  
|[4821 - SynchronizationContextSetToNull](../../../../../docs/framework/wcf/diagnostics/etw/4821-synchronizationcontextsettonull.md)|情報|SynchronizationContext は、Find 操作を開始する前に、DiscoveryClientChannel によって NULL に設定されました。|探索|  
|[5001 - DCSerializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5001-dcserializewithsurrogatestart.md)|詳細|DataContract のサロゲートによる %1 のシリアル化を開始します。|シリアル化|  
|[5002 - DCSerializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5002-dcserializewithsurrogatestop.md)|詳細|DataContract のサロゲートによるシリアル化を停止します。|シリアル化|  
|[5003 - DCDeserializeWithSurrogateStart](../../../../../docs/framework/wcf/diagnostics/etw/5003-dcdeserializewithsurrogatestart.md)|詳細|DataContract のサロゲートによる %1 のシリアル化解除を開始します。|シリアル化|  
|[5004 - DCDeserializeWithSurrogateStop](../../../../../docs/framework/wcf/diagnostics/etw/5004-dcdeserializewithsurrogatestop.md)|詳細|DataContract のサロゲートによるシリアル化解除を停止します。|シリアル化|  
|[5005 - ImportKnownTypesStart](../../../../../docs/framework/wcf/diagnostics/etw/5005-importknowntypesstart.md)|詳細|ImportKnownTypes を開始します。|シリアル化|  
|[5006 - ImportKnownTypesStop](../../../../../docs/framework/wcf/diagnostics/etw/5006-importknowntypesstop.md)|詳細|ImportKnownTypes を停止します。|シリアル化|  
|[5007 - DCResolverResolve](../../../../../docs/framework/wcf/diagnostics/etw/5007-dcresolverresolve.md)|詳細|DataContract リゾルバーが %1 の解決を開始します。|シリアル化|  
|[5008 - DCGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5008-dcgenwriterstart.md)|詳細|DataContract の %2 の %1 ライターの生成を開始します。|シリアル化|  
|[5009 - DCGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5009-dcgenwriterstop.md)|詳細|DataContract のライターの生成を停止します。|シリアル化|  
|[5010 - DCGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5010-dcgenreaderstart.md)|詳細|DataContract の %2 の %1 リーダーの生成を開始します。|シリアル化|  
|[5011 - DCGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5011-dcgenreaderstop.md)|詳細|DataContract の生成を停止します。|シリアル化|  
|[5012 - DCJsonGenReaderStart](../../../../../docs/framework/wcf/diagnostics/etw/5012-dcjsongenreaderstart.md)|詳細|Json の %2 の %1 リーダーの生成を開始します。|シリアル化|  
|[5013 - DCJsonGenReaderStop](../../../../../docs/framework/wcf/diagnostics/etw/5013-dcjsongenreaderstop.md)|詳細|Json のリーダーの生成を停止します。|シリアル化|  
|[5014 - DCJsonGenWriterStart](../../../../../docs/framework/wcf/diagnostics/etw/5014-dcjsongenwriterstart.md)|詳細|Json の %2 の %1 ライターの生成を開始します。|シリアル化|  
|[5015 - DCJsonGenWriterStop](../../../../../docs/framework/wcf/diagnostics/etw/5015-dcjsongenwriterstop.md)|詳細|Json のライターの生成を停止します。|シリアル化|  
|[5016 - GenXmlSerializableStart](../../../../../docs/framework/wcf/diagnostics/etw/5016-genxmlserializablestart.md)|詳細|'%1' の XML シリアル化が可能な要素の生成を開始します。|シリアル化|  
|[5017 - GenXmlSerializableStop](../../../../../docs/framework/wcf/diagnostics/etw/5017-genxmlserializablestop.md)|詳細|XML シリアル化が可能な要素の生成を停止します。|シリアル化|  
|[5203 - JsonMessageDecodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5203-jsonmessagedecodingstart.md)|詳細|JsonMessageEncoder がメッセージのデコードを開始しました。|チャネル|  
|[5204 - JsonMessageEncodingStart](../../../../../docs/framework/wcf/diagnostics/etw/5204-jsonmessageencodingstart.md)|詳細|JsonMessageEncoder がメッセージのエンコードを開始しました。|チャネル|  
|[5402 - TokenValidationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5402-tokenvalidationstarted.md)|詳細|SecurityToken (型 '%1'、ID '%2') の検証を開始しました。|セキュリティ|  
|[5403 - TokenValidationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5403-tokenvalidationsuccess.md)|詳細|SecurityToken (型 '%1'、ID '%2') の検証に成功しました。|セキュリティ|  
|[5404 - TokenValidationFailure](../../../../../docs/framework/wcf/diagnostics/etw/5404-tokenvalidationfailure.md)|Error|SecurityToken (型 '%1'、ID '%2') の検証に失敗しました。 %3|セキュリティ|  
|[5405 - GetIssuerNameSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5405-getissuernamesuccess.md)|詳細|トークン ID: %2 からの発行者名: %1 の取得に成功しました。|セキュリティ|  
|[5406 - GetIssuerNameFailure](../../../../../docs/framework/wcf/diagnostics/etw/5406-getissuernamefailure.md)|Error|トークン ID: %1 からの発行者名の取得に失敗しました。|セキュリティ|  
|[5600 - FederationMessageProcessingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5600-federationmessageprocessingstarted.md)|詳細|フェデレーション メッセージの処理を開始しました。|セキュリティ|  
|[5601 - FederationMessageProcessingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5601-federationmessageprocessingsuccess.md)|詳細|フェデレーション メッセージの処理に成功しました。|セキュリティ|  
|[5602 - FederationMessageCreationStarted](../../../../../docs/framework/wcf/diagnostics/etw/5602-federationmessagecreationstarted.md)|詳細|フォーム ポストからのフェデレーション メッセージの作成を開始しました。|セキュリティ|  
|[5603 - FederationMessageCreationSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5603-federationmessagecreationsuccess.md)|詳細|フォーム ポストからのフェデレーション メッセージの作成に成功しました。|セキュリティ|  
|[5604 - SessionCookieReadingStarted](../../../../../docs/framework/wcf/diagnostics/etw/5604-sessioncookiereadingstarted.md)|詳細|セッション クッキーからのセッション トークンの読み取りを開始しました。|セキュリティ|  
|[5605 - SessionCookieReadingSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5605-sessioncookiereadingsuccess.md)|詳細|セッション クッキーからのセッション トークンの読み取りに成功しました。|セキュリティ|  
|[5606 - PrincipalSettingFromSessionTokenStarted](../../../../../docs/framework/wcf/diagnostics/etw/5606-principalsettingfromsessiontokenstarted.md)|詳細|セッション トークンからのプリンシパルの設定を開始しました。|セキュリティ|  
|[5607 - PrincipalSettingFromSessionTokenSuccess](../../../../../docs/framework/wcf/diagnostics/etw/5607-principalsettingfromsessiontokensuccess.md)|詳細|セッション トークンからのプリンシパルの設定に成功しました。|セキュリティ|  
|[57393 - AppDomainUnload](../../../../../docs/framework/wcf/diagnostics/etw/57393-appdomainunload.md)|情報|AppDomain をアンロードしています。 AppDomain.FriendlyName %1、ProcessName %2、ProcessId %3。|インフラストラクチャ|  
|[57394 - HandledException](../../../../../docs/framework/wcf/diagnostics/etw/57394-handledexception.md)|情報|例外を処理しています。|インフラストラクチャ|  
|[57395 - ShipAssertExceptionMessage](../../../../../docs/framework/wcf/diagnostics/etw/57395-shipassertexceptionmessage.md)|Error|予期しないエラーが発生しました。 アプリケーションではこのエラーを処理することはできません。 診断上の目的から、次の英語のメッセージがエラーに関連付けられています: %1。|インフラストラクチャ|  
|[57396 - ThrowingException](../../../../../docs/framework/wcf/diagnostics/etw/57396-throwingexception.md)|警告|例外をスローしています。 発生元 %1。|インフラストラクチャ|  
|[57397 - UnhandledException](../../../../../docs/framework/wcf/diagnostics/etw/57397-unhandledexception.md)|重大|ハンドルされていない例外です。|インフラストラクチャ|  
|[57399 - TraceCodeEventLogCritical](../../../../../docs/framework/wcf/diagnostics/etw/57399-tracecodeeventlogcritical.md)|重大|イベント ログに書き込みました。|インフラストラクチャ|  
|[57400 - TraceCodeEventLogError](../../../../../docs/framework/wcf/diagnostics/etw/57400-tracecodeeventlogerror.md)|Error|イベント ログに書き込みました。|インフラストラクチャ|  
|[57401 - TraceCodeEventLogInfo](../../../../../docs/framework/wcf/diagnostics/etw/57401-tracecodeeventloginfo.md)|情報|イベント ログに書き込みました。|インフラストラクチャ|  
|[57402 - TraceCodeEventLogVerbose](../../../../../docs/framework/wcf/diagnostics/etw/57402-tracecodeeventlogverbose.md)|詳細|イベント ログに書き込みました。|インフラストラクチャ|  
|[57403 - TraceCodeEventLogWarning](../../../../../docs/framework/wcf/diagnostics/etw/57403-tracecodeeventlogwarning.md)|警告|イベント ログに書き込みました。|インフラストラクチャ|  
|[57404 - HandledExceptionWarning](../../../../../docs/framework/wcf/diagnostics/etw/57404-handledexceptionwarning.md)|警告|例外を処理しています。|インフラストラクチャ|  
|[62326 - HttpHandlerPickedForUrl](../../../../../docs/framework/wcf/diagnostics/etw/62326-httphandlerpickedforurl.md)|情報|URL '%1' は、ルート要素型 '%2' の XAML ドキュメントをホストします。 この URL に対して行われるすべての要求を処理するために、HTTP ハンドラー型 '%3' が選択されています。|WebHost|
