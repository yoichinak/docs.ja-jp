---
title: ICorDebugManagedCallback::EvalComplete メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.EvalComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::EvalComplete
helpviewer_keywords:
- ICorDebugManagedCallback::EvalComplete method [.NET Framework debugging]
- EvalComplete method [.NET Framework debugging]
ms.assetid: f74ab4eb-cd1b-407c-a66d-8ec0d85647f3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1261942865419762fa454eb8d4bc5e5d99e86d6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193175"
---
# <a name="icordebugmanagedcallbackevalcomplete-method"></a>ICorDebugManagedCallback::EvalComplete メソッド
評価が完了したことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT EvalComplete (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread,  
    [in] ICorDebugEval      *pEval  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 [in]評価が実行されたアプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。  
  
 `pThread`  
 [in]評価が実行されたスレッドを表す ICorDebugThread オブジェクトへのポインター。  
  
 `pEval`  
 [in]評価を実行するコードを表す ICorDebugEval オブジェクトへのポインター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
