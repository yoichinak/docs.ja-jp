---
title: ICorDebugThread4::GetCurrentCustomDebuggerNotification メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type:
- apiref
ms.openlocfilehash: ba4375511fe7f5aaee032c4e132de54808041111
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122443"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a>ICorDebugThread4::GetCurrentCustomDebuggerNotification メソッド

現在のスレッドの現在の[ICorDebugManagedCallback3:: CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)オブジェクトを取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a>パラメーター

`ppNotificationObject`\
入出力現在のスレッド上の現在の `ICorDebugManagedCallback3::CustomNotification` オブジェクトへのポインター。

## <a name="remarks"></a>Remarks

`ICorDebugManagedCallback3::CustomNotification` コールバック内からメソッドが呼び出されていない場合、または現在の通知オブジェクトが存在しない場合は、`ppNotificationObject` の値が null になります。

## <a name="requirements"></a>［要件］

**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。

**ヘッダー:** CorDebug.idl、CorDebug.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]

## <a name="see-also"></a>関連項目

- [ICorDebugThread4 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
