---
title: ICorDebugManagedCallback::UnloadModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadModule
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadModule method [.NET Framework debugging]
- UnloadModule method [.NET Framework debugging]
ms.assetid: b12bfcd9-1e29-48bf-9a3d-44bfae5df5e8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae4c1cb251f7786a8415449f16b4eb26d15a4fb2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491270"
---
# <a name="icordebugmanagedcallbackunloadmodule-method"></a>ICorDebugManagedCallback::UnloadModule メソッド
共通言語ランタイム モジュール (DLL) がアンロードされたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT UnloadModule (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugModule     *pModule  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 [in]モジュールに含まれるアプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。  
  
 `pModule`  
 [in]モジュールを表す ICorDebugModule オブジェクトへのポインター。  
  
## <a name="remarks"></a>Remarks  
 この呼び出しの後、モジュールを使用しない必要があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [LoadModule メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-loadmodule-method.md)
- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
