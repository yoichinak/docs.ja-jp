---
title: COR_PRF_GC_GENERATION_RANGE 構造体
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_GENERATION_RANGE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_GENERATION_RANGE
helpviewer_keywords:
- COR_PRF_GC_GENERATION_RANGE structure [.NET Framework profiling]
ms.assetid: e7e07273-8d10-4a68-807e-59634e3f8c5e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 646c4e37a7fab503a26557f9fdfc926b1186b17b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216705"
---
# <a name="corprfgcgenerationrange-structure"></a>COR_PRF_GC_GENERATION_RANGE 構造体
ガーベッジ コレクションを実行中のメモリ範囲 (ブロック) を説明します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef struct COR_PRF_GC_GENERATION_RANGE {  
    COR_PRF_GC_GENERATION generation;  
    ObjectID rangeStart;  
    UINT_PTR rangeLength;  
    UINT_PTR rangeLengthReserved;  
} COR_PRF_GC_GENERATION_RANGE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`generation`|値、 [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)メモリ ブロックを生成するように指定する列挙体が属しています。|  
|`rangeStart`|メモリ ブロックの開始位置を指定するオブジェクトの ID。|  
|`rangeLength`|メモリ ブロック (つまり、ブロック内で使用されるメモリ量) の使用部分のサイズを指定する整数へのポインター。|  
|`rangeLengthReserved`|(つまり、ブロックのために予約されるメモリ量) メモリ ブロックのサイズを指定する整数へのポインター。|  
  
## <a name="remarks"></a>Remarks  
 `rangeLength`値は正確であることが保証場合にのみ[icorprofilerinfo 2::getgenerationbounds](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getgenerationbounds-method.md)または[icorprofilerinfo 2::getobjectgeneration](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getobjectgeneration-method.md)、使用するはどちらも、 `COR_PRF_GC_GENERATION_RANGE`構造体から呼び出される、 [icorprofilercallback 2::garbagecollectionstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)または[icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [構造体のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)
