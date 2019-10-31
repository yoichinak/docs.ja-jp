---
title: ICorDebugManagedCallback::NameChange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.NameChange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::NameChange
helpviewer_keywords:
- ICorDebugManagedCallback::NameChange method [.NET Framework debugging]
- NameChange method [.NET Framework debugging]
ms.assetid: a7018a0e-880e-4b68-b52a-1cd22c7aad62
topic_type:
- apiref
ms.openlocfilehash: 456a79ec290964df8e9f74fc6ca19ef9aabe1230
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130675"
---
# <a name="icordebugmanagedcallbacknamechange-method"></a>ICorDebugManagedCallback::NameChange メソッド
アプリケーションドメインまたはスレッドの名前が変更されたことをデバッガーに通知します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT NameChange (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *pThread  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pAppDomain`  
 から名前が変更されたか、または名前の変更があったスレッドを含むアプリケーションドメインを表す、ツールオブジェクトへのポインター。  
  
 `pThread`  
 から名前の変更があったスレッドを表す、スレッドオブジェクトへのポインター。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
