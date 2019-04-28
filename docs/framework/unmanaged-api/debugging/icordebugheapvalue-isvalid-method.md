---
title: ICorDebugHeapValue::IsValid メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e1edb1d25a62a9a689c397339740e563d986c8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61700222"
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid メソッド
この ICorDebugHeapValue によって表されるオブジェクトが有効かどうかを示す値を取得します。  
  
 このメソッドは、.NET Framework version 2.0 で廃止されました。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pbValid`  
 [out]ヒープ上には、この値が有効かどうかを示すブール値へのポインター。  
  
## <a name="remarks"></a>Remarks  
 値は、ガベージ コレクターが解放された場合に有効ではありません。  
  
 このメソッドの使用は非推奨とされました。 すべての値の有効期限は、.NET Framework 2.0 で[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)であり、値は、検証は、呼び出されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
