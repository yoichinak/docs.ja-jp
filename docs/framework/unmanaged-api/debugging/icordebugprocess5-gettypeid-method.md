---
title: ICorDebugProcess5::GetTypeID メソッド
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugProcess5.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeID
helpviewer_keywords:
- ICorDebugProcess5::GetTypeID method [.NET Framework debugging]
- GetTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 47dbaea4-8857-462e-93ba-fff880fc9e50
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f58e4213959ca1cd6e65bc809a9ad964bebc31ae
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494793"
---
# <a name="icordebugprocess5gettypeid-method"></a>ICorDebugProcess5::GetTypeID メソッド
変換するオブジェクトのアドレスを[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)識別子。  
  
## <a name="syntax"></a>構文  
  
```cpp
HRESULT GetTypeID(  
    [in] CORDB_ADDRESS obj,  
    [out] COR_TYPEID *pId  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `obj`  
 [in]オブジェクトのアドレス。  
  
 `pId`  
 ポインター、 [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)オブジェクトを識別する値。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorDebugProcess5 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
