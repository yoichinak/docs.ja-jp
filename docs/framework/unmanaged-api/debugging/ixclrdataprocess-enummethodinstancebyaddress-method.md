---
title: メソッドをメソッドとして使用します。
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: afc5fc377dd45d5e8d4d2d7b3385ca0524df69e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176657"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a>メソッドをメソッドとして使用します。

アドレス オフセットから開始するこのプロセスのメソッド インスタンスを列挙します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a>パラメーター

`handle`\
[in]メソッド インスタンスを列挙するためのハンドル。

`mod`\
[アウト]列挙されたメソッド のインスタンス。

## <a name="remarks"></a>解説

提供されたメソッドはインターフェイスの`IXCLRDataProcess`一部であり、仮想メソッド テーブルの 28 番目のスロットに対応します。

## <a name="requirements"></a>必要条件

**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。
**ヘッダー:** なし**ライブラリ:** なし **.NET フレームワークのバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>関連項目

- [列挙型](clrdatasourcetype-enumeration.md)
- [デバッグ](index.md)
- [IXCLRDataProcess インターフェイス](ixclrdataprocess-interface.md)
