---
title: ICorProfilerCallback2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2
helpviewer_keywords:
- ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83c72704ccb01baf68a3cacb6252367e07909fa8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638415"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 インターフェイス
プロファイラーがサブスクライブしているイベントが発生したときにコード プロファイラーに通知を共通言語ランタイム (CLR) によって使用されるメソッドを提供します。 `ICorProfilerCallback2`インターフェイスの拡張機能は、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)インターフェイス。 つまり、.NET Framework version 2.0 で導入された新しいコールバックを提供します。  
  
> [!NOTE]
>  各メソッドの実装では、S_OK のエラー発生時に成功した場合、または E_FAIL の値を持つ HRESULT を返す必要があります。 現時点では、CLR を除く各コールバックによって返される HRESULT を無視[icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[FinalizeableObjectQueued メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|コード プロファイラーに通知ファイナライザーを持つオブジェクトが、ファイナライザー スレッドを実行するためにキューに登録されましたが、`Finalize`メソッド。|  
|[GarbageCollectionFinished メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|ガベージ コレクションが完了し、それに対してガベージ コレクションのすべてのコールバックが発行されたことをプロファイラーに通知します。|  
|[GarbageCollectionStarted メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|ガベージ コレクションが開始されたことをコード プロファイラーに通知します。|  
|[HandleCreated メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|ガベージ コレクション ハンドルが作成されているコード プロファイラーに通知します。|  
|[HandleDestroyed メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|ガベージ コレクション ハンドルが破棄されたことをコード プロファイラーに通知します。|  
|[RootReferences2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|ガベージ コレクションが発生した後、ルート参照について、プロファイラーに通知します。 このメソッドは、の拡張機能、 [icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)メソッド。|  
|[SurvivingReferences メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|ガベージ コレクションで残ったオブジェクト参照をプロファイラーに通知します。|  
|[ThreadNameChanged メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|スレッドの名前が変更されたことをコード プロファイラーに通知します。|  
  
## <a name="remarks"></a>Remarks  
 CLR でメソッドを呼び出し、 `ICorProfilerCallback` (または`ICorProfilerCallback2`) インターフェイスをイベントは、プロファイラーがサブスクライブしているときにプロファイラーに通知が発生します。 これは、コード プロファイラーを使用して、CLR 通信に使用するプライマリのコールバック インターフェイスです。  
  
 コード プロファイラーのメソッドを実装する必要があります、`ICorProfilerCallback`インターフェイス。 .NET Framework 2.0 と以降のバージョンでは、プロファイラーを実装する必要がありますも、`ICorProfilerCallback2`メソッド。 各メソッドの実装では、S_OK のエラー発生時に成功した場合、または E_FAIL の値を持つ HRESULT を返す必要があります。 現時点では、CLR を除く各コールバックによって返される HRESULT を無視[icorprofilercallback::objectreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)します。  
  
 コード プロファイラーは、Microsoft Windows レジストリを実装する COM オブジェクトに登録する必要があります、`ICorProfilerCallback`と`ICorProfilerCallback2`インターフェイス。 コード プロファイラーが呼び出すことで通知を受信する対象のイベントをサブスクライブ[icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)します。 プロファイラーの実装でこれは、通常[icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)します。 プロファイラーは、イベントが実行されるときに、または実行中のランタイム プロセスがいつ発生したときに、ランタイムから通知を受信できます。  
  
> [!NOTE]
>  プロファイラーは、1 つの COM オブジェクトを登録します。 場合は、プロファイラーは、.NET Framework version 1.0 または 1.1 を対象とするが、その COM オブジェクト必要がありますのメソッドを実装のみ`ICorProfilerCallback`します。 .NET Framework version 2.0 が対象として、後で、COM オブジェクトである必要がありますのメソッドを実装も場合`ICorProfilerCallback2`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
