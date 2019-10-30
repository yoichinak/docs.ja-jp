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
ms.openlocfilehash: ec60274648315c4fa38f3832d8d39c1a269956b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129702"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a>ICorDebugProcess3::SetEnableCustomNotification メソッド
指定された型のカスタムデバッガー通知を有効または無効にします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pClass`  
 からカスタムデバッガー通知を指定する型。  
  
 `fEnable`  
 [in] カスタムデバッガー通知を有効にする `true`通知を無効にする `false` ます。 既定値は `false`です。  
  
## <a name="remarks"></a>Remarks  
 `fEnable` が `true`に設定されている場合、<xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> メソッドを呼び出すと、 [ICorDebugManagedCallback3:: CustomNotification](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)コールバックがトリガーされます。 既定では、通知は無効になっています。そのため、デバッガーは、認識している通知の種類を指定し、処理を希望する必要があります。 このクラス[のクラスはアプリケーション](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)ドメインによってスコープが設定されているため、プロセス全体で通知を受け取る必要がある場合は、プロセス内のすべてのアプリケーションドメインに対して `SetEnableCustomNotification` を呼び出す必要があります。  
  
 .NET Framework 4 以降、サポートされている通知は、スレッド間の依存関係通知だけです。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
