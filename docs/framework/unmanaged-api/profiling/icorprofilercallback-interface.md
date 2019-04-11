---
title: ICorProfilerCallback インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback
helpviewer_keywords:
- ICorProfilerCallback interface [.NET Framework profiling]
ms.assetid: 4bae06f7-94d7-4ba8-b250-648b2da78674
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e2f474317493b3aac421ca1270ff461b97cfe027
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125945"
---
# <a name="icorprofilercallback-interface"></a>ICorProfilerCallback インターフェイス
プロファイラーがサブスクライブしているイベントが発生したときにコード プロファイラーに通知を共通言語ランタイム (CLR) によって使用されるメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[AppDomainCreationFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationfinished-method.md)|アプリケーション ドメインが作成されたことをプロファイラーに通知します。|  
|[AppDomainCreationStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomaincreationstarted-method.md)|アプリケーション ドメインが作成されていることをプロファイラーに通知します。|  
|[AppDomainShutdownFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownfinished-method.md)|アプリケーション ドメインが、プロセスからアンロードされたことをプロファイラーに通知します。|  
|[AppDomainShutdownStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-appdomainshutdownstarted-method.md)|プロセスから、アプリケーション ドメインがアンロードされることをプロファイラーに通知します。|  
|[AssemblyLoadFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadfinished-method.md)|アセンブリの読み込みが完了したことをプロファイラーに通知します。|  
|[AssemblyLoadStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyloadstarted-method.md)|アセンブリが読み込まれていることをプロファイラーに通知します。|  
|[AssemblyUnloadFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadfinished-method.md)|アセンブリがアンロードされたことをプロファイラーに通知します。|  
|[AssemblyUnloadStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md)|アセンブリがアンロードされることをプロファイラーに通知します。|  
|[ClassLoadFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)|クラスの読み込みが完了したことをプロファイラーに通知します。|  
|[ClassLoadStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)|クラスが読み込まれていることをプロファイラーに通知します。|  
|[ClassUnloadFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadfinished-method.md)|クラスのアンロードが完了したことをプロファイラーに通知します。|  
|[ClassUnloadStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classunloadstarted-method.md)|クラスがアンロードされることをプロファイラーに通知します。|  
|[COMClassicVTableCreated メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)|指定された IID とクラスのランタイム呼び出し可能ラッパー (RCW) が作成されたことをプロファイラーに通知します。|  
|[COMClassicVTableDestroyed メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)|RCW が破棄されていることをプロファイラーに通知します。|  
|[ExceptionCatcherEnter メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)|適切な制御が渡されることをプロファイラーに通知`catch`ブロックします。|  
|[ExceptionCatcherLeave メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md)|コントロールが、適切なから渡されることをプロファイラーに通知`catch`ブロックします。|  
|[ExceptionCLRCatcherExecute メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)|.NET Framework version 2.0 で廃止されました。|  
|[ExceptionCLRCatcherFound メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherfound-method.md)|.NET Framework 2.0 で廃止します。|  
|[ExceptionOSHandlerEnter メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerenter-method.md)|実装されていません。 非管理対象の例外情報を必要とするプロファイラーでは、他の手段では、この情報を取得する必要があります。|  
|[ExceptionOSHandlerLeave メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionoshandlerleave-method.md)|実装されていません。 非管理対象の例外情報を必要とするプロファイラーでは、他の手段では、この情報を取得する必要があります。|  
|[ExceptionSearchCatcherFound メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchcatcherfound-method.md)|例外処理の検索フェーズでスローされた例外のハンドラーが見つかったことをプロファイラーに通知します。|  
|[ExceptionSearchFilterEnter メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)|ユーザー フィルターが実行されていることをプロファイラーに通知します。|  
|[ExceptionSearchFilterLeave メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md)|ユーザー フィルターがだけ完了したことを実行するプロファイラーに通知します。|  
|[ExceptionSearchFunctionEnter メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionenter-method.md)|例外処理の検索フェーズが関数に入ったことをプロファイラーに通知します。|  
|[ExceptionSearchFunctionLeave メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfunctionleave-method.md)|例外処理の検索フェーズで、関数の検索が完了したことをプロファイラーに通知します。|  
|[ExceptionThrown メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionthrown-method.md)|例外がスローされたことをプロファイラーに通知します。|  
|[ExceptionUnwindFinallyEnter メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)|例外のアンワインド フェーズの処理が入ることをプロファイラーに通知を`finally`句が指定された関数に含まれています。|  
|[ExceptionUnwindFinallyLeave メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)|例外のアンワインド フェーズの処理が残っているプロファイラーに通知を`finally`句。|  
|[ExceptionUnwindFunctionEnter メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)|例外処理のアンワインド フェーズが関数に入ったことをプロファイラーに通知します。|  
|[ExceptionUnwindFunctionLeave メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)|例外処理のアンワインド フェーズの関数のアンワインドが完了したことをプロファイラーに通知します。|  
|[FunctionUnloadStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-functionunloadstarted-method.md)|関数のアンロードをランタイムが開始されたことをプロファイラーに通知します。|  
|[Initialize メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)|CLR の新しいアプリケーションを起動するたびに、プロファイラーを初期化するために呼び出されます。|  
|[JITCachedFunctionSearchFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchfinished-method.md)|NGen.exe を使用して以前にコンパイルされた関数の検索が完了したことをプロファイラーに通知します。|  
|[JITCachedFunctionSearchStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcachedfunctionsearchstarted-method.md)|NGen.exe を使用して以前にコンパイルされた関数の検索が開始されたことをプロファイラーに通知します。|  
|[JITCompilationFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationfinished-method.md)|JIT コンパイラが関数のコンパイルを完了したことをプロファイラーに通知します。|  
|[JITCompilationStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)|ジャストイン タイム (JIT) コンパイラが関数のコンパイルを開始されたことをプロファイラーに通知します。|  
|[JITFunctionPitched メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitfunctionpitched-method.md)|JIT コンパイルされた関数がメモリから削除されたことをプロファイラーに通知します。|  
|[JITInlining メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)|JIT コンパイラが別の関数に合わせて関数を挿入しようとしていますが、プロファイラーに通知します。|  
|[ManagedToUnmanagedTransition メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md)|マネージ コードからアンマネージ コードへの移行が発生したことをプロファイラーに通知します。|  
|[ModuleAttachedToAssembly メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleattachedtoassembly-method.md)|モジュールが、親アセンブリに関連付けられていることをプロファイラーに通知します。|  
|[ModuleLoadFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md)|モジュールの読み込みが完了したことをプロファイラーに通知します。|  
|[ModuleLoadStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)|モジュールが読み込まれていることをプロファイラーに通知します。|  
|[ModuleUnloadFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadfinished-method.md)|モジュールのアンロードが完了したことをプロファイラーに通知します。|  
|[ModuleUnloadStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md)|モジュールがアンロードされることをプロファイラーに通知します。|  
|[MovedReferences メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)|ガベージ コレクション中に移動されたオブジェクト参照をプロファイラーに通知します。|  
|[ObjectAllocated メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectallocated-method.md)|オブジェクトの割り当てられたヒープ内のメモリ プロファイラーに通知します。|  
|[ObjectReferences メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)|指定したオブジェクトによって参照されるメモリ内のオブジェクトをプロファイラーに通知します。|  
|[ObjectsAllocatedByClass メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)|前のガベージ コレクションの後に作成された指定した各クラスのインスタンスの数をプロファイラーに通知します。|  
|[RemotingClientInvocationFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationfinished-method.md)|クライアントで、リモート処理呼び出しが完了するまで実行をプロファイラーに通知します。|  
|[RemotingClientInvocationStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientinvocationstarted-method.md)|リモート処理呼び出しが開始されたことをプロファイラーに通知します。|  
|[RemotingClientReceivingReply メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientreceivingreply-method.md)|リモート処理呼び出しのサーバー側の部分が完了し、クライアントが受け取るようになりましたことをプロファイラーに通知し、応答を処理します。|  
|[RemotingClientSendingMessage メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingclientsendingmessage-method.md)|クライアントがサーバーに要求を送信しているプロファイラーに通知します。|  
|[RemotingServerInvocationReturned メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationreturned-method.md)|プロセスで、リモート メソッド呼び出しの要求に応答におけるメソッドの呼び出しが完了したことをプロファイラーに通知します。|  
|[RemotingServerInvocationStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverinvocationstarted-method.md)|プロセスがリモート メソッド呼び出しの要求に応答でメソッドを呼び出すことをプロファイラーに通知します。|  
|[RemotingServerReceivingMessage メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserverreceivingmessage-method.md)|プロセスがリモート メソッド呼び出しまたはアクティブ化要求を受信しているプロファイラーに通知します。|  
|[RemotingServerSendingReply メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-remotingserversendingreply-method.md)|プロセスがリモート メソッド呼び出し要求の処理が完了して、チャネルを介して応答を送信しようとしていますが、プロファイラーに通知します。|  
|[RootReferences メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)|ガベージ コレクション後のルート参照に関する情報をプロファイラーに通知します。|  
|[RuntimeResumeFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumefinished-method.md)|ランタイムはランタイムのすべてのスレッドが再開し、通常の操作に返されますが、プロファイラーに通知します。|  
|[RuntimeResumeStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md)|ランタイムが実行時のすべてのスレッドを再開することをプロファイラーに通知します。|  
|[RuntimeSuspendAborted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)|ランタイムで発生しているランタイムの中断が中止されたことをプロファイラーに通知します。|  
|[RuntimeSuspendFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)|ランタイムの実行時のすべてのスレッドの中断が完了したことをプロファイラーに通知します。|  
|[RuntimeSuspendStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)|ランタイムを実行時のすべてのスレッドを中断することをプロファイラーに通知します。|  
|[RuntimeThreadResumed メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)|指定したスレッドが中断された後に再開されたことをプロファイラーに通知します。|  
|[RuntimeThreadSuspended メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)|指定したスレッドが、またはが中断するには、プロファイラーに通知します。|  
|[Shutdown メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md)|アプリケーションのシャット ダウンをプロファイラーに通知します。|  
|[ThreadAssignedToOSThread メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)|特定のオペレーティング システム (OS) のスレッドを使用して、マネージ スレッドが実装されることをプロファイラーに通知します。|  
|[ThreadCreated メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)|スレッドが作成されたことをプロファイラーに通知します。|  
|[ThreadDestroyed メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threaddestroyed-method.md)|スレッドが破棄されたことをプロファイラーに通知します。|  
|[UnmanagedToManagedTransition メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md)|アンマネージ コードからマネージ コードへの移行が発生したことをプロファイラーに通知します。|  
  
