---
title: ICorDebugThread2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4d21c221bba3ac668924003f96580bb660229ad7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963003"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 インターフェイス
は、"、" スレッドインターフェイスの論理的な拡張として機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetActiveFunctions メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|スレッドのフレーム内のアクティブな関数に関するデータを格納する COR_ACTIVE_FUNCTION インスタンスの配列を取得します。|  
|[GetConnectionID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|この`ICorDebugThread2`の接続識別子を取得します。|  
|[GetTaskID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|この`ICorDebugThread2`のタスク識別子を取得します。|  
|[GetVolatileOSThreadID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|この`ICorDebugThread2`のオペレーティングシステムスレッド識別子を取得します。|  
|[InterceptCurrentException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|デバッガーがスレッドの現在の例外をインターセプトできるようにします。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
