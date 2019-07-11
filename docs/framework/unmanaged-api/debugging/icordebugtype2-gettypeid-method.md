---
title: Icordebugtype 2::gettypeid メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3098911bab2878876b93ee1ce23d9794d7e6cdbd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772471"
---
# <a name="icordebugtype2gettypeid-method"></a>Icordebugtype 2::gettypeid メソッド
取得、 [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)この種類。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `id`  
 [out]ポインター、 [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)この icordebugtype します。  
  
## <a name="return-value"></a>戻り値  
 戻り値は、成功の場合は `S_OK` で、失敗の場合は `HRESULT` コードです。 `HRESULT`コードには、次が含まれます。  
  
|リターン コード|説明|  
|-----------------|-----------------|  
|`S_OK`|メソッドが成功しました。 メソッドは、有効な取得が[COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)します。|  
|`CORDBG_E_CLASS_NOT_LOADED`|型が読み込まれていません。|  
|`CORDBG_E_UNSUPPORTED`|型がサポートされていません。|  
  
## <a name="remarks"></a>Remarks  
 このメソッドでは、マッピングを提供することがありますいないに読み込まれている、実行時に、型を表す、ICorDebugType から、 [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)ランタイムに読み込まれた型を識別する非透過的なとして機能する処理です。  
  
 ときに、ICorDebugType を表す型がまだ読み込まれていますが、このメソッドが戻る`CORDBG_E_CLASS_NOT_LOADED`します。  返すかどうか、型はサポートされていません、`CORDBG_E_UNSUPPORTED`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugType2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
