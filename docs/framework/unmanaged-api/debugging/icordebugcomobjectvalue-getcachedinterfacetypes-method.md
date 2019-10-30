---
title: ICorDebugComObjectValue::GetCachedInterfaceTypes メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfaceTypes
helpviewer_keywords:
- GetCachedInterface method, ICorDebugComObjectValue interface [.NET Framework debugging]
- ICorDebugComObjectValue::GetCachedInterface method [.NET Framework debugging]
ms.assetid: d492284f-d3c5-4614-adb8-d718d5042500
topic_type:
- apiref
ms.openlocfilehash: 199f58456e64ccf7ef771d42d5c7d64b189cb670
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125493"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacetypes-method"></a>ICorDebugComObjectValue::GetCachedInterfaceTypes メソッド
現在のオブジェクトがキャストされた、またはとして使用されたインターフェイス型の列挙子を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetCachedInterfaceTypes(  
    [in] BOOL bIInspectableOnly,  
    [out] ICorDebugTypeEnum **ppInterfacesEnum);  
```  
  
## <a name="parameters"></a>パラメーター  
 `bIInspectableOnly`  
 からメソッドが、ランタイム呼び出し可能ラッパー (RCW) によってキャッシュされた Windows ランタイムインターフェイス (`IInspectable` インターフェイス) またはすべての COM インターフェイスだけを返すかどうかを示す値。  
  
 `ppInterfacesEnum`  
 入出力`bIInspectableOnly`に従ってフィルター処理された、キャッシュされたインターフェイスの種類を表す、の型のオブジェクトへのアクセスを提供する、の型のオブジェクトへのアクセスを提供する、の型のアドレスへのポインター。  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorDebugComObjectValue のインターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)
- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
