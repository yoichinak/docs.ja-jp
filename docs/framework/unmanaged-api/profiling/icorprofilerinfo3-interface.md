---
title: ICorProfilerInfo3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3
helpviewer_keywords:
- ICorProfilerInfo3 interface [.NET Framework profiling]
ms.assetid: 044a262f-0fa7-485d-b0c1-64cdc359c654
topic_type:
- apiref
ms.openlocfilehash: c42b0df90dc690997bbc5414e977d6830dc5f3b8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449631"
---
# <a name="icorprofilerinfo3-interface"></a>ICorProfilerInfo3 インターフェイス
コード プロファイラーが共通言語ランタイム (CLR: Common Language Runtime) とやり取りして、イベント監視を制御したり、情報を要求したりするために使用する各種メソッドを提供します。 The `ICorProfilerInfo3` interface is an extension of the [ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md) interface. It provides new methods supported in the .NET Framework 4 and later versions.  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[EnumJITedFunctions メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)|以前に JIT でコンパイルされたすべての関数に対する列挙子を返します。|  
|[EnumModules メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)|アプリケーションに読み込まれるマネージド モジュールのコレクションを順番に反復処理するメソッドを提供する列挙子を返します。|  
|[GetAppDomainsContainingModule メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|指定したモジュールが読み込まれているアプリケーション ドメインの識別子を取得します。|  
|[GetFunctionEnter3Info メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)|Provides the stack frame and argument information of the function that is being reported to the profiler by the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md) function; can be called only during the `FunctionEnter3WithInfo` callback.|  
|[GetFunctionLeave3Info メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md)|Provides the stack frame and return value of the function that is being reported to the profiler by the [FunctionLeave3WithInfo function](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md) function; can be called only during the `FunctionLeave3WithInfo` callback.|  
|[GetFunctionTailcall3Info メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)|Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) function; can be called only during the `FunctionTailcall3WithInfo` callback.|  
|[GetModuleInfo2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md)|モジュール ID を指定して、モジュールのファイル名、モジュールの親アセンブリの ID、およびモジュールのプロパティを示すビットマスクを返します。|  
|[GetRuntimeInformation メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getruntimeinformation-method.md)|プロファイリングされているランタイムに関するバージョン情報を提供します。|  
|[GetStringLayout2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getstringlayout2-method.md)|文字列オブジェクトのレイアウトに関する情報を取得します。|  
|[GetThreadStaticAddress2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getthreadstaticaddress2-method.md)|指定したスレッドおよびアプリケーション ドメインのスコープ内にある、指定したスレッド内静的フィールドのアドレスを取得します。|  
|[RequestProfilerDetach メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)|プロファイラーをデタッチするようにランタイムに指示します。|  
|[SetEnterLeaveFunctionHooks3 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)|Specifies the profiler-implemented functions that will be called on the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) functions.|  
|[SetEnterLeaveFunctionHooks3WithInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)|Specifies the profiler-implemented functions that will be called on the [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) hooks of managed functions.|  
|[SetFunctionIDMapper2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)|`FunctionID` 値を代替値に対応付けるために呼び出すプロファイラー実装関数を指定します。代替値は、プロファイラーの関数の開始フックと終了フックに渡されます。 This method extends [ICorProfilerInfo::SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md) with a parameter that profilers may use to disambiguate among runtimes.|  
  
## <a name="remarks"></a>Remarks  
 CLR は、`ICorProfilerInfo3` インターフェイスのメソッドを、フリー スレッド モデルを使用して実装します。 各メソッドが、成功または失敗を示す HRESULT を返します。 返される可能性があるリターン コードの一覧については、CorError.h ファイルを参照してください。  
  
 The CLR passes an `ICorProfilerInfo3` interface to each code profiler during initialization, using the profiler's implementation of the [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) or [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method. その後、コード プロファイラーは `ICorProfilerInfo3` メソッドを呼び出して、CLR の制御下で実行中のマネージド コードに関する情報を取得できます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
