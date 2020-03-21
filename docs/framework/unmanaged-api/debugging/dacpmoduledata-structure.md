---
title: DacpModuleData 構造体
ms.date: 02/01/2019
api.name:
- DacpModuleData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpModuleData Structure
helpviewer.keywords:
- DacpModuleData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: c24bdce64eb7e208bf3830940d7beab1ebf92e78
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179185"
---
# <a name="dacpmoduledata-structure"></a>DacpModuleData 構造体

モジュールの実行時情報のトランスポート バッファーを定義します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
struct DacpModuleData
{
    CLRDATA_ADDRESS Address;
    CLRDATA_ADDRESS File;
    CLRDATA_ADDRESS  ilBase;
    char payLoad[132];
};
```

## <a name="members"></a>メンバー

| メンバー    | 説明                                                             |
| --------- | ----------------------------------------------------------------------- |
| `Address` | モジュール オブジェクトのアドレス。                                           |
| `File`    | ポータブル実行可能 (PE) ファイルへのポインター。                       |
| `ilBase`  | 読み込まれたイメージのベースのアドレス。                                 |
| `payLoad` | ランタイムで使用される追加のモジュール情報のペイロード バッファー。 |

## <a name="remarks"></a>解説

この構造体はランタイム内に存在し、ヘッダーやライブラリ ファイルを通じて公開されません。 使用するには、上記で指定した構造を定義します。

## <a name="requirements"></a>必要条件
**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
**ヘッダー:** なし  
**ライブラリ:** なし  
**.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [デバッグ構造体](debugging-structures.md)
