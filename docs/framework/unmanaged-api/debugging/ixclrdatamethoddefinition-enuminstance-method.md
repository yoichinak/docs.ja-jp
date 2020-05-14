---
title: 'IXCLRDataMethodDefinition:: EnumInstance メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 72560de9777b2d826418e63b4a4fcccf1e4fa8b9
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396480"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a>IXCLRDataMethodDefinition:: EnumInstance メソッド

このメソッド定義のインスタンスを列挙します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a>パラメーター

`handle`\
[入力、出力]インスタンスを列挙するハンドル。

`instance`\
入出力列挙されたインスタンス。

## <a name="remarks"></a>解説

指定されたメソッドはインターフェイスの一部で `IXCLRDataMethodDefinition` あり、仮想メソッドテーブルの6番目のスロットに対応します。

## <a name="requirements"></a>要件

**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
**ヘッダー:** 存在  
**ライブラリ:** 存在  
**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [CLRDataSourceType 列挙型](clrdatasourcetype-enumeration.md)
- [デバッグ](index.md)
- [IXCLRDataMethodDefinition インターフェイス](ixclrdatamethoddefinition-interface.md)
- [IXCLRDataMethodInstance インターフェイス](ixclrdatamethodinstance-interface.md)
