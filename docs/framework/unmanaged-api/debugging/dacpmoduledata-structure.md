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
ms.openlocfilehash: 752d87c5f4a6b8d854a06be8962ee754cdd4622d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61965959"
---
# <a name="dacpmoduledata-structure"></a>DacpModuleData 構造体

トランスポートのバッファーをモジュールのランタイム情報を定義します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```
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
| `ilBase`  | 読み込まれたイメージのアドレスの基本です。                                 |
| `payLoad` | その他のモジュールについては、ランタイムによって使用されるペイロードのバッファー。 |

## <a name="remarks"></a>Remarks

この構造は、ランタイム内に収めるし、任意のヘッダーまたはライブラリ ファイルでは公開されません。 これを使用するには、上で指定した構造を定義します。

## <a name="requirements"></a>必要条件
**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
**ヘッダー:** なし  
**ライブラリ:** なし  
**.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
