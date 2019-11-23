---
title: ICorProfilerInfo::BeginInprocDebugging メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
ms.openlocfilehash: fffc028c7706c86e8384483cc92ebad90b292861
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447749"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a>ICorProfilerInfo::BeginInprocDebugging メソッド
Initializes in-process debugging support. This method is obsolete in the .NET Framework version 2.0.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a>パラメーター  
 `fThisThreadOnly`  
 [in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.  
  
 `pdwProfilerContext`  
 [out] The pointer to a returned value that identifies the debugging session.  
  
## <a name="remarks"></a>Remarks  
 The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1. In-process debugging enabled a profiler to use the inspection portions of the debugging API. However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework Version:** 1.0  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
