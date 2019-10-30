---
title: ICorDebugRemote::DebugActiveProcessEx メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
ms.openlocfilehash: 83cc4eadca7c337c06c5fbf9f0e74306c2b9cb99
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131271"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>ICorDebugRemote::DebugActiveProcessEx メソッド
デバッガーでリモートコンピューター上のプロセスを起動します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pRemoteTarget`  
 からツールの[ターゲットインターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)を指すポインター。 このパラメーターは、プロセスが実行されているコンピューターを決定するために使用されます。  
  
 `id`  
 からデバッガーがアタッチされるプロセスの ID。  
  
 `win32Attach`  
 [in] デバッガーをプロセスの Win32 デバッガーとして動作させる必要があるかどうかを `true` し、アンマネージコールバックをディスパッチします。それ以外の場合は、`false`ます。  
  
 `ppProcess`  
 入出力デバッガーがアタッチされているプロセスを表す "いいプロセス" オブジェクトのアドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 リモートコンピューター上のプロセスに正常にアタッチされました。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 リモートコンピューター上のプロセスにアタッチできません。  
  
## <a name="remarks"></a>Remarks  
 混合モードのデバッグは、Silverlight ではサポートされていません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** 4.5、4、3.5 SP1  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRemote インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
