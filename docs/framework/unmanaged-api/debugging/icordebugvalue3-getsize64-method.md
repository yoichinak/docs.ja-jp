---
title: ICorDebugValue3::GetSize64 メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValue3::GetSize64
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3::GetSize64
helpviewer_keywords:
- GetSize64 method, ICorDebugValue3 interface [.NET Framework debugging]
- ICorDebugValue3::GetSize64 method [.NET Framework debugging]
ms.assetid: fee56a29-3154-4192-958d-71da2ced3740
topic_type:
- apiref
ms.openlocfilehash: 72a1b6fdc40f3169500d8cf3b3028315106ecc69
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140234"
---
# <a name="icordebugvalue3getsize64-method"></a>ICorDebugValue3::GetSize64 メソッド
この[ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)オブジェクトのサイズ (バイト単位) を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSize64(  
    [out] ULONG64 *pSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 pSize  
 入出力このオブジェクトのサイズ (バイト単位) へのポインター。  
  
## <a name="remarks"></a>Remarks  
 この値の型が参照型の場合、このメソッドはオブジェクトのサイズではなく、ポインターのサイズを返します。  
  
 `ICorDebugValue3::GetSize` メソッドは、その出力パラメーターの型の[ICorDebugValue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)メソッドとは異なります。 [ICorDebugValue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-getsize-method.md)では、出力パラメーターは `ULONG32`です。`ICorDebugValue3::GetSize`では、`ULONG64`です。 これにより、 [ICorDebugValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)インターフェイスは、2gb を超える配列のサイズを報告できます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugValue3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
