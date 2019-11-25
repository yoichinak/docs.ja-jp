---
title: ICorProfilerInfo10::ResumeRuntime
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo10.ResumeRuntime
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 515b42d649f68345f9924f57a91d146556480e0a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449807"
---
# <a name="icorprofilerinfo10resumeruntime-method"></a>ICorProfilerInfo10::ResumeRuntime Method

Resumes the runtime without performing a GC.

## <a name="syntax"></a>構文

```cpp
HRESULT ResumeRuntime();
```

## <a name="requirements"></a>［要件］

**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).

**ヘッダー** : CorProf.idl、CorProf.h

**ライブラリ:** CorGuids.lib

**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]

## <a name="see-also"></a>関連項目

- [ICorProfilerInfo10 Interface](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-interface.md)
