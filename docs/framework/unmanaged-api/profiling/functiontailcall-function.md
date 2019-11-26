---
title: FunctionTailcall 関数
ms.date: 03/30/2017
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
ms.openlocfilehash: c83a55a74542d94559b50b89ef784de0bd55d0db
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427345"
---
# <a name="functiontailcall-function"></a>FunctionTailcall 関数
Notifies the profiler that the currently executing function is about to perform a tail call to another function.  
  
> [!NOTE]
> The `FunctionTailcall` function is deprecated in the .NET Framework version 2.0. It will continue to work, but will incur a performance penalty. Use the [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) function instead.  
  
## <a name="syntax"></a>構文  
  
```cpp
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `funcID`  
 [in] The identifier of the currently executing function that is about to make a tail call.  
  
## <a name="remarks"></a>Remarks  
 The target function of the tail call will use the current stack frame, and will return directly to the caller of the function that made the tail call. This means that a [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md) callback will not be issued for a function that is the target of a tail call.  
  
 The `FunctionTailcall` function is a callback; you must implement it. The implementation must use the `__declspec`(`naked`) storage-class attribute.  
  
 The execution engine does not save any registers before calling this function.  
  
- On entry, you must save all registers that you use, including those in the floating-point unit (FPU).  
  
- On exit, you must restore the stack by popping off all the parameters that were pushed by its caller.  
  
 The implementation of `FunctionTailcall` should not block because it will delay garbage collection. The implementation should not attempt a garbage collection because the stack may not be in a garbage collection-friendly state. If a garbage collection is attempted, the runtime will block until `FunctionTailcall` returns.  
  
 Also, the `FunctionTailcall` function must not call into managed code or in any way cause a managed memory allocation.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **Header:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework Versions:** 1.1, 1.0  
  
## <a name="see-also"></a>関連項目

- [FunctionEnter2 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)
- [FunctionLeave2 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)
- [SetEnterLeaveFunctionHooks2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)
- [グローバル静的関数のプロファイル](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
