---
title: CLRDataSourceType 列挙型
ms.date: 01/16/2019
api.name:
- CLRDataSourceType Enumeration
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- CLRDataSourceType Enumeration
helpviewer.keywords:
- CLRDataSourceType Enumeration [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 7ace405e2624f15b1cdb6d383222ae87c93289bb
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274092"
---
# <a name="clrdatasourcetype-enumeration"></a>CLRDataSourceType 列挙型

CLRDATA_IL_ADDRESS_MAP 構造体によって使用される値を提供します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
typedef enum
{
    CLRDATA_SOURCE_TYPE_INVALID        = 0x00, // To indicate that nothing else applies
} CLRDataSourceType;
```

## <a name="members"></a>メンバー

| メンバー                        | 説明                           |
| ----------------------------- | ------------------------------------- |
| `CLRDATA_SOURCE_TYPE_INVALID` | 他に何も適用されないことを示すには |

## <a name="remarks"></a>コメント

この列挙体はランタイム内に存在し、ヘッダーまたはライブラリファイルを介して公開されることはありません。 これを使用するには、コードで前述したように、列挙型を定義します。 これは、「 `CLRDATA_ENUM` [Common Data Types](../common-data-types-unmanaged-api-reference.md)」で説明されているように、という別名でもあります。

## <a name="requirements"></a>要件

**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
**ヘッダー:** なし  
**ライブラリ**なし  
**.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [列挙型のデバッグ](debugging-enumerations.md)
