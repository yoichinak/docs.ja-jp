---
title: ICorDebugValue::GetSize メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugValue interface [.NET Framework debugging]
- ICorDebugValue::GetSize method [.NET Framework debugging]
ms.assetid: 445a9ee3-e050-4f3a-931a-96b0efb00110
topic_type:
- apiref
ms.openlocfilehash: 3d6caa02333229bcd49f4c6ccf8b93265181a0b3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137093"
---
# <a name="icordebugvaluegetsize-method"></a>ICorDebugValue::GetSize メソッド
この "ICorDebugValue" オブジェクトのサイズ (バイト単位) を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetSize (  
    [out] ULONG32   *pSize  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pSize`  
 入出力この値オブジェクトのサイズ (バイト単位)。  
  
## <a name="remarks"></a>Remarks  
 値の型が参照型の場合、このメソッドはオブジェクトのサイズではなく、ポインターのサイズを返します。  
  
 `ICorDebugValue::GetSize` メソッドは、64ビットプラットフォームで 4 GB を超えるオブジェクトの `COR_E_OVERFLOW` を返します。 4 GB を超えるオブジェクトには、代わりに[ICorDebugValue3:: GetSize64](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)メソッドを使用してください。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetSize64 メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)
