---
title: ICorProfilerCallback2::RootReferences2 メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.RootReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::RootReferences2
helpviewer_keywords:
- RootReferences2 method [.NET Framework profiling]
- ICorProfilerCallback2::RootReferences2 method [.NET Framework profiling]
ms.assetid: 55a2f907-d216-42eb-8f2f-e5d59c2eebd6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 563a2e19c9c254870b3e767253a276a201e631a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779307"
---
# <a name="icorprofilercallback2rootreferences2-method"></a>ICorProfilerCallback2::RootReferences2 メソッド
ガベージ コレクションが発生した後、ルート参照について、プロファイラーに通知します。 このメソッドは、の拡張機能、 [icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT RootReferences2(  
    [in] ULONG  cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_KIND rootKinds[],  
    [in, size_is(cRootRefs)] COR_PRF_GC_ROOT_FLAGS rootFlags[],  
    [in, size_is(cRootRefs)] UINT_PTR rootIds[]);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cRootRefs`  
 [in]要素の数、 `rootRefIds`、 `rootKinds`、 `rootFlags`、および`rootIds`配列。  
  
 `rootRefIds`  
 [in]オブジェクト Id は、静的オブジェクトまたはスタック上のオブジェクトのいずれかの参照の配列。 内の要素、`rootKinds`配列に対応する要素を分類する情報を提供する、`rootRefIds`配列。  
  
 `rootKinds`  
 [in]配列の[COR_PRF_GC_ROOT_KIND](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-kind-enumeration.md)ガベージ コレクションのルートの種類を示す値。  
  
 `rootFlags`  
 [in]配列の[COR_PRF_GC_ROOT_FLAGS](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-root-flags-enumeration.md)ガベージ コレクションのルートのプロパティを記述する値。  
  
 `rootIds`  
 [in]UINT_PTR の配列の値の値に応じて、ガベージ コレクションのルートに関する追加情報を格納する整数を指す、`rootKinds`パラメーター。  
  
 ルートの種類が、スタックの場合は、ルート ID は、変数を含む関数です。 そのルート ID が 0 の場合、関数、CLR の内部にある名前のない機能です。 ルートの種類が識別するハンドルである場合は、ルート ID は、ガベージ コレクション ハンドル用です。 その他のルート型の ID は非透過の値は、され、無視する必要があります。  
  
## <a name="remarks"></a>Remarks  
 `rootRefIds`、 `rootKinds`、 `rootFlags`、および`rootIds`配列は並列配列です。 つまり、 `rootRefIds[i]`、 `rootKinds[i]`、 `rootFlags[i]`、および`rootIds[i]`同じルートに関するものすべてです。  
  
 両方`RootReferences`と`RootReferences2`をプロファイラーに通知と呼ばれます。 プロファイラーは通常実装方法の 1 つまたは両方ではなく、他の情報が渡されたため、`RootReferences2`渡さのスーパー セット`RootReferences`します。  
  
 内のエントリの可能性が`rootRefIds`を対応するルートの参照が null と、マネージ ヒープ上のオブジェクトを参照していないことを意味する 0 にします。  
  
 によって返されるオブジェクト Id`RootReferences2`コールバック自体の中に無効なため、古いアドレスから新しいアドレスにオブジェクトを移動中にガベージ コレクションがある可能性があります。 このため、`RootReferences2` 呼び出しの間、プロファイラーはオブジェクトを検査するべきではありません。 ときに[icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)が呼び出されると、すべてのオブジェクトの新しい場所に移動されているし、安全に検査することができます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
