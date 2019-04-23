---
title: CorDebugIntercept 列挙型
ms.date: 03/30/2017
api_name:
- CorDebugIntercept
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIntercept
helpviewer_keywords:
- CorDebugIntercept enumeration [.NET Framework debugging]
ms.assetid: 3d5b642e-7ef2-428b-a5ae-509c35ed461a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0791a59e0325668960dcfc98816920db55bcfb87
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199935"
---
# <a name="cordebugintercept-enumeration"></a>CorDebugIntercept 列挙型
インターセプト (ステップ イン) できるコードの型を示します。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum CorDebugIntercept {  
    INTERCEPT_NONE                = 0x0,  
    INTERCEPT_CLASS_INIT          = 0x01,  
    INTERCEPT_EXCEPTION_FILTER    = 0x02,  
    INTERCEPT_SECURITY            = 0x04,  
    INTERCEPT_CONTEXT_POLICY      = 0x08,  
    INTERCEPT_INTERCEPTION        = 0x10,  
    INTERCEPT_ALL                 = 0xffff  
} CorDebugIntercept;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`INTERCEPT_NONE`|インターセプトできるコードはありません。|  
|`INTERCEPT_CLASS_INIT`|コンストラクターをインターセプトできます。|  
|`INTERCEPT_EXCEPTION_FILTER`|例外フィルターをインターセプトできます。|  
|`INTERCEPT_SECURITY`|セキュリティを適用するコードをインターセプトできます。|  
|`INTERCEPT_CONTEXT_POLICY`|コンテキスト ポリシーをインターセプトできます。|  
|`INTERCEPT_INTERCEPTION`|使用しません。|  
|`INTERCEPT_ALL`|すべてのコードをインターセプトできます。|  
  
## <a name="remarks"></a>Remarks  
 使用して、 [icordebugstepper::setinterceptmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)インターセプトできるコードの種類を構築する方法。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
