---
title: メソッドを変更 :Pしました。
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: a6f36f5b86b4fa58ce2a4ef4aa23d527f797a5a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178626"
---
# <a name="icordebugprocess4processstatechanged-method"></a>メソッドを変更 :Pしました。

プロセス外のデバッガーがデバッグ先の実行を続行していることを ICorDebug パイプラインに通知します。

## <a name="syntax"></a>構文

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a>パラメーター

 `eChange`\
[in]プロセスの実行状態の変更を記述する[列挙体](cordebugstatechange-enumeration.md)のメンバー。

## <a name="remarks"></a>解説

指定されたメソッドはインターフェイスの`ICorDebugProcess4`一部であり、仮想メソッド テーブルの 4 番目のスロットに対応します。

## <a name="requirements"></a>必要条件

 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。

 **ヘッダー:** なし

 **ライブラリ:** なし

 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>関連項目

- [ICorDebugProcess4 インターフェイス](icordebugprocess4-interface.md)
- [デバッグ インターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
