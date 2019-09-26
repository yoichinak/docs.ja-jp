---
title: CorDebugBlockingReason 列挙体
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 99fcf160b3e3b2b238520e3db5ba2e74b270380a
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274141"
---
# <a name="cordebugblockingreason-enumeration"></a>CorDebugBlockingReason 列挙体
指定されたオブジェクト上でスレッドがブロックされる理由を指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`BLOCKING_NONE`|内部使用のみ。|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|スレッドが、オブジェクトのモニターロックに関連付けられているクリティカルセクションを取得しようとしています。 通常、このエラー <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType>は、メソッドまたは<xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType>メソッドのいずれかを呼び出すと発生します。|  
|`BLOCKING_MONITOR_EVENT`|スレッドが、オブジェクトのモニターロックに関連付けられているイベントを待機しています。 通常、これは、 <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait`メソッドのいずれかを呼び出すと発生します。|  
  
## <a name="remarks"></a>コメント  
 メンバーまたは`BLOCKING_MONITOR_EVENT`メンバーが[CorDebugBlockingObject](cordebugblockingobject-structure.md)構造体で使用され`pBlockingObject`ている場合、構造体のメンバーは、入力されるオブジェクトを表す "ICorDebugValue" インターフェイスを指します。 `BLOCKING_MONITOR_CRITICAL_SECTION` また、 [ICorDebugHeapValue3](icordebugheapvalue3-interface.md)インターフェイスを実装することも保証されます。  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のデバッグ](debugging-enumerations.md)
- [デバッグ](index.md)
