---
title: 'ICorDebugCode4:: EnumerateVariableHomes メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugCode4.EnumerateVariableHomes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4::EnumerateVariableHomes
helpviewer_keywords:
- EnumerateVariableHomes method [.NET Framework debugging]
- ICorDebugCode4::EnumerateVariableHomes method [.NET Framework debugging]
ms.assetid: 802c01ff-8b80-4733-b6dd-03ab6ff7fa11
topic_type:
- apiref
ms.openlocfilehash: 850cbd2367dddd9f46375817e271cb8e7183cf64
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121097"
---
# <a name="icordebugcode4enumeratevariablehomes-method"></a>ICorDebugCode4:: EnumerateVariableHomes メソッド
関数のローカル変数および引数に対する列挙子を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT EnumerateVariableHomes(  
    [out] ICorDebugVariableHomeEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppEnum`  
 関数内のローカル変数および引数の列挙子である、の[型](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)のオブジェクトのアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
 "ICorDebugEnum" インターフェイスから派生した標準列挙子で[ある、表示変数](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)[ホーム](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)オブジェクトを列挙できます。 コレクションには、同じスロットまたは引数インデックスに対して、関数内の異なるポイントに異なる[ホーム](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)オブジェクトが含まれている場合があります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugCode4 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
