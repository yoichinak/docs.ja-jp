---
title: CorDebugStepReason 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugStepReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugStepReason
helpviewer_keywords:
- CorDebugStepReason enumeration [.NET Framework debugging]
ms.assetid: fe248069-b33c-48e1-a777-06ac9b239c54
topic_type:
- apiref
ms.openlocfilehash: 6c73afb00cbd104cff3d310d1369097b459c131e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133686"
---
# <a name="cordebugstepreason-enumeration"></a>CorDebugStepReason 列挙型
個々のステップの結果を示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum CorDebugStepReason {  
    STEP_NORMAL,  
    STEP_RETURN,  
    STEP_CALL,  
    STEP_EXCEPTION_FILTER,  
    STEP_EXCEPTION_HANDLER,  
    STEP_INTERCEPT,  
    STEP_EXIT  
} CorDebugStepReason;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`STEP_NORMAL`|同じ関数内で通常どおりにステップ実行が完了しました。|  
|`STEP_RETURN`|関数が返された後、通常どおりにステップ実行を続行します。|  
|`STEP_CALL`|新しく呼び出された関数の先頭で、ステップ実行は通常どおり続行されます。|  
|`STEP_EXCEPTION_FILTER`|例外が生成され、制御が例外フィルターに渡されました。|  
|`STEP_EXCEPTION_HANDLER`|例外が生成され、制御が例外ハンドラーに渡されました。|  
|`STEP_INTERCEPT`|コントロールがインターセプターに渡されました。|  
|`STEP_EXIT`|ステップが完了する前にスレッドが終了しました。|  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StepComplete メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)
- [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
