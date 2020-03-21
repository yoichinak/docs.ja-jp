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
ms.openlocfilehash: 29006eba3d3a523fd24a461207ab12222a639782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178588"
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields メソッド
型に属するフィールドに関する情報を提供します。  
  
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
 [in]フィールド情報を取得する型の識別子。  
  
 `celt`  
 [in]フィールド情報を取得する[COR_FIELD](cor-field-structure.md)オブジェクトの数。  
  
 `fields`  
 [アウト]型に属するフィールドに関する情報を提供する[COR_FIELD](cor-field-structure.md)オブジェクトの配列。  
  
 `pceltNeeded`  
 [アウト]に含まれる[COR_FIELD](cor-field-structure.md)オブジェクトの数へのポインター `fields`。  
  
## <a name="remarks"></a>解説  
 この`celt`パラメーターは、メソッドがフィールド情報を設定`fields`するために使用するフィールドの数を`COR_TYPE_LAYOUT::numFields`フィールドの値に対応させる必要があります。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess5 インターフェイス](icordebugprocess5-interface.md)
- [デバッグ インターフェイス](debugging-interfaces.md)
