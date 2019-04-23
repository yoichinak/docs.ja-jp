---
title: ICorProfilerInfo4::GetReJITIDs メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetReJITIDs
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetReJITIDs
helpviewer_keywords:
- GetReJITIDs method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetReJITIDs method [.NET Framework profiling]
ms.assetid: 634ac28c-a5b7-4fc3-af84-256c24ca8177
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d2d48e5fb070ec0334de579d2e28146177a87b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121616"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs メソッド
JIT 再コンパイルのすべてのバージョン指定の関数も割り当てられているを識別する Id の配列を返します。 これには、後で元に戻されますが (たとえば、元に戻された関数を含むアプリケーション ドメインでは、使用中で) ときに解放されていない関数の JIT 再コンパイルのバージョンが含まれます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `functionId`  
 [in]`FunctionID`関数インスタンスのバージョンを列挙するのです。  
  
 `cReJitIds`  
 [in]JIT 再コンパイルの Id の割り当ての数、`reJitIds`配列。  
  
 `pcReJitIds`  
 [out]実際に JIT 再コンパイルの Id の数。  
  
 `reJitIds`  
 [out]指定した関数の JIT 再コンパイルの Id を含む、呼び出し元が割り当てた配列。  
  
## <a name="remarks"></a>Remarks  
 `GetReJITIDs` 指定された関数のインスタンスのアクティブな JIT 再コンパイルの Id を列挙します。 他の同時使用状況パターンに従って`ICorProfilerInfo`呼び出し元が割り当てたバッファーを受け取る関数をします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
