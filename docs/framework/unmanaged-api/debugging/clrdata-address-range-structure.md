---
title: CLRDATA_ADDRESS_RANGE 構造体
ms.date: 01/16/2019
api.name:
- CLRDATA_ADDRESS_RANGE Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDATA_ADDRESS_RANGE Structure
helpviewer.keywords:
- CLRDATA_ADDRESS_RANGE Structure [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 8eb841b4c4f06a3932805ae6222bdd693def5ea0
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274310"
---
# <a name="clrdata_address_range-structure"></a>CLRDATA_ADDRESS_RANGE 構造体

アドレス範囲を定義します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
typedef struct
{
    CLRDATA_ADDRESS startAddress;
    CLRDATA_ADDRESS endAddress;
} CLRDATA_ADDRESS_RANGE;
```

## <a name="members"></a>メンバー

| メンバー         | 説明                     |
| -------------- | ------------------------------- |
| `startAddress` | 範囲の開始アドレス。 |
| `endAddress`   | 範囲の終了アドレス。   |

## <a name="remarks"></a>コメント

この構造体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。 これを使用するに`CLRDATA_ADDRESS`は、上で指定したように構造体を定義します。は、64ビットの符号なし整数です。

## <a name="requirements"></a>要件

**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
**ヘッダー:** なし  
**ライブラリ**なし  
**.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [デバッグ構造体](debugging-structures.md)
