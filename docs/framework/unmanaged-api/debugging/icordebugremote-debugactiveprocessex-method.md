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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 45b919d90454c9424cadb1d4dfc3b0dfb09e5053
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209451"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a>ICorDebugRemote::DebugActiveProcessEx メソッド
デバッガーでのリモート コンピューター上のプロセスを起動します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pRemoteTarget`  
 [in]ポインター、 [ICorDebugRemoteTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)します。 このパラメーターを使用してをプロセスが実行されているコンピューターを特定します。  
  
 `id`  
 [in]デバッガーのアタッチ先のプロセスの ID。  
  
 `win32Attach`  
 [in]`true`デバッガーで、Win32 のデバッガー プロセスとして動作する必要があります、アンマネージのコールバックのディスパッチ場合それ以外の場合、`false`します。  
  
 `ppProcess`  
 [out]デバッガーのアタッチするプロセスを表す"ICorDebugProcess"オブジェクトのアドレスへのポインター。  
  
## <a name="return-value"></a>戻り値  
 S_OK  
 リモート コンピューター上のプロセスに正常に接続します。  
  
 E_FAIL (またはその他の E_ リターン コード)  
 リモート コンピューター上のプロセスにアタッチできません。  
  
## <a name="remarks"></a>Remarks  
 Silverlight では、混合モード デバッグはサポートされていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 4.5、4、3.5 SP1  
  
## <a name="see-also"></a>関連項目

- [ICorDebugRemote インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)
- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
