---
title: ICorDebugManagedCallback2::ChangeConnection メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.ChangeConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::ChangeConnection
helpviewer_keywords:
- ICorDebugManagedCallback2::ChangeConnection method [.NET Framework debugging]
- ChangeConnection method [.NET Framework debugging]
ms.assetid: 7263f9a9-4c0b-4d82-a181-288873fb2b18
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ff47576fb6a9d1f681aba1157efd63190b8dc23
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491387"
---
# <a name="icordebugmanagedcallback2changeconnection-method"></a>ICorDebugManagedCallback2::ChangeConnection メソッド
指定された接続に関連付けられているタスクのセットが変更されたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ChangeConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pProcess`  
 [in]変更された接続を含むプロセスを表す"ICorDebugProcess"オブジェクトへのポインター。  
  
 `dwConnectionId`  
 [in]変更された接続の ID。  
  
## <a name="remarks"></a>Remarks  
 A`ChangeConnection`コールバックは、次の場合のいずれかで発生します。  
  
-   ときに、デバッガーは、接続を含むプロセスにアタッチされます。 ランタイムの生成し、ディスパッチここを[icordebugmanagedcallback 2::createconnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-createconnection-method.md)イベントと`ChangeConnection`プロセス内の各接続のイベント。 A`ChangeConnection`その接続の一連のタスクが作成されてから変更されたかどうかに関係なく、すべての既存の接続のイベントが生成されます。  
  
-   ホストが呼び出したときに[iclrdebugmanager::setconnectiontasks](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)で、[ホスト API](../../../../docs/framework/unmanaged-api/hosting/index.md)します。  
  
 デバッガーでは、新しい変更を取得するプロセスのすべてのスレッドをスキャンする必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
