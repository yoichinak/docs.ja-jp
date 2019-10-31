---
title: ICorDebugType::GetFirstTypeParameter メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
ms.openlocfilehash: 4dbc042143e68dc962eb21b2bf741cbaefc1977e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122350"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a>ICorDebugType::GetFirstTypeParameter メソッド
この `ICorDebugType`によって表される型の最初の <xref:System.Type> パラメーターを表す、の型へのインターフェイスポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `value`  
 入出力最初のパラメーターを表す `ICorDebugType` オブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 型に関する追加情報には、最大で1つの型パラメーターが含まれている場合に、`GetFirstTypeParameter` を呼び出すことができます。 具体的には、型が ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF、または ELEMENT_TYPE_PTR である場合に使用できます。これは、[型:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)メソッドによって示されます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
