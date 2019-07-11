---
title: CorDebugStateChange 列挙体
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 676489880cb30ca540cb78d70797dbf4eedf7395
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739584"
---
# <a name="cordebugstatechange-enumeration"></a>CorDebugStateChange 列挙体

プロセスへの変更に基づいて破棄が必要となった、キャッシュされたデータの量を示します。

## <a name="syntax"></a>構文

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a>メンバー

| メンバー            | 説明                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | プロセスはフォワード実行によって新しいメモリ状態に達しています。            |
| `FLUSH_ALL`       | プロセスのメモリは、以前とは異なる状態になっている場合があります。 |

## <a name="remarks"></a>Remarks

 メンバー、`CorDebugStateChange`デバッガーを呼び出すと、列挙型が、引数として指定された、`ProcessStateChanged`メソッドで[ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md)または[ICorDebugProcess6:。ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)

## <a name="requirements"></a>必要条件

 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

 **ヘッダー:** CorDebug.idl、CorDebug.h

 **ライブラリ:** CorGuids.lib

 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>関連項目

- [列挙型のデバッグ](debugging-enumerations.md)
- [デバッグ](index.md)
