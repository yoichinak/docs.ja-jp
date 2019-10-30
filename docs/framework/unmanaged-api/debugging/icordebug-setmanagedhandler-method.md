---
title: ICorDebug::SetManagedHandler メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.SetManagedHandler
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::SetManagedHandler
helpviewer_keywords:
- ICorDebug::SetManagedHandler method [.NET Framework debugging]
- SetManagedHandler method [.NET Framework debugging]
ms.assetid: d079131b-685b-4869-95be-826b88d28bd2
topic_type:
- apiref
ms.openlocfilehash: 88a007654646ba42ebcaf1b42e002282a1040c7f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134064"
---
# <a name="icordebugsetmanagedhandler-method"></a>ICorDebug::SetManagedHandler メソッド
マネージイベントのイベントハンドラーオブジェクトを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetManagedHandler (  
    [in] ICorDebugManagedCallback     *pCallback  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pCallback`  
 からイベントハンドラーオブジェクトである、ツール[コールバック](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)オブジェクトへのポインター。  
  
## <a name="remarks"></a>Remarks  
 `SetManagedHandler` は、作成時に呼び出す必要があります。  
  
 `ICorDebugManagedCallback` の実装に、デバッグ中のアプリケーションのデバッグイベントを処理するための十分なインターフェイスが含まれていない場合、`SetManagedHandler` は E_NOINTERFACE の HRESULT を返します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
