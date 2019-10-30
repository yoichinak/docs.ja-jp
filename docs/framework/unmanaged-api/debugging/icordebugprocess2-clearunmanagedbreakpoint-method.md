---
title: ICorDebugProcess2::ClearUnmanagedBreakpoint メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.ClearUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::ClearUnmanagedBreakpoint
helpviewer_keywords:
- ClearUnmanagedBreakpoint method [.NET Framework debugging]
- ICorDebugProcess2::ClearUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 12ed0fff-7f0e-4d7a-bb70-b3376371f36c
topic_type:
- apiref
ms.openlocfilehash: 8377ead42c752d8ebe9813d9e00662b94339f8a3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137244"
---
# <a name="icordebugprocess2clearunmanagedbreakpoint-method"></a>ICorDebugProcess2::ClearUnmanagedBreakpoint メソッド
指定したアドレスに、以前に設定したブレークポイントを削除します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT ClearUnmanagedBreakpoint (  
    [in] CORDB_ADDRESS   address  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `address`  
 からブレークポイントが設定されたアドレスを示す `CORDB_ADDRESS` 値です。  
  
## <a name="remarks"></a>Remarks  
 指定されたブレークポイントは、以前の[ICorDebugProcess2:: SetUnmanagedBreakpoint](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-setunmanagedbreakpoint-method.md)の呼び出しによって以前に設定されていた可能性があります。  
  
 `ClearUnmanagedBreakpoint` メソッドは、デバッグ中のプロセスの実行中に呼び出すことができます。  
  
 デバッガーがマネージ専用モードでアタッチされている場合、または指定されたアドレスにブレークポイントが存在しない場合、`ClearUnmanagedBreakpoint` メソッドはエラーコードを返します。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
