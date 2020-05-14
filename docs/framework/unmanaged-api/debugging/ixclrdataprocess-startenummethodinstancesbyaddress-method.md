---
title: 'IXCLRDataProcess:: StartEnumMethodInstancesByAddress メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: e28fa73300e147ac07a2d325fbf517480bb73797
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2020
ms.locfileid: "83394947"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a>IXCLRDataProcess:: StartEnumMethodInstancesByAddress メソッド

指定されたアドレスから開始するのメソッドインスタンスを列挙するハンドルを提供し `AppDomain` ます。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a>パラメーター

`address`\
から最初のメソッドインスタンスのアドレス。

`appDomain`\
からメソッドインスタンスの AppDomain。

`handle`\
入出力メソッドインスタンスを列挙するハンドル。

## <a name="remarks"></a>解説

指定されたメソッドはインターフェイスの一部で `IXCLRDataProcess` あり、仮想メソッドテーブルの28番目のスロットに対応します。

## <a name="requirements"></a>要件

**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
**ヘッダー:** 存在  
**ライブラリ:** 存在  
**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [CLRDataSourceType 列挙型](clrdatasourcetype-enumeration.md)
- [デバッグ](index.md)
- [IXCLRDataProcess インターフェイス](ixclrdataprocess-interface.md)
