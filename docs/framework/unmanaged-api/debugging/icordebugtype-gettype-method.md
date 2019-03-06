---
title: ICorDebugType::GetType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f6b36c524921a4fecf8bc5ddcbace62af6450b6d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492427"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType メソッド
共通言語ランタイム (CLR) のネイティブな型を記述する CorElementType 値を取得します<xref:System.Type>この ICorDebugType によって表されます。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ty`  
 [out]値へのポインター、 `CorElementType` CLR を示す列挙体<xref:System.Type>この`ICorDebugType`を表します。  
  
## <a name="remarks"></a>Remarks  
 場合の値`ty`ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE のいずれかが、 [icordebugtype::getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)メソッドがジェネリック型のインスタンス化されていない型を取得するということがあります。 それ以外の場合、呼び出さない`ICorDebugType::GetClass`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