## <a name="remarks"></a>Remarks  
 CLR でメソッドを呼び出し、 `ICorProfilerCallback` (または[ICorProfilerCallback2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)) インターフェイスをイベントは、プロファイラーがサブスクライブしているときにプロファイラーに通知が発生します。 これは、コード プロファイラーを使用して、CLR 通信に使用するプライマリのコールバック インターフェイスです。  
  
 コード プロファイラーのメソッドを実装する必要があります、`ICorProfilerCallback`インターフェイス。 .NET Framework バージョン 2.0 以降では、プロファイラーを実装する必要がありますも、`ICorProfilerCallback2`メソッド。 各メソッドの実装では、失敗した場合の値が成功した場合は S_OK HRESULT または E_FAIL を返す必要があります。 現時点では、CLR を除く各コールバックによって返される HRESULT を無視[icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)します。  
  
 コード プロファイラーは、Microsoft Windows レジストリで、コンポーネント オブジェクト モデル (COM) オブジェクトを実装するを登録する必要があります、`ICorProfilerCallback`と`ICorProfilerCallback2`インターフェイス。 コード プロファイラーが呼び出すことで通知を受信する対象のイベントをサブスクライブ[icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)します。 プロファイラーの実装でこれは、通常[icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)します。 プロファイラーは、イベントが実行されるときに、または実行中のランタイム プロセスがいつ発生したときに、ランタイムから通知を受信できます。  
  
> [!NOTE]
>  プロファイラーは、1 つの COM オブジェクトを登録します。 プロファイラーが .NET Framework version 1.0 または 1.1 では、COM オブジェクトがのメソッドのみを実装する必要があることを対象とするかどうかは`ICorProfilerCallback`します。 COM オブジェクトがのメソッドを実装する必要がありますも .NET Framework version 2.0 以降を対象とは、その場合`ICorProfilerCallback2`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
