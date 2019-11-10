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
ms.openlocfilehash: 4201fe23bf54388510088e21471edce91809e94c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129800"
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
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [マネージド デバッグ アシスタントによるエラーの診断](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
