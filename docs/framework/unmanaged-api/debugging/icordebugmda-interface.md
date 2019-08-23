---
title: ICorDebugMDA インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugMDA
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA
helpviewer_keywords:
- ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 8ecbb854-295c-4dd4-b9fc-01ebeac46e06
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a662185bb84e9a66573b43b26ffcd256ecb943f5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909848"
---
# <a name="icordebugmda-interface"></a>ICorDebugMDA インターフェイス
マネージド デバッグ アシスタント (MDA) メッセージを表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetDescription メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getdescription-method.md)|この MDA の説明を格納している文字列を取得します。|  
|[GetFlags メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getflags-method.md)|この MDA に関連付けられているフラグを取得します。|  
|[GetName メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getname-method.md)|この MDA の名前を格納している文字列を取得します。|  
|[GetOSThreadId メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getosthreadid-method.md)|この MDA が実行されているオペレーティングシステムのスレッド id を取得します。|  
|[GetXML メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-getxml-method.md)|この MDA に関連付けられている XML の完全ストリームを取得します。|  
  
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
- [マネージド デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
