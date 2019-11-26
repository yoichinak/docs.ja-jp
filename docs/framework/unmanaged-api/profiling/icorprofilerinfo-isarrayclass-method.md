---
title: ICorProfilerInfo::IsArrayClass メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
ms.openlocfilehash: 57515ac4670b9b7e25bb496851347a62e1b246df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438711"
---
# <a name="icorprofilerinfoisarrayclass-method"></a>ICorProfilerInfo::IsArrayClass メソッド
Determines whether the specified class is an array class.  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a>パラメーター  
 `classId`  
 [in] The ID of the class to be examined.  
  
 `pBaseElemType`  
 [out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.  
  
 `pBaseClassId`  
 [out] A pointer to the class ID of the array elements, when available.  
  
 `pcRank`  
 [out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.  
  
## <a name="remarks"></a>Remarks  
 If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters. Otherwise, it returns S_FALSE.  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
