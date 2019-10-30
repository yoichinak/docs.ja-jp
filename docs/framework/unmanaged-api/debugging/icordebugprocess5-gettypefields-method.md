---
title: ICorDebugProcess5::GetTypeFields メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
ms.openlocfilehash: 0045285a3da22f468c2426bb3b9c4ae7e3e1d7c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132667"
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields メソッド
型に属しているフィールドに関する情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `id`  
 からフィールド情報を取得する型の識別子。  
  
 `celt`  
 からフィールド情報を取得する[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)オブジェクトの数。  
  
 `fields`  
 入出力型に属するフィールドに関する情報を提供する[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)オブジェクトの配列。  
  
 `pceltNeeded`  
 入出力`fields`に含まれている[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)オブジェクトの数へのポインター。  
  
## <a name="remarks"></a>Remarks  
 `celt` パラメーターは、メソッドが `fields`を設定するために使用するフィールド情報を持つフィールドの数を指定します。 `COR_TYPE_LAYOUT::numFields` フィールドの値に対応する必要があります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess5 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
