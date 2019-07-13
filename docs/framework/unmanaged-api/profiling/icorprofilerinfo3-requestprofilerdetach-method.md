---
title: ICorProfilerInfo3::RequestProfilerDetach メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.RequestProfilerDetach Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::RequestProfilerDetach
helpviewer_keywords:
- RequestProfilerDetach method [.NET Framework profiling]
- ICorProfilerInfo3::RequestProfilerDetach method [.NET Framework profiling]
ms.assetid: ea102e62-0454-4477-bcf3-126773acd184
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ab203fc054298971fadfd9abe4e787844313898b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67765323"
---
# <a name="icorprofilerinfo3requestprofilerdetach-method"></a>ICorProfilerInfo3::RequestProfilerDetach メソッド
プロファイラーをデタッチするようにランタイムに指示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT RequestProfilerDetach(  
   [in] DWORD    dwExpectedCompletionMilliseconds);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwExpectedCompletionMilliseconds`  
 [in] プロファイラーをアンロードするのが安全かどうかを確認するチェックを行うまでに共通言語ランタイム (CLR) が待機する時間 (ミリ秒)。  
  
## <a name="return-value"></a>戻り値  
 このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|デタッチ要求は有効です。またデタッチ プロシージャは別のスレッドで継続しています。 デタッチが完了すると、`ProfilerDetachSucceeded` イベントが発行されます。|  
|E_ CORPROF_E_CALLBACK3_REQUIRED|プロファイラーが失敗しました、 [iunknown::queryinterface](https://go.microsoft.com/fwlink/?LinkID=144867)の試行、 [ICorProfilerCallback3](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)インターフェイスで、デタッチ操作をサポートするために実装する必要がある必要があります。 デタッチは試行されませんでした。|  
|CORPROF_E_IMMUTABLE_FLAGS_SET|プロファイラーが起動時に変更できないフラグを設定しているため、デタッチできません。 デタッチは試行されませんでした。プロファイラーは完全にアタッチされたままです。|  
|CORPROF_E_IRREVERSIBLE_INSTRUMENTATION_PRESENT|デタッチは、プロファイラーの使用が Microsoft intermediate language (MSIL) コードでは、インストルメント化されているため、または挿入`enter` / `leave`フックします。 デタッチは試行されませんでした。プロファイラーは完全にアタッチされたままです。<br /><br /> **注**インストルメント化した MSIL は、コードを使用してプロファイラーによって提供されるコードでは、 [SetILFunctionBody](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setilfunctionbody-method.md)メソッド。|  
|CORPROF_E_RUNTIME_UNINITIALIZED|マネージ アプリケーションでランタイムがまだ初期化されていません。 (つまり、ランタイムは完全には読み込まれていません。)このエラー コードは、プロファイラー コールバックの内部でデタッチが要求されたときに返される可能性があります[icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)メソッド。|  
|CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT|サポートされていないタイミングで `RequestProfilerDetach` が呼び出されました。 これは、内からされませんが、マネージ スレッドでメソッドが呼び出された場合に発生します、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)メソッド内から、 [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)ガベージ コレクションが許されないメソッド。 詳細については、次を参照してください。 [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)します。|  
  
## <a name="remarks"></a>Remarks  
 デタッチ プロシージャの実行中に、デタッチ スレッド (プロファイラーのデタッチのために作成されたスレッド) は、すべてのスレッドがプロファイラーのコードを終了したかどうかを時々チェックします。 プロファイラーは、退避が終了するまでの予想時間を、`dwExpectedCompletionMilliseconds` パラメーターを介して提供する必要があります。 使用に適した値は、特定の `ICorProfilerCallback*` メソッド内でプロファイラーが使う通常の時間です。この値は、プロファイラーが使うと想定される最大時間の半分未満にしないでください。  
  
 デタッチ スレッドでは `dwExpectedCompletionMilliseconds` を使用して、プロファイラーのコールバック コードがすべてのスタックからポップされたかどうかをチェックする前にスリープする時間の長さを指定します。 次のアルゴリズムの詳細は今後の CLR のリリースで変更される可能性がありますが、これはプロファイラーをアンロードしても安全なタイミングを決定するために `dwExpectedCompletionMilliseconds` を利用する 1 つの方法を示しています。 デタッチ スレッドはまず `dwExpectedCompletionMilliseconds` ミリ秒間、スリープ状態になります。 デタッチ スレッドがスリープ 2 回のこの時点で、もう一度、スリープ状態からアクティブになる後、は、CLR は、プロファイラーのコールバック コードがまだ存在することを検出した場合は、 `dwExpectedCompletionMilliseconds` (ミリ秒)。 この 2 回目のスリープから復帰した後に、プロファイラーのコールバック コードがまだ存在することがデタッチ スレッドで検出された場合、再チェックが行われる前に 10 分間、スリープ状態になります。 デタッチ スレッドは継続して 10 分ごとに再チェックを行います。  
  
 プロファイラーが `dwExpectedCompletionMilliseconds` を 0 (ゼロ) に指定している場合、CLR は既定値 5000 を使用します。この設定では、チェックが 5 秒後に行われ、その次は 10 秒後に、それ以降は 10 分ごとに再チェックが行われます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo3 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
