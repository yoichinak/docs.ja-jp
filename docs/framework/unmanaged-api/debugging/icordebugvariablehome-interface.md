---
title: ICorDebugVariableHome インターフェイス
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugVariableHome
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome
helpviewer_keywords:
- ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 76f2bf3b-759f-4eed-bce7-119415b25915
topic_type:
- apiref
ms.openlocfilehash: 306a07450b8ae6d29875ca0cc4679390472e4d1d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121039"
---
# <a name="icordebugvariablehome-interface"></a>ICorDebugVariableHome インターフェイス
関数のローカル変数または引数を表します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetArgumentIndex メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getargumentindex-method.md)|関数の引数のインデックスを取得します。|  
|[GetCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getcode-method.md)|この `ICorDebugVariableHome` オブジェクトを含む "コード" インスタンスを取得します。|  
|[GetLiveRange メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getliverange-method.md)|この変数がライブであるネイティブ範囲を取得します。|  
|[GetLocationType メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md)|変数のネイティブな場所の型を取得します。|  
|[GetOffset メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getoffset-method.md)|変数の基本レジスタからのオフセットを取得します。|  
|[GetRegister メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getregister-method.md)|`VLT_REGISTER`の場所の種類を持つ変数と、場所の種類が `VLT_REGISTER_RELATIVE`の変数の基本レジスタを含むレジスタを取得します。|  
|[GetSlotIndex メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getslotindex-method.md)|ローカル変数のマネージドスロットインデックスを取得します。|  
  
## <a name="example"></a>例  
 次のコード片では、`pCode4`という名前の[ICorDebugCode4](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)オブジェクトを使用します。  
  
```cpp  
ICorDebugCode4 *pCode4 = NULL;  
pCode->QueryInterface(IID_ICorDebugCode4, &pCode4);  
  
ICorDebugVariableEnum *pVarLocEnum = NULL;  
pCode4->EnumerateVariableHomes(&pVarLocEnum);  
  
// retrieve local variables and arguments  
ULONG celt = 0;  
pVarLocEnum->GetCount(&celt);  
ICorDebugVariableHome **homes = new ICorDebugVariableHome *[celt];  
ULONG celtFetched = 0;  
pVarLocEnum->Next(celt, homes, &celtFetched);  
  
for (int i = 0; i < celtFetched; i++)  
{  
    VariableLocationType locType = VLT_INVALID;  
    homes[i].GetLocationType(&locType);  
    switch (locType)  
    {  
    case VLT_REGISTER:  
        CorDebugRegister register = 0;  
        locals[i].GetRegister(&register);  
        // now we know which register it is in  
        break;  
    case VLT_REGISTER_RELATIVE:  
        CorDebugRegister baseRegister = 0;  
        LONG offset = 0;  
        locals[i].GetRegister(&register);  
        locals[i].GetOffset(&offset);  
        // now we know the register-relative offset  
        break;  
    case VLT_INVALID:  
        // handle case where we can't access the location  
        break;  
    }  
}  
```  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [ICorDebugVariableHomeEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
