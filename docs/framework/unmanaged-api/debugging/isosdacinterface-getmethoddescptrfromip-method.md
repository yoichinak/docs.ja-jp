---
title: 'ISOSDacInterface:: GetMethodDescPtrFromIP メソッド'
ms.date: 02/01/2019
api.name:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method
helpviewer.keywords:
- ISOSDacInterface::GetMethodDescPtrFromIP Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 0c8d91c11205e06857b4a6e7edfedcd087270d00
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396937"
---
# <a name="isosdacinterfacegetmethoddescptrfromip-method"></a>ISOSDacInterface:: GetMethodDescPtrFromIP メソッド

指定されたネイティブ命令アドレスを格納しているメソッドに対応する MethodDesc のポインターを取得します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT GetMethodDescPtrFromIP(
    CLRDATA_ADDRESS ip,
    CLRDATA_ADDRESS * ppMD
);
```

## <a name="parameters"></a>パラメーター

`ip`\
から実行時のメソッド内のアドレス。

`ppMD`\
入出力`MethodDesc`特定のメソッドののアドレス。

## <a name="remarks"></a>解説

指定されたメソッドは[ `ISOSDacInterface` インターフェイス](isosdacinterface-interface.md)の一部であり、仮想メソッドテーブルの22スロットに対応します。

## <a name="requirements"></a>要件

**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
**ヘッダー:** 存在  
**ライブラリ:** 存在  
**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [ISOSDacInterface インターフェイス](isosdacinterface-interface.md)
