---
title: ICorDebugProcess6::ProcessStateChanged メソッド
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a4dcee3b396d9533f3169db1ea54a6cdc6086c8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948591"
---
# <a name="icordebugprocess6processstatechanged-method"></a>ICorDebugProcess6::ProcessStateChanged メソッド
通知[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)プロセスが実行されています。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a>パラメーター  
 `change`  
 [in]メンバー、 [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md)列挙型  
  
## <a name="remarks"></a>Remarks  
 デバッガーに通知するには、このメソッドを呼び出して[ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)プロセスが実行されています。  
  
> [!NOTE]
>  このメソッドは .NET ネイティブでのみ使用できます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess6 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
