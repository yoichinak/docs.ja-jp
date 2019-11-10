---
title: ICorDebugValue::GetType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
ms.openlocfilehash: 284a74823b01305f8c6e025f70bb9209c8607b7b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137072"
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType メソッド
この "ICorDebugValue" オブジェクトのプリミティブ型を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pType`  
 入出力値の型を示す "CorElementType" 列挙値へのポインター。  
  
## <a name="remarks"></a>Remarks  
 オブジェクトが複雑な実行時の型である場合、その型は、`ICorDebugValue` インターフェイスの適切なサブクラスを通じて検査される可能性があります。 たとえば、`ICorDebugValue`から継承する "" は、複合型を表します。  
  
 `GetType` とには、それぞれ値の型に関する情報が返され[ます。](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-getclass-method.md) これらはどちらも、ジェネリック対応[ICorDebugValue2:: GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)メソッドに置き換えられています。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
