---
title: ICorDebugHeapEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: 1beb69bfaad9acb9c269ad8becb81bea64edb6a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138470"
---
# <a name="icordebugheapenumnext-method"></a>ICorDebugHeapEnum::Next メソッド
マネージヒープ上のオブジェクトに関する情報を格納している、指定した数の[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)インスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 celt  
 [in] 取得するオブジェクトの数。  
  
 オブジェクト  
 入出力ポインターの配列。各ポインターは、マネージヒープ上のオブジェクトに関する情報を提供する[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)オブジェクトを指します。  
  
 pceltFetched  
 入出力`objects`に実際に返された[COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md)オブジェクトの数へのポインター。 `celt` が 1 の場合、この値は`null` になることがあります。  
  
## <a name="remarks"></a>Remarks  
 `COR_HEAPOBJECT.type` フィールドは、入れ子になった参照カウントの COM インターフェイスの識別子です。 この参照は、`ICorDebugHeapEnum::Next` の呼び出し元によって解放される必要があります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugHeapEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
