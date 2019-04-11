---
title: CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
ms.date: 03/30/2017
f1_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE
helpviewer_keywords:
- CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT [.NET Framework profiling]
ms.assetid: f2fc441f-d62e-4f72-a011-354ea13c8c59
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8c65ec6acc5ff87501392eb41909fcd6ebf1e3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092137"
---
# <a name="corprofeunsupportedcallsequence-hresult"></a>CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT
CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT は、.NET Framework version 2.0 で導入されました。 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)] 2 つのシナリオでこの HRESULT を返します。  
  
-   ハイジャック プロファイラーがスレッドを強制的にリセットしたときに、スレッドが不整合な状態では、構造にアクセスしようとするように、任意の時点でコンテキストを登録します。  
  
-   プロファイラーは、コールバック メソッドからのガベージ コレクションをトリガーする情報提供メソッドを呼び出そうとすると、ガベージ コレクションが禁止されているがします。  
  
 これら 2 つのシナリオは、次のセクションについて説明します。  
  
## <a name="hijacking-profilers"></a>プロファイラーをハイジャック  
 (このシナリオは、主にハイジャック非のプロファイラーがこの HRESULT を表示できる場合がありますが、プロファイラーをハイジャック問題です)。  
  
 このシナリオでハイジャック プロファイラー強制的にリセット レジスタ コンテキストのスレッドの任意の時点で、スレッドがプロファイラー コードを入力または共通言語ランタイム (CLR) を再入力するようにを通じて、 [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)メソッド。  
  
 多くのプロファイル API は、CLR でのデータ構造体へのポイントを提供する Id。 多く`ICorProfilerInfo`呼び出しは単なるこれらのデータ構造から情報を読み取るしに渡します。 ただし、CLR はこれらの構造の処理を変更可能性があります、それが実行され、そのためにはロックを使用することでしょう。 CLR が既に保持している (または取得しようとしています) 時にロックと、プロファイラーがスレッドをハイジャックです。 スレッドは、CLR を再入力して、複数のロックを取得または変更される過程で構造を検査しようとしています。、一貫性のない状態でこれらの構造があります。 デッドロックやアクセス違反は、このような状況では簡単に発生します。  
  
 非ハイジャック プロファイラーが内のコードを実行するときに一般的に、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)メソッドを呼び出し、`ICorProfilerInfo`メソッドで有効なパラメーターは、いないデッドロックまたはアクセス違反が発生にする必要があります。 内で実行されるプロファイラー コードなど、 [icorprofilercallback::classloadfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadfinished-method.md)メソッドがクラスについての情報を呼び出して要求、 [icorprofilerinfo 2::getclassidinfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)メソッド。 コードは、情報が使用可能であることを示す CORPROF_E_DATAINCOMPLETE HRESULT を受け取ることがあります。ただし、デッドロックまたはされませんアクセス違反が発生します。 このクラスへの呼び出しの`ICorProfilerInfo`から構成されているため、同期と呼びます、`ICorProfilerCallback`メソッド。  
  
 ただし、マネージ スレッドを実行するコード内ではありません、`ICorProfilerCallback`メソッドの非同期呼び出しを行うと見なされます。 .NET Framework のバージョン 1 では、非同期の呼び出しで何が起こるかを判断する困難でした。 呼び出しでは、デッドロックが発生、クラッシュ、または、無効な答えが得られます可能性があります。 .NET Framework version 2.0 では、この問題を回避するためのいくつかの簡単なチェックが導入されました。 呼び出すことが、安全でない場合、.NET Framework 2.0 で`ICorProfilerInfo`非同期的に関数を CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT で失敗します。  
  
 一般に、非同期の呼び出しは安全ではありません。 ただし、次のメソッドは安全かつ具体的には非同期呼び出しをサポートします。  
  
-   [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md)  
  
-   [SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)  
  
-   [GetCurrentThreadID](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcurrentthreadid-method.md)  
  
-   [GetThreadContext](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getthreadcontext-method.md)  
  
-   [GetThreadAppDomain](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadappdomain-method.md)  
  
-   [GetFunctionFromIP](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctionfromip-method.md)  
  
-   [GetFunctionInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getfunctioninfo-method.md)  
  
-   [GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)  
  
-   [GetCodeInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getcodeinfo-method.md)  
  
-   [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)  
  
-   [GetModuleInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmoduleinfo-method.md)  
  
-   [GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md)  
  
-   [GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md)  
  
-   [IsArrayClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-isarrayclass-method.md)  
  
-   [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
  
-   [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
  
 詳細については、エントリを参照してください。 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE あります](https://go.microsoft.com/fwlink/?LinkId=169156)CLR プロファイル API のブログ。  
  
## <a name="triggering-garbage-collections"></a>ガベージ コレクションをトリガーします。  
 このシナリオでは、コールバック メソッドの内部で実行しているプロファイラー (たとえば、1 つの`ICorProfilerCallback`メソッド) のガベージ コレクションが禁止されています。 プロファイラーが情報提供メソッドを呼び出そうとしている場合 (メソッドなど、`ICorProfilerInfo`インターフェイス) ガベージ コレクションをトリガーする可能性があります、情報提供メソッドが CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT で失敗します。  
  
 次の表では、ガベージ コレクションを禁止するコールバック メソッドをおよびガベージ コレクションがトリガーされるメソッドの情報が表示されます。 プロファイラーは内で表示されているコールバック メソッドのいずれかを実行し、表示されている情報メソッドのいずれかを呼び出し、その情報提供メソッドは CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT で失敗します。  
  
|ガベージ コレクションが禁止されているコールバック メソッド|ガベージ コレクションをトリガーする情報メソッド|  
|------------------------------------------------------|------------------------------------------------------------|  
|[ThreadAssignedToOSThread](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadassignedtoosthread-method.md)<br /><br /> [ExceptionUnwindFunctionEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionenter-method.md)<br /><br /> [ExceptionUnwindFunctionLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfunctionleave-method.md)<br /><br /> [ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)<br /><br /> [ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)<br /><br /> [ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md)<br /><br /> [RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md)<br /><br /> [RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)<br /><br /> [RuntimeSuspendAborted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)<br /><br /> [RuntimeThreadSuspended](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadsuspended-method.md)<br /><br /> [RuntimeThreadResumed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)<br /><br /> [MovedReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)<br /><br /> [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md)<br /><br /> [ObjectsAllocatedByClass](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectsallocatedbyclass-method.md)<br /><br /> [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)<br /><br /> [HandleCreated](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)<br /><br /> [HandleDestroyed](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)<br /><br /> [GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)<br /><br /> [GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|[GetILFunctionBodyAllocator](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getilfunctionbodyallocator-method.md)<br /><br /> [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)<br /><br /> [SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilinstrumentedcodemap-method.md)<br /><br /> [ForceGC](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md)<br /><br /> [GetClassFromToken](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassfromtoken-method.md)<br /><br /> [GetClassFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassfromtokenandtypeargs-method.md)<br /><br /> [GetFunctionFromTokenAndTypeArgs](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctionfromtokenandtypeargs-method.md)<br /><br /> [GetAppDomainInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getappdomaininfo-method.md)<br /><br /> [EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)<br /><br /> [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md)<br /><br /> [GetAppDomainsContainingModule](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getappdomainscontainingmodule-method.md)|  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [ICorProfilerInfo3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
