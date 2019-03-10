---
title: 追跡イベントのリファレンス
ms.date: 03/30/2017
ms.assetid: c1c1ee87-f80a-449b-acd0-50d81eef116e
ms.openlocfilehash: 5b3bba83b3c6c7ab27c9470213b7675f7e107c7e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/09/2019
ms.locfileid: "57712215"
---
# <a name="tracking-events-reference"></a>追跡イベントのリファレンス

  [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] のワークフローが実行中にライフタイムのさまざまなステージを移行するとき、追跡イベントが発生します。 ホストはこれらのイベントに定期受信し、ライフタイム中のワークフローの進行状況について最新の状態に保ちます。 ここでは、発生する追跡イベントについて説明します。  
  
## <a name="event-reference"></a>イベント リファレンス  
  
|イベント ID|イベント レベル|イベント メッセージ|キーワード|  
|--------------|-----------------|-------------------|--------------|  
|[100 - WorkflowInstanceRecord](100-workflowinstancerecord.md)|情報|TrackRecord= WorkflowInstanceRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、State = %5、Annotations = %6、ProfileName = %7|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[101 - WorkflowInstanceUnhandledExceptionRecord](101-workflowinstanceunhandledexceptionrecord.md)|Error|TrackRecord = WorkflowInstanceUnhandledExceptionRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、SourceName = %5、SourceId = %6、SourceInstanceId = %7、SourceTypeName=%8、Exception=%9、Annotations= %10、ProfileName = %11|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[102 - WorkflowInstanceAbortedRecord](102-workflowinstanceabortedrecord.md)|警告|TrackRecord = WorkflowInstanceAbortedRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[103 - ActivityStateRecord](103-activitystaterecord.md)|情報|TrackRecord = ActivityStateRecord、InstanceID = %1、RecordNumber=%2、EventTime=%3、State = %4、Name=%5、ActivityId=%6、ActivityInstanceId=%7、ActivityTypeName=%8、Arguments=%9、Variables=%10、Annotations=%11、ProfileName = %12|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[104 - ActivityScheduledRecord](104-activityscheduledrecord.md)|情報|TrackRecord = ActivityScheduledRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、Name = %4、ActivityId = %5、ActivityInstanceId = %6、ActivityTypeName = %7、ChildActivityName = %8、ChildActivityId = %9、ChildActivityInstanceId = %10、ChildActivityTypeName =%11、Annotations=%12、ProfileName = %13|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[105 - FaultPropagationRecord](105-faultpropagationrecord.md)|警告|TrackRecord = FaultPropagationRecord、InstanceID=%1、RecordNumber=%2、EventTime=%3、FaultSourceActivityName=%4、FaultSourceActivityId=%5、FaultSourceActivityInstanceId=%6、FaultSourceActivityTypeName=%7、FaultHandlerActivityName=%8、FaultHandlerActivityId = %9、FaultHandlerActivityInstanceId =%10、FaultHandlerActivityTypeName=%11、Fault=%12、IsFaultSource=%13、Annotations=%14、ProfileName = %15|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[106 - CancelRequestRecord](106-cancelrequestrecord.md)|情報|TrackRecord = CancelRequestedRecord、InstanceID=%1、RecordNumber=%2、EventTime=%3、Name=%4、ActivityId=%5、ActivityInstanceId=%6、ActivityTypeName = %7、ChildActivityName = %8、ChildActivityId = %9、ChildActivityInstanceId = %10、ChildActivityTypeName =%11、Annotations=%12、ProfileName = %13|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[107 -- BookmarkResumptionRecord](107-bookmarkresumptionrecord.md)|情報|TrackRecord = BookmarkResumptionRecord、InstanceID=%1、RecordNumber=%2,EventTime=%3、Name=%4、SubInstanceID=%5、OwnerActivityName=%6、OwnerActivityId =%7、OwnerActivityInstanceId=%8、OwnerActivityTypeName=%9、Annotations=%10、ProfileName = %11|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[108 - CustomTrackingRecordInfo](108-customtrackingrecordinfo.md)|情報|TrackRecord = CustomTrackingRecord、InstanceID = %1、RecordNumber=%2、EventTime=%3、Name=%4、ActivityName=%5、ActivityId=%6、ActivityInstanceId=%7、ActivityTypeName=%8、Data=%9、Annotations=%10、ProfileName = %11|UserEvents、EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[110 - CustomTrackingRecordWarning](110-customtrackingrecordwarning.md)|警告|TrackRecord = CustomTrackingRecord、InstanceID = %1、RecordNumber=%2、EventTime=%3、Name=%4、ActivityName=%5、ActivityId=%6、ActivityInstanceId=%7、ActivityTypeName=%8、Data=%9、Annotations=%10、ProfileName = %11|UserEvents、EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[111 - CustomTrackingRecordError](111-customtrackingrecorderror.md)|Error|TrackRecord = CustomTrackingRecord、InstanceID = %1、RecordNumber=%2、EventTime=%3、Name=%4、ActivityName=%5、ActivityId=%6、ActivityInstanceId=%7、ActivityTypeName=%8、Data=%9、Annotations=%10、ProfileName = %11|UserEvents、EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[112 - WorkflowInstanceSuspendedRecord](112-workflowinstancesuspendedrecord.md)|情報|TrackRecord = WorkflowInstanceSuspendedRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[113 - WorkflowInstanceTerminatedRecord](113-workflowinstanceterminatedrecord.md)|Error|TrackRecord = WorkflowInstanceTerminatedRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|[114 - WorkflowInstanceRecordWithId](114-workflowinstancerecordwithid.md)|情報|TrackRecord= WorkflowInstanceRecord, InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、State = %5、Annotations = %6、ProfileName = %7、WorkflowDefinitionIdentity = %8|HealthMonitoring、WFTracking|  
|[115 - WorkflowInstanceAbortedRecordWithId](115-workflowinstanceabortedrecordwithid.md)|警告|TrackRecord = WorkflowInstanceAbortedRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7、WorkflowDefinitionIdentity = %8|HealthMonitoring、WFTracking|  
|[116 - WorkflowInstanceSuspendedRecordWithId](116-workflowinstancesuspendedrecordwithid.md)|情報|TrackRecord = WorkflowInstanceSuspendedRecord, InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7、WorkflowDefinitionIdentity = %8|HealthMonitoring、WFTracking|  
|[117 - WorkflowInstanceTerminatedRecordWithId](117-workflowinstanceterminatedrecordwithid.md)|Error|TrackRecord = WorkflowInstanceTerminatedRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、Reason = %5、Annotations = %6、ProfileName = %7、WorkflowDefinitionIdentity = %8|HealthMonitoring、WFTracking|  
|[118 - WorkflowInstanceUnhandledExceptionRecordWithId](118-workflowinstanceunhandledexceptionrecordwithid.md)|Error|TrackRecord = WorkflowInstanceUnhandledExceptionRecord、InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、SourceName = %5、SourceId = %6、SourceInstanceId = %7、SourceTypeName = %8、Exception = %9、Annotations %10、ProfileName = =%11、WorkflowDefinitionIdentity = %12|HealthMonitoring、WFTrackingHealthMonitoring、WFTracking|  
|[119 - WorkflowInstanceUpdatedRecord](119-workflowinstanceupdatedrecord.md)|情報|TrackRecord= WorkflowInstanceUpdatedRecord, InstanceID = %1、RecordNumber = %2、EventTime = %3、ActivityDefinitionId = %4、State = %5、OriginalDefinitionIdentity = %6、UpdatedDefinitionIdentity = %7、Annotations = %8、ProfileName = %9|HealthMonitoring、WFTracking|  
|[225 - TraceCorrelationKeys](225-tracecorrelationkeys.md)|情報|親スコープ '%3' の値 '%2' を使用して相関関係キー '%1' が計算されました。|トラブルシューティング (WF サービス)|  
|[440 - StartSignpostEvent1](440-startsignpostevent.md)|情報|アクティビティの境界|トラブルシューティング (WF サービス)|  
|[441- StopSignpostEvent1](441-stopsignpostevent.md)|情報|アクティビティの境界|トラブルシューティング (WF サービス)|  
|[1001 - WorkflowApplicationCompleted](1001-workflowapplicationcompleted.md)|情報|WorkflowInstance ID: %1 は Closed 状態で完了しました。|WFRuntime|  
|[1002 - WorkflowApplicationTerminated](1002-workflowapplicationterminated.md)|情報|WorkflowApplication ID: %1 は中止されました。 例外により Faulted 状態で完了しました。|WFRuntime|  
|[1003 - WorkflowInstanceCanceled](1003-workflowinstancecanceled.md)|情報|WorkflowInstance ID: %1 は Canceled 状態で完了しました。|WFRuntime|  
|[1004 - WorkflowInstanceAborted](1004-workflowinstanceaborted.md)|情報|WorkflowInstance ID: '%1' は例外により中止されました。|WFRuntime|  
|[1005 - WorkflowApplicationIdled](1005-workflowapplicationidled.md)|情報|WorkflowApplication ID: '%1' がアイドル状態になりました。|WFRuntime|  
|[1006 - WorkflowApplicationUnhandledException](1006-workflowapplicationunhandledexception.md)|Error|WorkflowInstance Id: '%1' にハンドルされない例外が発生しました。  Activity '%2'、DisplayName、例外の発生元: '%3'。  次の動作が行われます。 % 4。|WFRuntime|  
|[1007 - WorkflowApplicationPersisted](1007-workflowapplicationpersisted.md)|情報|WorkflowApplication ID: %1 が永続化されました。|WFRuntime|  
|[1008 - WorkflowApplicationUnloaded](1008-workflowapplicationunloaded.md)|情報|WorkflowInstance ID: '%1' がアンロードされました。|WFRuntime|  
|[1009 - ActivityScheduled](1009-activityscheduled.md)|情報|Parent Activity '%1'、DisplayName: '%2'、InstanceId: '%3' scheduled child Activity '%4'、DisplayName: '%5'、InstanceId: '%6'。|WFRuntime|  
|[1010 - ActivityCompleted](1010-activitycompleted.md)|情報|Parent Activity '%1'、DisplayName: '%2'、InstanceId: '%3' scheduled child Activity '%4'、DisplayName: '%5'、InstanceId: '%6'。|WFRuntime|  
|[1011 - ScheduleExecuteActivityWorkItem](1011-scheduleexecuteactivityworkitem.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して ExecuteActivityWorkItem がスケジュールされました。|WFRuntime|  
|[1012 - StartExecuteActivityWorkItem](1012-startexecuteactivityworkitem.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の ExecuteActivityWorkItem の実行を開始しています。|WFRuntime|  
|[1013 - CompleteExecuteActivityWorkItem](1013-completeexecuteactivityworkitem.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の ExecuteActivityWorkItem が完了しました。|WFRuntime|  
|[1014 - ScheduleCompletionWorkItem](1014-schedulecompletionworkitem.md)|詳細|親 Activity '%1'、DisplayName に対して CompletionWorkItem がスケジュールされました: '%2'、InstanceId: '%3'。  Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。|WFRuntime|  
|[1015 - StartCompletionWorkItem](1015-startcompletionworkitem.md)|詳細|親 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CompletionWorkItem の実行を開始しています。 Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。|WFRuntime|  
|[1016 - CompleteCompletionWorkItem](1016-completecompletionworkitem.md)|詳細|親 Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CompletionWorkItem が完了しました。 Activity '%4'、DisplayName: '%5'、InstanceId: '%6' が完了しました。|WFRuntime|  
|[1017 - ScheduleCancelActivityWorkItem](1017-schedulecancelactivityworkitem.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して CancelActivityWorkItem がスケジュールされました。|WFRuntime|  
|[1018 - StartCancelActivityWorkItem](1018-startcancelactivityworkitem.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CancelActivityWorkItem の実行を開始しています。|WFRuntime|  
|[1019 - CompleteCancelActivityWorkItem](1019-completecancelactivityworkitem.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の CancelActivityWorkItem が完了しました。|WFRuntime|  
|[1020 - CreateBookmark](1020-createbookmark.md)|詳細|Activity '%1'、DisplayName のブックマークが作成されました: '%2'、InstanceId: '%3'。  BookmarkName: %4、BookmarkScope: %5。|WFRuntime|  
|[1021 - ScheduleBookmarkWorkItem](1021-schedulebookmarkworkitem.md)|詳細|Activity '%1'、DisplayName に対して BookmarkWorkItem がスケジュールされました: '%2'、InstanceId: '%3'。  BookmarkName: %4、BookmarkScope: %5。|WFRuntime|  
|[1022 - StartBookmarkWorkItem](1022-startbookmarkworkitem.md)|詳細|Activity '%1'、DisplayName の BookmarkWorkItem の実行を開始: '%2'、InstanceId: '%3'。  BookmarkName: %4、BookmarkScope: %5。|WFRuntime|  
|[1023 - CompleteBookmarkWorkItem](1023-completebookmarkworkitem.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の BookmarkWorkItem が完了しました。 BookmarkName: %4、BookmarkScope: %5。|WFRuntime|  
|[1024 - CreateBookmarkScope](1024-createbookmarkscope.md)|詳細|BookmarkScope が作成されました: %1。|WFRuntime|  
|[1025 - BookmarkScopeInitialized](1025-bookmarkscopeinitialized.md)|詳細|TemporaryId: '%1' を指定されていた BookmarkScope が ID: '%2' で初期化されました。|WFRuntime|  
|[1026 - ScheduleTransactionContextWorkItem](1026-scheduletransactioncontextworkitem.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対して TransactionContextWorkItem がスケジュールされました。|WFRuntime|  
|[1027 - StartTransactionContextWorkItem](1027-starttransactioncontextworkitem.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の TransactionContextWorkItem の実行を開始しています。|WFRuntime|  
|[1028 - CompleteTransactionContextWorkItem](1028-completetransactioncontextworkitem.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の TransactionContextWorkItem が完了しました。|WFRuntime|  
|[1029 - ScheduleFaultWorkItem](1029-schedulefaultworkitem.md)|詳細|Activity '%1'、DisplayName に対して FaultWorkItem がスケジュールされました: '%2'、InstanceId: '%3'。  Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。|WFRuntime|  
|[1030 - StartFaultWorkItem](1030-startfaultworkitem.md)|詳細|Activity '%1'、DisplayName の FaultWorkItem の実行を開始: '%2'、InstanceId: '%3'。  Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。|WFRuntime|  
|[1031 - CompleteFaultWorkItem](1031-completefaultworkitem.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' の FaultWorkItem が完了しました。 Activity '%4'、DisplayName: '%5'、InstanceId: '%6' から例外が伝達されました。|WFRuntime|  
|[1032 - ScheduleRuntimeWorkItem](1032-scheduleruntimeworkitem.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' に対してランタイム作業項目がスケジュールされました。|WFRuntime|  
|[1033 - StartRuntimeWorkItem](1033-startruntimeworkitem.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' のランタイム作業項目の実行を開始しています。|WFRuntime|  
|[1034 - CompleteRuntimeWorkItem](1034-completeruntimeworkitem.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' のランタイム作業項目が完了しました。|WFRuntime|  
|[1035 - RuntimeTransactionSet](1035-runtimetransactionset.md)|詳細|Activity '%1'、DisplayName によってランタイム トランザクションが設定されています: '%2'、InstanceId: '%3'。  実行の分離を Activity '%4'、DisplayName: '%5'、InstanceId: '%6'。|WFRuntime|  
|[1036 - RuntimeTransactionCompletionRequested](1036-runtimetransactioncompletionrequested.md)|詳細|Activity '%1'、DisplayName: '%2'、InstanceId: '%3' はランタイム トランザクションの完了をスケジュールしました。|WFRuntime|  
|[1037 - RuntimeTransactionComplete](1037-runtimetransactioncomplete.md)|詳細|ランタイム トランザクションは '%1' の状態で完了しました。|WFRuntime|  
|[1038 - EnterNoPersistBlock](1038-enternopersistblock.md)|詳細|no persist ブロックに入ります。|WFRuntime|  
|[1039 - ExitNoPersistBlock](1039-exitnopersistblock.md)|詳細|no persist ブロックを終了します。|WFRuntime|  
|[1040 - InArgumentBound](1040-inargumentbound.md)|詳細|Activity '%2' の引数 '%1' で、DisplayName: '%3'、InstanceId: '%4' が値: %5 にバインドされています。|WFActivities|  
|[1041 - WorkflowApplicationPersistableIdle](1041-workflowapplicationpersistableidle.md)|情報|WorkflowApplication Id: '%1' には、アイドル状態と永続化ができます。  次の動作が行われます。 % 2。|WFRuntime|  
|[1101 - WorkflowActivityStart](1101-workflowactivitystart.md)|情報|WorkflowInstance ID: '%1' E2E アクティビティ|WFRuntime|  
|[1102 - WorkflowActivityStop](1102-workflowactivitystop.md)|情報|WorkflowInstance ID: '%1' E2E アクティビティ|WFRuntime|  
|[1103 - WorkflowActivitySuspend](1103-workflowactivitysuspend.md)|情報|WorkflowInstance ID: '%1' E2E アクティビティ|WFRuntime|  
|[1104 - WorkflowActivityResume](1104-workflowactivityresume.md)|情報|WorkflowInstance ID: '%1' E2E アクティビティ|WFRuntime|  
|[1124 - InvokeMethodIsStatic](1124-invokemethodisstatic.md)|情報|InvokeMethod '%1' - メソッドは Static です。|WFRuntime|  
|[1125 - InvokeMethodIsNotStatic](1125-invokemethodisnotstatic.md)|情報|InvokeMethod '%1' - メソッドは Static ではありません。|WFRuntime|  
|[1126 - InvokedMethodThrewException](1126-invokedmethodthrewexception.md)|情報|アクティビティ '%1' によって呼び出されたメソッドで例外がスローされました。 %2|WFRuntime|  
|[1131 - InvokeMethodUseAsyncPattern](1131-invokemethoduseasyncpattern.md)|情報|InvokeMethod '%1' - メソッドでは '%2' および '%3' の非同期パターンを使用します。|WFRuntime|  
|[1132 - InvokeMethodDoesNotUseAsyncPattern](1132-invokemethoddoesnotuseasyncpattern.md)|情報|InvokeMethod '%1' - メソッドでは非同期パターンを使用しません。|WFRuntime|  
|[1140 - FlowchartStart](1140-flowchartstart.md)|情報|フローチャート '%1' - 開始がスケジュールされています。|WFActivities|  
|[1141 - FlowchartEmpty](1141-flowchartempty.md)|警告|フローチャート '%1' - アクティビティ '%1' によって呼び出されたメソッドで Nodes.An 例外がスローされることなく実行されました。 %2|WFActivities|  
|[1143 - FlowchartNextNull](1143-flowchartnextnull.md)|情報|フローチャート '%1'/FlowStep - 次のノードは null です。 フローチャートの実行は終了します。|WFActivities|  
|[1146 - FlowchartSwitchCase](1146-flowchartswitchcase.md)|情報|フローチャート '%1'/FlowSwitch - Case '%2' が選択されました。|WFActivities|  
|[1147 - FlowchartSwitchDefault](1147-flowchartswitchdefault.md)|情報|フローチャート '%1'/FlowSwitch - 既定の Case が選択されました。|WFActivities|  
|[1148 - FlowchartSwitchCaseNotFound](1148-flowchartswitchcasenotfound.md)|情報|Flowchart '%1'/FlowSwitch - 式の結果に一致する Case アクティビティも Default Case も見つかりませんでした。 フローチャートの実行は終了します。|WFActivities|  
|[1150 - CompensationState](1150-compensationstate.md)|情報|CompensableActivity '%1' は '%2' 状態です。|WFActivities|  
|[1223 - SwitchCaseNotFound](1223-switchcasenotfound.md)|情報|Switch アクティビティ '%1' は Expression の結果に一致する Case アクティビティを見つけることができませんでした。|WFActivities|  
|[1449 - WfMessageReceived](1449-wfmessagereceived.md)|情報|ワークフローによって受信されたメッセージ|WFServices|  
|[1450 - WfMessageSent](1450-wfmessagesent.md)|情報|ワークフローから送信されたメッセージ|WFServices|  
|[2021 - ExecuteWorkItemStart](2021-executeworkitemstart.md)|詳細|作業項目の実行を開始します|WFRuntime|  
|[2022 - ExecuteWorkItemStop](2022-executeworkitemstop.md)|詳細|作業項目の実行を停止します|WFRuntime|  
|[2023 - SendMessageChannelCacheMiss](2023-sendmessagechannelcachemiss.md)|詳細|SendMessageChannelCache ミス|WFRuntime|  
|[2024 - InternalCacheMetadataStart](2024-internalcachemetadatastart.md)|詳細|アクティビティ '%1' で InternalCacheMetadata が開始されました。|WFRuntime|  
|[2025 - InternalCacheMetadataStop](2025-internalcachemetadatastop.md)|詳細|アクティビティ '%1' で InternalCacheMetadata が停止されました。|WFRuntime|  
|[2026 - CompileVbExpressionStart](2026-compilevbexpressionstart.md)|詳細|VB の式 '%1' をコンパイルしています|WFRuntime|  
|[2027 - CacheRootMetadataStart](2027-cacherootmetadatastart.md)|詳細|アクティビティ '%1' で CacheRootMetadata が開始されました|WFRuntime|  
|[2028 - CacheRootMetadataStop](2028-cacherootmetadatastop.md)|詳細|アクティビティ %1 で CacheRootMetadata が停止されました。|WFRuntime|  
|[2029 - CompileVbExpressionStop](2029-compilevbexpressionstop.md)|詳細|VB の式のコンパイルが完了しました。|WFRuntime|  
|[2576 - TryCatchExceptionFromTry](2576-trycatchexceptionfromtry.md)|情報|TryCatch アクティビティ '%1' は、型 '%2' の例外をキャッチしました。|WFActivities|  
|[2577 - TryCatchExceptionDuringCancelation](2577-trycatchexceptionduringcancelation.md)|警告|TryCatch アクティビティ '%1' の子アクティビティは取り消し中に例外をスローしました。|WFActivities|  
|[2578 - TryCatchExceptionFromCatchOrFinally](2578-trycatchexceptionfromcatchorfinally.md)|警告|TryCatch アクティビティ '%1' に関連付けられている Catch または Finally アクティビティは例外をスローしました。|WFActivities|  
|[3501 - InferredContractDescription](3501-inferredcontractdescription.md)|情報|Name='%1' で Namespace='%2' の ContractDescription が WorkflowService から推論されました。|WFServices|  
|[3502 - InferredOperationDescription](3502-inferredoperationdescription.md)|情報|コントラクト '%2' 内の Name='%1' の OperationDescription が WorkflowService から推論されました。 IsOneWay=%3。|WFServices|  
|[3503 - DuplicateCorrelationQuery](3503-duplicatecorrelationquery.md)|警告|Where='%1' で重複する CorrelationQuery が見つかりました。 相関の計算時には、この重複するクエリは使用されません。|WFServices|  
|[3507 - ServiceEndpointAdded](3507-serviceendpointadded.md)|情報|アドレス '%1'、バインド '%2'、コントラクト '%3' のサービス エンドポイントが追加されました。|WFServices|  
|[3508 - TrackingProfileNotFound](3508-trackingprofilenotfound.md)|詳細|ActivityDefinitionId '%2' の TrackingProfile '%1' が見つかりません。 config ファイルに TrackingProfile がないか、ActivityDefinitionId が一致しません。|WFServices|  
|[3550 - BufferOutOfOrderMessageNoInstance](3550-bufferoutofordermessagenoinstance.md)|情報|操作 '%1' は現時点では実行できません。 サービス インスタンスがこの特定の操作を処理できる状態になったとき、もう一度試行されます。|WFServices|  
|[3551 - BufferOutOfOrderMessageNoBookmark](3551-bufferoutofordermessagenobookmark.md)|情報|サービス インスタンス '%1' での操作 '%2' は現時点では実行できません。 サービス インスタンスがこの特定の操作を処理できる状態になったとき、もう一度試行されます。|WFServices|  
|[3552 - MaxPendingMessagesPerChannelExceeded](3552-maxpendingmessagesperchannelexceeded.md)|警告|スロットル '%1' の 'MaxPendingMessagesPerChannel' の制限に達しました。 この制限を引き上げるには、BufferedReceiveServiceBehavior の MaxPendingMessagesPerChannel プロパティを調整してください。|クォータ WFServices|  
|[3557 - TransactedReceiveScopeEndCommitFailed](3557-transactedreceivescopeendcommitfailed.md)|情報|id = '%1' の CommittableTransaction に対する EndCommit への呼び出しにより、次のメッセージと共に TransactionException がスローされました: '%2'。|WFServices|  
|[4201 - EndSqlCommandExecute](4201-endsqlcommandexecute.md)|詳細|SQL コマンドの実行を終了します: %1|WFInstanceStore|  
|[4202 - StartSqlCommandExecute](4202-startsqlcommandexecute.md)|詳細|SQL コマンドの実行を開始します: %1|WFInstanceStore|  
|[4203 - RenewLockSystemError](4203-renewlocksystemerror.md)|Error|ロックの有効期限を延長できませんでした。ロックの有効期限が既に過ぎているか、ロックの所有者が削除されました。 SqlWorkflowInstanceStore を中止します。|WFInstanceStore|  
|[4205 - FoundProcessingError](4205-foundprocessingerror.md)|Error|コマンドが失敗しました: %1|WFInstanceStore|  
|[4206 - UnlockInstanceException](4206-unlockinstanceexception.md)|Error|インスタンスのロックを解除しようとして、例外 %1 が発生しました。|WFInstanceStore|  
|[4207 - MaximumRetriesExceededForSqlCommand](4207-maximumretriesexceededforsqlcommand.md)|情報|SQL コマンドが最大実行回数実行されたので、この SQL コマンドの再試行を停止します。|クオータ WFInstanceStore|  
|[4208 - RetryingSqlCommandDueToSqlError](4208-retryingsqlcommandduetosqlerror.md)|情報|SQL エラー番号 %1 のため、SQL コマンドを再試行します。|WFInstanceStore|  
|[4209 - TimeoutOpeningSqlConnection](4209-timeoutopeningsqlconnection.md)|Error|SQL 接続を開こうとしてタイムアウトしました。 割り当てられたタイムアウト時間 %1 内に操作が完了しませんでした。 この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。|WFInstanceStore|  
|[4210 - SqlExceptionCaught](4210-sqlexceptioncaught.md)|警告|SQL 例外番号 %1 メッセージ %2 がキャッチされました。|WFInstanceStore|  
|[4211 - QueuingSqlRetry](4211-queuingsqlretry.md)|警告|%1 ミリ秒の遅延で SQL の再試行をキューに登録しています。|WFInstanceStore|  
|[4212 - LockRetryTimeout](4212-lockretrytimeout.md)|警告|インスタンスのロックを取得しようとしてタイムアウトになりました。  割り当てられたタイムアウト時間 %1 内に操作が完了しませんでした。 この操作に割り当てられた時間は、より長いタイムアウト時間の一部であった可能性があります。|WFInstanceStore|  
|[4213 - RunnableInstancesDetectionError](4213-runnableinstancesdetectionerror.md)|Error|実行可能インスタンスの検出は次の例外のために失敗しました|WFInstanceStore|  
|[4214 - InstanceLocksRecoveryError](4214-instancelocksrecoveryerror.md)|Error|インスタンスのロックの回復は次の例外のために失敗しました|WFInstanceStore|  
|[39456 - TrackingRecordDropped](39456-trackingrecorddropped.md)|警告|追跡レコード %1 のサイズが、プロバイダー %2 の ETW セッションで許可される最大サイズを超えています|WFTracking|  
|[39457 - TrackingRecordRaised](39457-trackingrecordraised.md)|情報|追跡レコード %1 が %2 になりました。|WFRuntime|  
|[39458 - TrackingRecordTruncated](39458-trackingrecordtruncated.md)|警告|プロバイダー %2 の ETW セッションに書き込まれた追跡レコード %1 が切り捨てられました。 変数/注釈/ユーザー データは削除されました|WFTracking|  
|[39459 - TrackingDataExtracted](39459-trackingdataextracted.md)|詳細|追跡データ %1 がアクティビティ %2 で抽出されました。|WFRuntime|  
|[39460 - TrackingValueNotSerializable](39460-trackingvaluenotserializable.md)|警告|抽出された引数/変数 '%1' はシリアル化できません。|WFTracking|  
|[57398 - MaxInstancesExceeded](57398-maxinstancesexceeded.md)|警告|システムはスロットル 'MaxConcurrentInstances' に設定された制限に達しました。 このスロットルの制限は %1 に設定されました。 スロットル値を変更するには、serviceThrottle 要素の属性 'maxConcurrentInstances' を変更するか、動作 ServiceThrottlingBehavior の 'MaxConcurrentInstances' プロパティを変更する必要があります。|WFServices|
