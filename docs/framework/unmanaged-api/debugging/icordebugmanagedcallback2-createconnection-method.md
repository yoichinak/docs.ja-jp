---
title: ICorDebugManagedCallback2::CreateConnection メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.CreateConnection
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::CreateConnection
helpviewer_keywords:
- CreateConnection method [.NET Framework debugging]
- ICorDebugManagedCallback2::CreateConnection method [.NET Framework debugging]
ms.assetid: 49e647be-9d63-4250-9d11-704e2a400d1b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 300baeb4184bbb73704563671ab907fafbdb5284
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472630"
---
# <a name="icordebugmanagedcallback2createconnection-method"></a>ICorDebugManagedCallback2::CreateConnection メソッド
新しい接続が作成されたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateConnection (  
    [in] ICorDebugProcess     *pProcess,  
    [in] CONNID               dwConnectionId,  
    [in] WCHAR                *pConnName  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pProcess`  
 [in]接続が作成されたプロセスを表す"ICorDebugProcess"オブジェクトへのポインター  
  
 `dwConnectionId`  
 [in]新しい接続の ID。  
  
 `pConnName`  
 [in]新しい接続の名前へのポインター。  
  
## <a name="remarks"></a>Remarks  
 A`CreateConnection`コールバックは、次の場合のいずれかで発生します。  
  
-   ときに、デバッガーは、接続を含むプロセスにアタッチされます。 ランタイムの生成し、ディスパッチここを`CreateConnection`イベントと[icordebugmanagedcallback 2::changeconnection](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-changeconnection-method.md)プロセス内の各接続のイベント。  
  
-   ホストが呼び出したときに[iclrdebugmanager::beginconnection](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)で、[ホスト API](../../../../docs/framework/unmanaged-api/hosting/index.md)します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
