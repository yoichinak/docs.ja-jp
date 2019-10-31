---
title: ICorDebug::CanLaunchOrAttach メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
ms.openlocfilehash: 805f9a5d1f2590a06bfa929c152bdfd13900531a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134282"
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach メソッド
現在のコンピューターおよびランタイム構成のコンテキスト内で、新しいプロセスを起動するか、指定した既存のプロセスにアタッチするかを示す HRESULT を返します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwProcessId`  
 から既存のプロセスの ID。  
  
 `win32DebuggingEnabled`  
 からWin32 デバッグを有効にして起動する場合、または Win32 デバッグを有効にしてアタッチする場合は、`true` を渡します。それ以外の場合は、`false`を渡します。  
  
## <a name="return-value"></a>戻り値  
 現在のコンピューターと実行時の構成に関する情報を指定して、デバッグサービスが新しいプロセスを起動するか、特定のプロセスにアタッチするかを決定する場合は S_OK。 使用できる HRESULT 値は次のとおりです。  
  
- S_OK  
  
- CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
- CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
- CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Remarks  
 このメソッドは純粋な情報です。 インターフェイスでは、`CanLaunchOrAttach`によって返される値に関係なく、プロセスの起動やアタッチが停止されることはありません。  
  
 Win32 デバッグが有効になっている状態で起動する場合、または Win32 デバッグを有効にしてアタッチする場合は、`win32DebuggingEnabled`の `true` を渡します。 このオプションを使用すると、`CanLaunchOrAttach` によって返される HRESULT は異なる場合があります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
