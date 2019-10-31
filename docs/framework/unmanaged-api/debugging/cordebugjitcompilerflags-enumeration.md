---
title: CorDebugJITCompilerFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
ms.openlocfilehash: 739b491d343c0eba76160c15719069ffae385f46
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73097976"
---
# <a name="cordebugjitcompilerflags-enumeration"></a>CorDebugJITCompilerFlags 列挙型
マネージド Just-In-Time (JIT) コンパイラの動作に影響を与える値が含まれます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|コンパイラがコンパイルデータを追跡し、最適化を許可することを指定します。|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|コンパイラがコンパイルデータを追跡する必要があるが、最適化を無効にすることを指定します。|  
|`CORDEBUG_JIT_ENABLE_ENC`|コンパイラがコンパイルデータを追跡し、最適化を無効にして、エディットコンティニュテクノロジを有効にする必要があることを指定します。|  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
