---
title: ICorDebugManagedCallback::BreakpointSetError メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.BreakpointSetError
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::BreakpointSetError
helpviewer_keywords:
- BreakpointSetError method [.NET Framework debugging]
- ICorDebugManagedCallback::BreakpointSetError method [.NET Framework debugging]
ms.assetid: f2b773a4-c4d0-429c-9717-51d6e2ed86af
topic_type:
- apiref
ms.openlocfilehash: dae04e1809c1bb3260461086a4953b8b4e5cce52
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122568"
---
# <a name="icordebugmanagedcallbackbreakpointseterror-method"></a>ICorDebugManagedCallback::BreakpointSetError メソッド
関数が just-in-time (JIT) コンパイルされる前に設定されたブレークポイントを共通言語ランタイムが正しくバインドできなかったことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT BreakpointSetError (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugBreakpoint *pBreakpoint,  
    [in] DWORD                dwError  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 からバインドされていないブレークポイントを含むアプリケーションドメインを表す、のオブジェクトへのポインター。  
  
 `pThread`  
 からバインドされていないブレークポイントを含むスレッドを表す、表示スレッドオブジェクトへのポインター。  
  
 `pBreakpoint`  
 からバインドされていないブレークポイントを表す ICorDebugBreakpoint オブジェクトへのポインター。  
  
 `dwError`  
 からエラーを示す整数。  
  
## <a name="remarks"></a>Remarks  
 指定されたブレークポイントはヒットしません。 デバッガーは、非アクティブ化して再バインドする必要があります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
