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
ms.openlocfilehash: 82648714c375998e9daa1bb59cd9ebd9802b5794
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153934"
---
# <a name="icordebugthread2-interface"></a>ICorDebugThread2 インターフェイス
ICorDebugThread インターフェイスを論理的に拡張として機能します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetActiveFunctions メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|スレッドのフレーム内のアクティブな関数についてのデータを含む COR_ACTIVE_FUNCTION インスタンスの配列を取得します。|  
|[GetConnectionID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|この接続識別子を取得します。`ICorDebugThread2`します。|  
|[GetTaskID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|このタスクの識別子を取得`ICorDebugThread2`します。|  
|[GetVolatileOSThreadID メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|このオペレーティング システムのスレッド識別子を取得します。`ICorDebugThread2`します。|  
|[InterceptCurrentException メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|スレッドで現在の例外をインターセプトするデバッガーを使用します。|  
  
## <a name="remarks"></a>Remarks  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
