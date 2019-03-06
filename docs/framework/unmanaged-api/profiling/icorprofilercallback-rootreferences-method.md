---
title: ICorProfilerCallback::RootReferences メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RootReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cfab1d716b5a8b530561e2dc72442591eb0d8e42
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499031"
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences メソッド
ガベージ コレクション後のルート参照に関する情報をプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
## <a name="parameters"></a>パラメーター  
 `cRootRefs`  
 [in]参照の数、`rootRefIds`配列。  
  
 `rootRefIds`  
 [in]静的オブジェクトまたはスタック上のオブジェクトのいずれかを参照するオブジェクト Id の配列。  
  
## <a name="remarks"></a>Remarks  
 両方`RootReferences`と[icorprofilercallback 2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)をプロファイラーに通知と呼ばれます。 プロファイラーは、どちらかを実装通常しますが、どちらで情報が渡されるため`RootReferences2`渡さのスーパー セット`RootReferences`します。  
  
 可能性があります、 `rootRefIds` null オブジェクトを格納する配列。 たとえば、スタックで宣言されているすべてのオブジェクト参照は、ガベージ コレクターによってルートとして扱われますは常に報告されます。  
  
 によって返されるオブジェクト Id`RootReferences`コールバック自体の中に無効なため、古いアドレスから新しいアドレスにオブジェクトを移動中にガベージ コレクションがある可能性があります。 そのため、プロファイラーは、中にオブジェクトを検査する試行する必要がありますいないを`RootReferences`呼び出します。 ときに[icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)が呼び出されると、すべてのオブジェクトの新しい場所に移動されているし、安全に検査することができます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
