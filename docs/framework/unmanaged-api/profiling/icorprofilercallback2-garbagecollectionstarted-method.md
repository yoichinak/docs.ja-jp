---
title: ICorProfilerCallback2::GarbageCollectionStarted メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f5f9104dded44540c47c955c15354d8d76a27650
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183073"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a>ICorProfilerCallback2::GarbageCollectionStarted メソッド
ガベージ コレクションが開始されたことをコード プロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cGenerations`  
 [in]内のエントリの合計数、`generationCollected`配列。  
  
 `generationCollected`  
 [in]ブール値の配列`true`このガベージ コレクションによって収集されます。 それ以外の場合、配列のインデックスに対応する生成されている場合`false`します。  
  
 値によって、配列のインデックスが、 [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md)列挙体は、ジェネレーションを示します。  
  
 `reason`  
 [in]値、 [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md)ガベージ コレクション理由を示す列挙体が発生しました。  
  
## <a name="remarks"></a>Remarks  
 このガベージ コレクションに関連するすべてのコールバック間で発生する、`GarbageCollectionStarted`コールバックと、対応する[icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)コールバック。 これらのコールバックは、同じスレッドでは発生する必要があります。  
  
 プロファイラーが中に元の場所にオブジェクトを検査するは安全では、`GarbageCollectionStarted`コールバック。 ガベージ コレクターが移動オブジェクトからの戻り値の後に開始されます`GarbageCollectionStarted`します。 プロファイラーがこのコールバックから戻ると後、プロファイラーが受信するまで無効にするすべてのオブジェクト Id を検討してください、`ICorProfilerCallback2::GarbageCollectionFinished`コールバック。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
