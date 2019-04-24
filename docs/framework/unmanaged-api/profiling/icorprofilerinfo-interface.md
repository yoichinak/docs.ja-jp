---
title: ICorProfilerInfo インターフェイス
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo
helpviewer_keywords:
- ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: eb4e4ce0-06e7-4469-bbc4-edc2eb5da4b1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b979b5f4ee849b96cd29b6c8e2e6a8932e88c182
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201716"
---
# <a name="icorprofilerinfo-interface"></a>ICorProfilerInfo インターフェイス
共通言語ランタイム (CLR) には、イベントの監視を制御し、情報を要求との通信にコード プロファイラーで使用するためのメソッドを提供します。  
  
> [!NOTE]
>  内の各メソッド、`ICorProfilerInfo`インターフェイスは、成功または失敗を示す HRESULT を返します。 リターン コードの一覧については、CorError.h を参照してください。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[BeginInprocDebugging メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md)|初期化します、インプロセス デバッグのサポート。 このメソッドは、.NET Framework version 2.0 で廃止されています。|  
|[EndInprocDebugging メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-endinprocdebugging-method.md)|プロセスでのデバッグ セッションを停止します。 このメソッドは、.NET Framework version 2.0 で廃止されています。|  
|[ForceGC メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)|強制的にガベージ コレクションに、ランタイム内で発生します。|  
|[GetAppDomainInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)|指定されたアプリケーション ドメインに関する情報を取得します。|  
|[GetAssemblyInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getassemblyinfo-method.md)|指定したアセンブリに関する情報を取得します。|  
|[GetClassFromObject メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromobject-method.md)|取得、`ClassID`の<br /><br /> 指定したオブジェクトの`ObjectID`します。|  
|[GetClassFromToken メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)|指定したメタデータ トークン、クラスの ID を取得します。 このメソッドは、.NET Framework version 2.0 で廃止されています。 使用して、 [icorprofilerinfo 2::getclassfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)メソッド代わりにします。|  
|[GetClassIDInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)|指定したクラスの親モジュールとメタデータ トークンを取得します。|  
|[GetCodeInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)|指定した関数 ID に関連付けられているネイティブ コードの範囲を取得します。 このメソッドは、互換性のために残されています。 使用して、 [icorprofilerinfo 2::getcodeinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)メソッド代わりにします。|  
|[GetCurrentThreadID メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)|マネージ スレッドである場合は、現在のスレッドの ID を取得します。|  
|[GetEventMask メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)|プロファイラーが CLR からのイベント通知を受け取る、現在のイベント カテゴリを取得します。|  
|[GetFunctionFromIP メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)|マネージ コードの命令ポインターのマップを`FunctionID`します。|  
|[GetFunctionFromToken メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromtoken-method.md)|関数の ID を取得します。 このメソッドは、.NET Framework version 2.0 で廃止されています。 使用して、 [icorprofilerinfo 2::getfunctionfromtokenandtypeargs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)メソッド代わりにします。|  
|[GetFunctionInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)|指定された関数の親クラスとメタデータ トークンを取得します。|  
|[GetHandleFromThread メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gethandlefromthread-method.md)|Win32 スレッドのハンドル、スレッドの ID にマップします。|  
|[GetILFunctionBody メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbody-method.md)|開始位置のヘッダーとして、Microsoft intermediate language (MSIL) コードでメソッドの本体にポインターを取得します。|  
|[GetILFunctionBodyAllocator メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)|MSIL コード内のメソッドの本文をスワップするために使用されるメモリを割り当てるメソッドを提供するインターフェイスを取得します。|  
|[GetILToNativeMapping メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)|MSIL オフセットから指定された関数に含まれるコードのネイティブ オフセットへのマップを取得します。|  
|[GetInprocInspectionInterface メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectioninterface-method.md)|ICorDebugProcess インターフェイスのクエリを実行できるオブジェクトを取得します。 このメソッドは、.NET Framework version 2.0 で廃止されています。|  
|[GetInprocInspectionIThisThread メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getinprocinspectionithisthread-method.md)|ICorDebugThread インターフェイスのクエリを実行できるオブジェクトを取得します。 このメソッドは、.NET Framework version 2.0 で廃止されています。|  
|[GetModuleInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)|モジュール ID を指定して、モジュールのファイル名とモジュールの親アセンブリの ID を取得します。|  
|[GetModuleMetaData メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md)|指定したモジュールにマップされるメタデータ インターフェイス インスタンスを取得します。|  
|[GetObjectSize メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getobjectsize-method.md)|指定したオブジェクトのサイズを取得します。|  
|[GetThreadContext メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)|指定したスレッドに関連付けられているコンテキスト id を取得します。|  
|[GetThreadInfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadinfo-method.md)|指定したスレッドの現在の Win32 スレッド id を取得します。|  
|[GetTokenAndMetadataFromFunction メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-gettokenandmetadatafromfunction-method.md)|メタデータ トークンとトークンに対して指定された関数を使用できるメタデータ インターフェイスのインスタンスを取得します。|  
|[IsArrayClass メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)|指定したクラスが、配列クラスであるかどうかを判断します。|  
|[SetEnterLeaveFunctionHooks メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)|「入力」、「のまま」、およびマネージ関数の"tailcall"フックで呼び出されるプロファイラー実装関数を指定します。|  
|[SetEventMask メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)|プロファイラーが CLR から通知を受け取るイベントの種類を指定する値を設定します。|  
|[SetFunctionIDMapper メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)|`FunctionID` 値を代替値に対応付けるために呼び出すプロファイラー実装関数を指定します。代替値は、プロファイラーの関数の開始フックと終了フックに渡されます。|  
|[SetFunctionReJIT メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionrejit-method.md)|実装されていません。 使用しないでください。|  
|[SetILFunctionBody メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)|指定したモジュール内の指定した関数の本体を置き換えます。|  
|[SetILInstrumentedCodeMap メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)|新しい関数のプロファイラーで変更された MSIL のオフセットを指定された関数の元の MSIL のオフセットをマップする方法を指定します。|  
  
## <a name="remarks"></a>Remarks  
 プロファイラーでメソッドを呼び出し、`ICorProfilerInfo`イベントの監視を制御し、情報を要求するには、CLR と通信するインターフェイス。  
  
 メソッド、`ICorProfilerInfo`インターフェイスは、フリー スレッド モデルを使用して、CLR によって実装されます。 各メソッドが、成功または失敗を示す HRESULT を返します。 リターン コードの一覧については、CorError.h を参照してください。  
  
 プロファイラーの実装を使用して、CLR に渡します[icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)、`ICorProfilerInfo`を初期化中には、各コード プロファイラーのインターフェイス。 コード プロファイラーは、のメソッドを呼び出すことができますし、 `ICorProfilerInfo` CLR の制御下で実行されているマネージ コードに関する情報を取得するインターフェイス。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
