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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3031cf2d9509f94b50c386b44e6d9e5d9ee5509c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768231"
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a>ICorDebugType::GetFirstTypeParameter メソッド
1 つ目を表す、ICorDebugType へインターフェイス ポインターを取得<xref:System.Type>これによって表される型のパラメーター`ICorDebugType`します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `value`  
 [out]アドレスへのポインター、`ICorDebugType`最初のパラメーターを表すオブジェクト。  
  
## <a name="remarks"></a>Remarks  
 `GetFirstTypeParameter` できる場合に呼び出される場所の種類に関する追加情報は、最大で 1 つの型パラメーター。 具体的には、使用できます、型が ELEMENT_TYPE_ARRAY、ELEMENT_TYPE_SZARRAY、ELEMENT_TYPE_BYREF、または ELEMENT_TYPE_PTR 場合、によって示される、 [icordebugtype::gettype](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
