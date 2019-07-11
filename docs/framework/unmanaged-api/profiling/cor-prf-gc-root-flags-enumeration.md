---
title: COR_PRF_GC_ROOT_FLAGS 列挙型
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_ROOT_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_ROOT_FLAGS
helpviewer_keywords:
- COR_PRF_GC_ROOT_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 4611ee6f-0f05-4d84-91e1-e83d5e7dd7e4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7f179e3b01d6c3b34dfa765565a0fc38d0ba867c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67753699"
---
# <a name="corprfgcrootflags-enumeration"></a>COR_PRF_GC_ROOT_FLAGS 列挙型
ガベージ コレクションのルートのプロパティを示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    COR_PRF_GC_ROOT_PINNING = 0x1,  
    COR_PRF_GC_ROOT_WEAKREF = 0x2,  
    COR_PRF_GC_ROOT_INTERIOR = 0x4,  
    COR_PRF_GC_ROOT_REFCOUNTED = 0x8,  
} COR_PRF_GC_ROOT_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`COR_PRF_GC_ROOT_PINNING`|ルートでは、ガベージ コレクション オブジェクトを移動できないようにします。|  
|`COR_PRF_GC_ROOT_WEAKREF`|ルートは、ガベージ コレクションを妨げません。|  
|`COR_PRF_GC_ROOT_INTERIOR`|ルートは、オブジェクト自体ではなく、オブジェクトのフィールドを参照します。|  
|`COR_PRF_GC_ROOT_REFCOUNTED`|ルートでは、オブジェクトの参照カウントが特定の値の場合、ガベージ コレクションができないようにします。|  
  
## <a name="remarks"></a>Remarks  
 `COR_PRF_GC_ROOT_FLAGS` 特殊なルートに関する追加情報を提供するビットマスク。 ただし、すべてのルートは特別です。 たとえば、一部のルートを内部ポインター、固定、または参照カウントの弱い参照にすることはできません。 このようなルートを伝達するためのフラグはありません。 など、この列挙体を使用するメソッド、そのため、 [icorprofilercallback 2::rootreferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)メソッドでは、送信 0 すべてフラグを設定するかを示す、フラグ ビットがオフになっています。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のプロファイリング](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
