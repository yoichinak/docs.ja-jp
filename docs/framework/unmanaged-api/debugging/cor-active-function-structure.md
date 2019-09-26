---
title: COR_ACTIVE_FUNCTION 構造体
ms.date: 03/30/2017
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50dd4acece43628b20b6bc50a539ee197e865855
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274154"
---
# <a name="cor_active_function-structure"></a>COR_ACTIVE_FUNCTION 構造体
スレッドのフレームで現在アクティブな機能に関する情報が含まれます。 この構造体は、 [ICorDebugThread2:: GetActiveFunctions](icordebugthread2-getactivefunctions-method.md)メソッドによって使用されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`pAppDomain`|`ilOffset`フィールドのアプリケーションドメイン所有者へのポインター。|  
|`pModule`|`ilOffset`フィールドのモジュール所有者へのポインター。|  
|`pFunction`|`ilOffset`フィールドの関数所有者へのポインター。|  
|`ilOffset`|フレームの MSIL (Microsoft 中間言語) オフセット。|  
|`flags`|将来の拡張のために予約されています。|  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
