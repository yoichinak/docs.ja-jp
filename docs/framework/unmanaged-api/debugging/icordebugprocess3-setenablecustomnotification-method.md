---
title: ICorDebugProcess3::SetEnableCustomNotification メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8c8725bf21aefa3abf5fc41366d8f983bd686b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175748"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>ICorDebugProcess3::SetEnableCustomNotification メソッド
有効にし、指定した型のカスタムのデバッガー通知を無効にします。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pClass`  
 [in]カスタムのデバッガー通知を指定する型。  
  
 `fEnable`  
 [in]`true`カスタムのデバッガー通知を有効にするには`false`通知を無効にします。 既定値は `false` です。  
  
## <a name="remarks"></a>Remarks  
 ときに`fEnable`に設定されている`true`への呼び出し、 <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> trigger メソッド、 [icordebugmanagedcallback 3::customnotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)コールバック。 既定では通知が無効になっていますそのため、デバッガーは、通知の種類が認識し、処理する必要があるを指定する必要があります。 [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)クラスのスコープは、アプリケーション ドメインによって、デバッガーを呼び出す必要があります`SetEnableCustomNotification`のプロセス全体で、通知を受信する場合にプロセス内の各アプリケーション ドメイン。  
  
 以降では、 [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]、のみサポートされている通知がスレッド間の依存関係の通知。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
