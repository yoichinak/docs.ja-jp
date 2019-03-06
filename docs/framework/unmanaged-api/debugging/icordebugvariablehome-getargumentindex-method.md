---
title: ICorDebugVariableHome::GetArgumentIndex メソッド
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2457dff3063e47f1fb9d040caac1bc08441e1739
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366830"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a>ICorDebugVariableHome::GetArgumentIndex メソッド

関数の引数のインデックスを取得します。

## <a name="syntax"></a>構文

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a>パラメーター

`pArgumentIndex`\
[out]引数のインデックスへのポインター。

## <a name="return-value"></a>戻り値

メソッドは、次の値を返します。

|[値]|説明|
|-----------|-----------------|
|`S_OK`|メソッドの呼び出しには、有効な引数のインデックスが返されます。|
|`E_FAIL`|現在[ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)インスタンスがローカル変数を表します。|

## <a name="remarks"></a>Remarks

この引数のメタデータを取得する引数のインデックスを使用できます。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** CorDebug.idl、CorDebug.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]

## <a name="see-also"></a>関連項目

- [ICorDebugVariableHome インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
