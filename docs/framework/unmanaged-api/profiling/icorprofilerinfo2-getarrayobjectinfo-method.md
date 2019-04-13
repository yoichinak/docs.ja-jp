---
title: ICorProfilerInfo2::GetArrayObjectInfo メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5276c69da05cedcd3195a09da12ddc5b2d0fed67
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201274"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a>ICorProfilerInfo2::GetArrayObjectInfo メソッド
配列オブジェクトに関する詳細な情報を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a>パラメーター  
 `objectId`  
 [in]有効な配列オブジェクトの ID。  
  
 `cDimensions`  
 [in]配列のランク (次元数)。  
  
 `pDimensionSizes`  
 [out]各配列の次元のサイズを表す整数を格納する配列。  
  
 `pDimensionLowerBounds`  
 [out]整数を含む配列、配列の次元の下限を表す各バインドされています。  
  
 `ppData`  
 [out]に従ってレイアウトは、配列の生バッファーのアドレスへのポインター、C++規則。  
  
## <a name="remarks"></a>Remarks  
 `pDimensionSizes`と`pDimensionLowerBounds`は並列配列は、各配列内の同じインデックス位置にある要素は、同じエンティティの特性。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
