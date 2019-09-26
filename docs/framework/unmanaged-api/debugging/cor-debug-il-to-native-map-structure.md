---
title: COR_DEBUG_IL_TO_NATIVE_MAP 構造体
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: babb1ace1385c241b782691f22bfb4fbb689e310
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274072"
---
# <a name="cor_debug_il_to_native_map-structure"></a>COR_DEBUG_IL_TO_NATIVE_MAP 構造体
Microsoft intermediate language (MSIL) コードをネイティブ コードにマップするために使用するオフセットが含まれます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`ilOffset`|MSIL コードのオフセット。|  
|`nativeStartOffset`|ネイティブコードの開始位置のオフセット。|  
|`nativeEndOffset`|ネイティブコードの末尾のオフセット。|  
  
## <a name="requirements"></a>要件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Corprof.idl、CorDebug .idl  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetILToNativeMapping メソッド](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [GetILToNativeMapping メソッド](icordebugcode-getiltonativemapping-method.md)
- [デバッグ構造体](debugging-structures.md)
- [デバッグ](index.md)
