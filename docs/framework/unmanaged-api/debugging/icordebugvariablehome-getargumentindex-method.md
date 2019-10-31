---
title: 'いい変数 Home:: GetArgumentIndex メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
ms.openlocfilehash: 86b2815c6f95c674c49bba7455e8497192bd8bac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125153"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a>いい変数 Home:: GetArgumentIndex メソッド

関数の引数のインデックスを取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a>パラメーター

`pArgumentIndex`\
入出力引数インデックスへのポインター。

## <a name="return-value"></a>戻り値

メソッドは、次の値を返します。

|[値]|説明|
|-----------|-----------------|
|`S_OK`|メソッド呼び出しによって有効な引数インデックスが返されました。|
|`E_FAIL`|現在の[ページ](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)は、ローカル変数を表します。|

## <a name="remarks"></a>Remarks

引数インデックスは、この引数のメタデータを取得するために使用できます。

## <a name="requirements"></a>［要件］

**:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。

**ヘッダー:** CorDebug.idl、CorDebug.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]

## <a name="see-also"></a>関連項目

- [ICorDebugVariableHome インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
