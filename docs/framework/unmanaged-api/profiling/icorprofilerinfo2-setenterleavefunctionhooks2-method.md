---
title: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9f95a404ce7124a76ee527cdc70ccccf103838b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763179"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 メソッド
更新されたバージョンの「入力」、「のまま」、およびマネージ関数の"tailcall"フックで呼び出されるプロファイラー実装関数を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pFuncEnter`  
 [in]として使用する実装へのポインター、 [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)コールバック。  
  
 `pFuncLeave`  
 [in]として使用する実装へのポインター、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)コールバック。  
  
 `pFuncTailcall`  
 [in]として使用する実装へのポインター、 [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)コールバック。  
  
## <a name="remarks"></a>Remarks  
 `SetEnterLeaveFunctionHooks2`メソッドは、 [icorprofilerinfo::setenterleavefunctionhooks](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md)メソッド。 前者を使用して、tailcall/enter/leave のコールバックの以前のバージョンとして使用する関数を指定する tailcall/enter/leave のコールバックになり、後者の新しいバージョンとして使用する関数を指定します。  
  
 一度に 1 つだけの一連のコールバックがアクティブな可能性があります。 そのため、プロファイラーは、両方を呼び出す場合`ICorProfilerInfo::SetEnterLeaveFunctionHooks`と`SetEnterLeaveFunctionHooks2`、`SetEnterLeaveFunctionHooks2`使用されます。  
  
 `SetEnterLeaveFunctionHooks2`メソッドは、プロファイラーからのみ呼び出すことが[icorprofilercallback::initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)コールバック。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
