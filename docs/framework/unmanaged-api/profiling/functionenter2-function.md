---
title: FunctionEnter2 関数
ms.date: 03/30/2017
api_name:
- FunctionEnter2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionEnter2
helpviewer_keywords:
- FunctionEnter2 function [.NET Framework profiling]
ms.assetid: ce7a21f9-0ca3-4b92-bc4b-bb803cae3f51
topic_type:
- apiref
ms.openlocfilehash: f4deec3e2b49b5cd6a924af8024e775c5c549f97
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440854"
---
# <a name="functionenter2-function"></a>FunctionEnter2 関数
Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments. This function supersedes the [FunctionEnter](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md) function.  
  
## <a name="syntax"></a>構文  
  
```cpp  
void __stdcall FunctionEnter2 (  
    [in]  FunctionID                       funcId,   
    [in]  UINT_PTR                         clientData,   
    [in]  COR_PRF_FRAME_INFO               func,   
    [in]  COR_PRF_FUNCTION_ARGUMENT_INFO  *argumentInfo  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `funcId`  
 [in] The identifier of the function to which control is passed.  
  
 `clientData`  
 [in] The remapped function identifier, which the profiler previously specified by using the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function.  
  
 `func`  
 [in] A `COR_PRF_FRAME_INFO` value that points to information about the stack frame.  
  
 The profiler should treat this as an opaque handle that can be passed back to the execution engine in the [ICorProfilerInfo2::GetFunctionInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md) method.  
  
 `argumentInfo`  
 [in] A pointer to a [COR_PRF_FUNCTION_ARGUMENT_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-function-argument-info-structure.md) structure that specifies the locations in memory of the function's arguments.  
  
 In order to access argument information, the `COR_PRF_ENABLE_FUNCTION_ARGS` flag must be set. The profiler can use the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the event flags.  
  
## <a name="remarks"></a>Remarks  
 The values of the `func` and `argumentInfo` parameters are not valid after the `FunctionEnter2` function returns because the values may change or be destroyed.  
  
 The `FunctionEnter2` function is a callback; you must implement it. The implementation must use the `__declspec`(`naked`) storage-class attribute.  
  
 The execution engine does not save any registers before calling this function.  
  
- On entry, you must save all registers that you use, including those in the floating-point unit (FPU).  
  
- On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.  
  
 The implementation of `FunctionEnter2` should not block because it will delay garbage collection. The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state. If a garbage collection is attempted, the runtime will block until `FunctionEnter2` returns.  
  
 Also, the `FunctionEnter2` function must not call into managed code or in any way cause a managed memory allocation.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [FunctionLeave2 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [FunctionTailcall2 関数](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)
- [SetEnterLeaveFunctionHooks2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [グローバル静的関数のプロファイル](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
