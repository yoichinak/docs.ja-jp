---
title: グローバル静的関数のプロファイル
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework profiling]
- profiling global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], profiling
ms.assetid: 08a13a57-dc49-488d-b937-31e3051fda97
ms.openlocfilehash: d1d9b0a4c61ce7c3f8f9792046fb4bddf0fdfa05
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447438"
---
# <a name="profiling-global-static-functions"></a>グローバル静的関数のプロファイル
This section describes the unmanaged API functions that the profiling API uses.  
  
## <a name="in-this-section"></a>このセクションの内容  
  
## <a name="net-framework-version-1-profiling-functions"></a>.NET Framework version 1 Profiling Functions  
 [FunctionEnter 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter-function.md)  
 Notifies the profiler that control is being passed to a function. Deprecated in the .NET Framework 2.0.  
  
 [FunctionLeave 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)  
 Notifies the profiler that a function is about to return to the caller. Deprecated in the .NET Framework 2.0.  
  
 [FunctionTailcall 関数](../../../../docs/framework/unmanaged-api/profiling/functiontailcall-function.md)  
 Notifies the profiler that the currently executing function is about to perform a tail call to another function. Deprecated in the .NET Framework 2.0.  
  
## <a name="net-framework-version-2-profiling-functions"></a>.NET Framework version 2 Profiling Functions  
 [FunctionIDMapper 関数](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)  
 Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md), [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md), and [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) callbacks for that function. Also enables the profiler to indicate whether it wants to receive callbacks for that function  
  
 [FunctionEnter2 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 Notifies the profiler that control is being passed to a function and provides information about the stack frame and function arguments. Deprecated in the .NET Framework 4.  
  
 [FunctionLeave2 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 Notifies the profiler that a function is about to return to the caller and provides information about the stack frame and function return value. Deprecated in the .NET Framework 4.  
  
 [FunctionTailcall2 関数](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 Notifies the profiler that the currently executing function is about to perform a tail call to another function and provides information about the stack frame. Deprecated in the .NET Framework 4.  
  
 [StackSnapshotCallback 関数](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md)  
 Provides the profiler with information about each managed frame and each run of unmanaged frames on the stack during a stack walk, which is initiated by the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.  
  
## <a name="net-framework-version-4-profiling-functions"></a>.NET Framework version 4 Profiling Functions  
 [FunctionIDMapper2 関数](../../../../docs/framework/unmanaged-api/profiling/functionidmapper2-function.md)  
 Notifies the profiler that the given identifier of a function may be remapped to an alternative ID to be used in the [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md), and [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md), or[FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md), [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md), and [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) callbacks for that function. Also enables the profiler to indicate whether it wants to receive callbacks for that function.  
  
 `FunctionIDMapper2` extends the [FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md) function with a `clientData` parameter, which profilers may use to disambiguate among runtimes.  
  
 [FunctionEnter3 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 Notifies the profiler that control is being passed to a function.  
  
 [FunctionEnter3WithInfo 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)  
 Notifies the profiler that control is being passed to a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md) to retrieve the stack frame and function arguments.  
  
 [FunctionLeave3 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 Notifies the profiler that control is being returned from a function.  
  
 [FunctionLeave3WithInfo 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 Notifies the profiler that control is being returned from a function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionLeave3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionleave3info-method.md) to retrieve the stack frame and the return value.  
  
 [FunctionTailcall3 関数](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 Notifies the profiler that the currently executing function is about to perform a tail call to another function.  
  
 [FunctionTailcall3WithInfo 関数](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)  
 Notifies the profiler that the currently executing function is about to perform a tail call to another function, and provides a handle that can be passed to [ICorProfilerInfo3::GetFunctionTailcall3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md) to retrieve the stack frame.  
  
## <a name="related-sections"></a>関連項目  
 [プロファイルの概要](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
  
 [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
  
 [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
  
 [構造体のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
