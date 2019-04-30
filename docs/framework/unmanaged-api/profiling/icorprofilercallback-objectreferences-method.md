---
title: ICorProfilerCallback::ObjectReferences メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ObjectReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ObjectReferences
helpviewer_keywords:
- ObjectReferences method [.NET Framework profiling]
- ICorProfilerCallback::ObjectReferences method [.NET Framework profiling]
ms.assetid: dd5e9b64-b4a3-4ba6-9be6-ddb540f4ffcf
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1142b33f029708d93cc3b808dc6be2b2df5b0ee3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942278"
---
# <a name="icorprofilercallbackobjectreferences-method"></a>ICorProfilerCallback::ObjectReferences メソッド
指定したオブジェクトによって参照されているメモリ内のオブジェクトをプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ObjectReferences(  
    [in]  ObjectID objectId,  
    [in]  ClassID  classId,  
    [in]  ULONG    cObjectRefs,  
    [in, size_is(cObjectRefs)] ObjectID objectRefIds[] );  
```  
  
## <a name="parameters"></a>パラメーター  
 `objectId`  
 [in]オブジェクトを参照しているオブジェクトの ID。  
  
 `classId`  
 [in]指定したオブジェクトのインスタンスでは、クラスの ID。  
  
 `cObjectRefs`  
 [in]指定したオブジェクトによって参照されるオブジェクトの数 (つまり、内の要素の数、`objectRefIds`配列)。  
  
 `objectRefIds`  
 [in]によって参照されるオブジェクトの Id の配列`objectId`します。  
  
## <a name="remarks"></a>Remarks  
 `ObjectReferences`ガベージ コレクションが完了した後のヒープの残りの各オブジェクトのメソッドが呼び出されます。 プロファイラーがこのコールバックからエラーを返した場合、プロファイリング サービスは、次のガベージ コレクションされるまでこのコールバックの呼び出しを中止します。  
  
 `ObjectReferences`コールバックを組み合わせて使用することができます、 [icorprofilercallback::rootreferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md)ランタイムの完全なオブジェクト参照グラフを作成するコールバック。 共通言語ランタイム (CLR) により、それぞれのオブジェクト参照を一度だけ報告、`ObjectReferences`メソッド。  
  
 によって返されるオブジェクト Id`ObjectReferences`コールバック自体の中に無効なため、オブジェクトを移動中にガベージ コレクションがある可能性があります。 そのため、プロファイラーは、中にオブジェクトを検査する試行する必要がありますいないを`ObjectReferences`呼び出します。 ときに[icorprofilercallback 2::garbagecollectionfinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)を呼び出すと、ガベージ コレクションが完了し、検査を安全に行うことができます。  
  
 Null`ClassId`ことを示します`objectId`型をアンロードしていますがあります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
