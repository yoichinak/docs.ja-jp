---
title: 'IXCLRDataMethodInstance:: GetRepresentativeEntryAddress メソッド'
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: d9f9e16d243c0f3b45ac24776caea5bb9c32dcc1
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395748"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a>IXCLRDataMethodInstance:: GetRepresentativeEntryAddress メソッド

メソッドに対して使用可能なすべてのエントリポイントのネイティブコンパイルを行うための最も代表的なエントリポイントアドレスを取得します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a>パラメーター

`addr`\
入出力メソッドの最も代表的なネイティブエントリポイントのアドレス。

## <a name="remarks"></a>解説

指定されたメソッドは[ `IXCLRDataMethodInstance` インターフェイス](ixclrdatamethodinstance-interface.md)の一部であり、仮想メソッドテーブルの20番目のスロットに対応します。

## <a name="requirements"></a>要件

**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
**ヘッダー:** 存在  
**ライブラリ:** 存在  
**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [IXCLRDataMethodInstance インターフェイス](ixclrdatamethodinstance-interface.md)
