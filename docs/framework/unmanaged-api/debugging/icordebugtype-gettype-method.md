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
ms.openlocfilehash: 7f3010cccc584288608b3f6ba95efbeb95f271fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132053"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType メソッド
このテキスト型で表される共通言語ランタイム (CLR) <xref:System.Type> のネイティブ型を記述する CorElementType 値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ty`  
 入出力この `ICorDebugType` が表す CLR <xref:System.Type> を示す `CorElementType` 列挙値へのポインター。  
  
## <a name="remarks"></a>Remarks  
 `ty` の値が ELEMENT_TYPE_CLASS または ELEMENT_TYPE_VALUETYPE の場合は、インスタンス型を取得するために、 [type:: GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md)メソッドを呼び出すことができます。それ以外の場合は、`ICorDebugType::GetClass`を呼び出さないでください。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
