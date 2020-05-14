---
title: 'IXCLRDataProcess:: EndEnumMethodInstancesByAddress メソッド'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 04ce8f44b0c9f532951666de7bfb9de475c14746
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395251"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a>IXCLRDataProcess:: EndEnumMethodInstancesByAddress メソッド

インスタンスの列挙中に使用される内部反復子によって使用されるリソースを解放します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a>パラメーター

`handle`\
入出力メソッドインスタンスを列挙するハンドル。

## <a name="remarks"></a>解説

指定されたメソッドはインターフェイスの一部で `IXCLRDataProcess` あり、仮想メソッドテーブルの30スロットに対応します。

## <a name="requirements"></a>要件

**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
**ヘッダー:** 存在  
**ライブラリ:** 存在  
**.NET Framework のバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [CLRDataSourceType 列挙型](clrdatasourcetype-enumeration.md)
- [デバッグ](index.md)
- [IXCLRDataProcess インターフェイス](ixclrdataprocess-interface.md)
