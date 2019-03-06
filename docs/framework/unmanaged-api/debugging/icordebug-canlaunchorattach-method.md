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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c29859a54b89956e017f06b8eeb97a6171eabbb
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57476218"
---
# <a name="icordebugcanlaunchorattach-method"></a>ICorDebug::CanLaunchOrAttach メソッド
現在コンピューターとランタイムの構成のコンテキスト内で、新しいプロセスの起動または指定した既存のプロセスにアタッチを実行するかどうかを示す HRESULT を返します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwProcessId`  
 [in]既存のプロセスの ID。  
  
 `win32DebuggingEnabled`  
 [in]渡す`true`Win32 デバッグを有効にすると、起動する予定するかどうか、または Win32 デバッグを有効になっている。 それ以外でアタッチするには、渡す`false`します。  
  
## <a name="return-value"></a>戻り値  
 デバッグ サービスを確認する新しいプロセスの起動または特定のプロセスにアタッチする場合は S_OK が、現在のコンピューターとランタイムの構成に関する情報を指定できます。 HRESULT 値があります。  
  
-   S_OK  
  
-   CORDBG_E_DEBUGGING_NOT_POSSIBLE  
  
-   CORDBG_E_KERNEL_DEBUGGER_PRESENT  
  
-   CORDBG_E_KERNEL_DEBUGGER_ENABLED  
  
## <a name="remarks"></a>Remarks  
 このメソッドは、純粋な情報です。 インターフェイスは停止されませんを起動またはによって返される値に関係なく、プロセスにアタッチ`CanLaunchOrAttach`します。  
  
 デバッグを有効に Win32 を使用して起動する Win32 デバッグを有効にアタッチまたは渡す場合`true`の`win32DebuggingEnabled`します。 によって返される HRESULT`CanLaunchOrAttach`このオプションを使用する場合に異なる場合があります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
