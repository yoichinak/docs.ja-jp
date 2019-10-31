---
title: ICorDebugGuidToTypeEnum::Next メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugGuidToTypeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGuidToTypeEnum::Next
helpviewer_keywords:
- ICorDebugGuidToTypeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugGuidToTypeEnum interface [.NET Framework debugging]
ms.assetid: c9937666-8e18-484d-9fe0-b9ac95199530
topic_type:
- apiref
ms.openlocfilehash: f6f190cd5b2f208df5a4ed88b650af671f2e6c5c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138513"
---
# <a name="icordebugguidtotypeenumnext-method"></a>ICorDebugGuidToTypeEnum::Next メソッド
Guid を型情報にマップする、指定された数の[Cordebugguidtotypemapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)インスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched] CorDebugGuidToTypeMapping values[  ],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `celt`  
 から取得する GUID から型へのマッピングオブジェクトの数。  
  
 `values`  
 入出力ポインターの配列。それぞれのポインターが[Cordebugguidtotypemapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)オブジェクトを指します。これは、Windows ランタイム GUID を対応するテキストオブジェクトにマップします。  
  
 `pceltFetched`  
 入出力実際に `values`で返された[Cordebugguidtotypemapping](../../../../docs/framework/unmanaged-api/debugging/cordebugguidtotypemapping-structure.md)オブジェクトの数へのポインター。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>［要件］  
 **プラットフォーム:** Windows ランタイム  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugGuidToTypeEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
