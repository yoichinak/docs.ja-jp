---
title: ICorDebugProcess4 インターフェイス
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4
helpviewer_keywords:
- ICorDebugProcess4 interface [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 1bdc958f2516bcd7c2eb74312fbf478e6d49535a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948806"
---
# <a name="icordebugprocess4-interface"></a>ICorDebugProcess4 インターフェイス

プロセス実行の制御外のサポートを提供します。

## <a name="methods"></a>メソッド

| メソッド                                                                 | 説明                                                                                             |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| [ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) | デバッガーをプロセスの出力がデバッグ対象の実行を続行は ICorDebug パイプラインに通知します。 |

## <a name="remarks"></a>Remarks

このインターフェイスは、ランタイム内に収めるを任意のヘッダーまたはライブラリ ファイルを通じて公開されていません。 ただし、これは COM インターフェイスから派生した`IUnknown`GUID を持つ`E930C679-78AF-4953-8AB7-B0AABF0F9F80`を通常の COM メカニズムを通じて取得できます。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** なし

**ライブラリ:** なし

**.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](debugging-interfaces.md)
- [デバッグ](index.md)
