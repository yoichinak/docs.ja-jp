---
title: ICorDebugHeapValue::IsValid メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
ms.openlocfilehash: 7edf0065fa7eb39dada167a682f2b634a438f1f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138396"
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid メソッド
この値によって表されるオブジェクトが有効かどうかを示す値を取得します。  
  
 このメソッドは .NET Framework バージョン2.0 では非推奨とされました。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pbValid`  
 入出力ヒープ上のこの値が有効かどうかを示すブール値へのポインター。  
  
## <a name="remarks"></a>Remarks  
 値は、ガベージコレクターによって回収されている場合は無効です。  
  
 このメソッドの使用は非推奨とされました。 .NET Framework 2.0 では、すべての値は、"の値は無効になります。 [" が呼び出されるまで、](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)すべての値が有効になります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
