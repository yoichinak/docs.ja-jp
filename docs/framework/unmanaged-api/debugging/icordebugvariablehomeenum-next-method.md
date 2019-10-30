---
title: は、次のメソッドを実行します。
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
ms.openlocfilehash: 9c2c16789fb61099c9b7c58154810739d225af1f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121922"
---
# <a name="icordebugvariablehomeenumnext-method"></a>は、次のメソッドを実行します。
関数内のローカル変数および引数に関する情報を格納している指定された数の表示変数[home](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)インスタンスを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `celt`  
 [in] 取得するオブジェクトの数。  
  
 `homes`  
 ポインターの配列。各ポインターは、関数のローカル変数または引数に関する情報を提供[する、の各オブジェクトを](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)参照します。  
  
 `pceltFetched`  
 入出力実際にオブジェクトで返されたインスタンスの数。  
  
## <a name="return-value"></a>戻り値  
 メソッドは、次の値を返します。  
  
|HRESULT|説明|  
|-------------|-----------------|  
|`S_OK`|メソッドは正常に完了しました。|  
|`S_FALSE`|`pceltFetched`に反映された実際に取得されたインスタンスの数が、要求されたインスタンスの数より少なくなっています。|  
  
## <a name="remarks"></a>Remarks  
 [次](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md)のメソッドは、列挙子の現在位置から最大 `celt` オブジェクトを取得します。 メソッドから制御が戻ったときに、`pceltFetched` 取得したオブジェクトの実際の数が含まれます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugVariableHomeEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
- [ICorDebugVariableHome インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
