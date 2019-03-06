---
title: ICorDebugManagedCallback::LoadModule メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e49c20d7627f666efd6561cee19ca505f723b714
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474437"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a>ICorDebugManagedCallback::LoadModule メソッド
共通言語ランタイム (CLR) モジュールが正常に読み込まれたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 [in]モジュールのロード先のアプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。  
  
 `pModule`  
 [in]CLR モジュールを表す ICorDebugModule オブジェクトへのポインター。  
  
## <a name="remarks"></a>Remarks  
 `LoadModule`コールバックは、モジュールのメタデータを調べて、ジャストイン タイム (JIT) コンパイラ フラグを設定または有効化またはクラス、モジュールのコールバックの読み込みを無効にする適切な時間を提供します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [UnloadModule メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-unloadmodule-method.md)
- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
