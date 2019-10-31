---
title: ICorDebugManagedCallback::ExitThread メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
ms.openlocfilehash: bbe2727e4b93cf6d7b3111b6060d170e497024a4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130771"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a>ICorDebugManagedCallback::ExitThread メソッド
マネージコードを実行していたスレッドが終了したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 からマネージスレッドを含むアプリケーションドメインを表す、コードの Appdomain オブジェクトへのポインター。  
  
 `thread`  
 からマネージスレッドを表す、コードスレッドオブジェクトへのポインター。  
  
## <a name="remarks"></a>Remarks  
 `ExitThread` コールバックが発生すると、スレッドはスレッド列挙に表示されなくなります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
