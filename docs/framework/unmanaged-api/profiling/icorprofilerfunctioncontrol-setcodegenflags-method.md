---
title: ICorProfilerFunctionControl::SetCodegenFlags メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionControl.SetCodegenFlags
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags
helpviewer_keywords:
- ICorProfilerFunctionControl::SetCodegenFlags method [.NET Framework profiling]
- SetCodegenFlags method, ICorProfilerFunctionControl interface [.NET Framework profiling]
ms.assetid: a2d5daa5-b990-4ae5-bf2a-c0862fe58bd7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 286d8494990c528e810f20f3fe5bfb986fdd267a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487691"
---
# <a name="icorprofilerfunctioncontrolsetcodegenflags-method"></a>ICorProfilerFunctionControl::SetCodegenFlags メソッド
1 つまたは複数のフラグを設定、 [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)を - just-in-time (JIT) のコード生成を制御する列挙型の再コンパイルされた関数。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetCodegenFlags(  
    [in] DWORD flags);  
```  
  
## <a name="parameters"></a>パラメーター  
 `flags`  
 [in]1 つまたは複数のフラグ、 [COR_PRF_CODEGEN_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-codegen-flags-enumeration.md)列挙体。  
  
## <a name="remarks"></a>Remarks  
 プロファイラーは、使用して、このインターフェイスのインスタンスを取得、 [icorprofilercallback 4::getrejitparameters](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-getrejitparameters-method.md)コールバック。 `SetCodegenFlags` 再コンパイルされた関数のコード生成を制御するプロファイラーを使用できます。 他のすべての JIT 再コンパイル パラメーターと同様、コード生成フラグは、関数のすべてのインスタンスに適用されます。  
  
 JIT コンパイラでは、関数をコンパイルするときに、その他のソースで指定されたその他のフラグと共に、これらのコンパイル フラグと見なします。  その他のソースには、デバッガーが含まれます、、を使用して、起動時にプロファイラーがグローバル フラグが設定、 [icorprofilerinfo::seteventmask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)メソッド (値を持つ`COR_PRF_DISABLE_INLINING`と`COR_PRF_DISABLE_OPTIMIZATIONS`)、およびプロファイラーの[。Icorprofilercallback::jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)コールバック。  JIT コンパイラでは、最小限の最適化を要求するソースを優先します。  たとえば、プロファイラーを指定します`COR_PRF_DISABLE_INLINING`スタートアップ時が指定されていません`COR_PRF_CODEGEN_DISABLE_INLINING`で、 [icorprofilerfunctioncontrol::setcodegenflags](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setcodegenflags-method.md)コールバック、インライン展開は引き続き無効です。  同様に、プロファイラーが指定されていない場合`COR_PRF_CODEGEN_DISABLE_INLINING`で`SetCodegenFlags`を使用してインライン化、無効、 [icorprofilercallback::jitinlining](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitinlining-method.md)コールバック、インライン化が無効になっています。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerFunctionControl インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md)
