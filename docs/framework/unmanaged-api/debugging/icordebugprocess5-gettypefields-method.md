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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7c2725c62105e92996bb2d8e79e8ff504904e9c7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107953"
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields メソッド
型に属するフィールドについてを説明します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `id`  
 [in]フィールド情報を取得する型の識別子です。  
  
 `celt`  
 [in]数[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)フィールド情報を取得するオブジェクト。  
  
 `fields`  
 [out]配列の[COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)型に属するフィールドに関する情報を提供するオブジェクト。  
  
 `pceltNeeded`  
 [out]数へのポインター [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md)に含まれるオブジェクト`fields`します。  
  
## <a name="remarks"></a>Remarks  
 `celt`フィールドがフィールドの情報を設定するメソッドを使用して数を指定するパラメーター`fields`の値に対応する必要があります、`COR_TYPE_LAYOUT::numFields`フィールド。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugProcess5 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
