---
title: CorDebugBlockingObject 構造体
ms.date: 03/30/2017
api_name:
- CorDebugBlockingObject Structure
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingObject
helpviewer_keywords:
- CorDebugBlockingObject structure [.NET Framework debugging]
ms.assetid: 5944edd1-0914-4efa-aba0-d5a277c38b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 12a114ea65aca544d653704cdfb01ed15d19c581
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59143222"
---
# <a name="cordebugblockingobject-structure"></a>CorDebugBlockingObject 構造体
スレッドおよびスレッドがブロックされている特定の理由をブロックしているオブジェクトを定義します。  
  
## <a name="syntax"></a>構文  
  
```  
Typedef struct CorDebugBlockingObject  
{  
ICorDebugValue pBlockingObject;  
DWORD dwTimeout;  
CorDebugBlockingReason blockingReason;  
}  CorDebugBlockingObject;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`pBlockingObject`|スレッドがブロックしているオブジェクト。 このオブジェクトは、現在の同期状態の期間に対してのみ有効です。 同じ同期された状態で同じオブジェクトでは、2 つのスレッドがブロックして、期待する場合は可能性があります、 [icordebugvalue::getaddress](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getaddress-method.md)メソッドを同じ値を返します。 ただし、インターフェイスは、同等のポインターができない可能性があります。|  
|`dwTimeout`|ブロック操作までのミリ秒数は、タイムアウト、または、値は INFINITE で、ものではタイムアウトしないことを示します。タイムアウト値には、時間が残っているではなく、ブロック操作の時間の合計の長さを指定します。|  
|`blockingReason`|このオブジェクトのスレッドがブロックされている理由です。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
