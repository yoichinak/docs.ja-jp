---
title: ICorDebugArrayValue::GetElement メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElement
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElement
helpviewer_keywords:
- GetElement method [.NET Framework debugging]
- ICorDebugArrayValue::GetElement method [.NET Framework debugging]
ms.assetid: 7ac3cba5-c282-402e-b7ef-b46634f5176b
topic_type:
- apiref
ms.openlocfilehash: adcb7b5a27f3b8c63dbbb660a23b5c891f84ac46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179010"
---
# <a name="icordebugarrayvaluegetelement-method"></a>ICorDebugArrayValue::GetElement メソッド
指定された配列要素の値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetElement (  
    [in]  ULONG32          cdim,  
    [in, size_is(cdim), length_is(cdim)]
         ULONG32           indices[],  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `cdim`  
 [in]この`ICorDebugArrayValue`オブジェクトの次元数。  
  
 この値は、オブジェクトの次元数`indices`と同じサイズであるため、配列の`ICorDebugArrayValue`サイズでもあります。  
  
 `indices`  
 [in]インデックス値の配列で、各配列はオブジェクトの次元内の位置を指定`ICorDebugArrayValue`します。  
  
 この値は null にできません。  
  
 `ppValue`  
 [アウト]指定した要素の値を表すオブジェクトのアドレスへのポインター。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
