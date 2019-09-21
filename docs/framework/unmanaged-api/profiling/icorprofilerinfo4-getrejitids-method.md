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
ms.openlocfilehash: 805ceb60d2ac122df2382656b95b7bf5e7509bfc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855946"
---
# <a name="icorprofilerinfo4getrejitids-method"></a>ICorProfilerInfo4::GetReJITIDs メソッド
割り当てられている指定された関数のすべての JIT 再コンパイルバージョンを識別する Id の配列を返します。 これには、後で元に戻されたがまだ解放されていない関数の JIT 再コンパイルバージョンが含まれます (たとえば、元に戻された関数を含むアプリケーションドメインがまだ使用されている場合など)。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetReJITIDs (  
     [in]  FunctionID          functionId,  
     [in]  ULONG               cReJitIds,  
     [out] ULONG *             pcReJitIds,  
     [out, size_is(cReJitIds), length_is(*pcReJitIds)]   ReJITID        reJitIds[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `functionId`  
 からバージョンを列挙する対象の関数インスタンスの。`FunctionID`  
  
 `cReJitIds`  
 から`reJitIds`配列に割り当てられた JIT 再コンパイル済み id の数。  
  
 `pcReJitIds`  
 入出力JIT 再コンパイルされた Id の実際の数。  
  
 `reJitIds`  
 入出力指定した関数の JIT 再コンパイルされた Id を格納する、呼び出し元が割り当てた配列。  
  
## <a name="remarks"></a>Remarks  
 `GetReJITIDs`指定された関数インスタンスのアクティブな JIT 再コンパイル済み Id を列挙します。 これは、呼び出し元が割り当てた`ICorProfilerInfo`バッファーを受け入れる他の関数と同じ使用パターンに従います。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Corprof.idl、Corprof.idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerInfo4 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [プロファイリングのインターフェイス](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [プロファイル](../../../../docs/framework/unmanaged-api/profiling/index.md)
