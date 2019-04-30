---
title: ICorDebugManagedCallback::Break メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bab20301c5413f8bbe95d44b87e06d3b3870c9e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988367"
---
# <a name="icordebugmanagedcallbackbreak-method"></a>ICorDebugManagedCallback::Break メソッド

デバッガーに通知時に、<xref:System.Reflection.Emit.OpCodes.Break>コード ストリームに命令を実行します。

## <a name="syntax"></a>構文

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a>パラメーター

`pAppDomain`\
[in]中断命令を含むアプリケーション ドメインを表す ICorDebugAppDomain オブジェクトへのポインター。

`thread`\
[in]中断命令を含むスレッドを表す ICorDebugThread オブジェクトへのポインター。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** CorDebug.idl、CorDebug.h

**ライブラリ:** CorGuids.lib

**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>関連項目

- [ICorDebugManagedCallback インターフェイス](icordebugmanagedcallback-interface.md)