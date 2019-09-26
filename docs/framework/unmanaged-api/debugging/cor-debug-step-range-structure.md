---
title: COR_DEBUG_STEP_RANGE 構造体
ms.date: 03/30/2017
api_name:
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 11d5e2eb5e2743fca4876ed09add79be3eba514f
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274200"
---
# <a name="cor_debug_step_range-structure"></a>COR_DEBUG_STEP_RANGE 構造体
コードの範囲に関するオフセット情報が含まれます。  
  
 この構造体は、 [ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md)メソッドによって使用されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`startOffset`|範囲の先頭のオフセット。|  
|`endOffset`|範囲の末尾のオフセット。|  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StepRange メソッド](icordebugstepper-steprange-method.md)
- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
