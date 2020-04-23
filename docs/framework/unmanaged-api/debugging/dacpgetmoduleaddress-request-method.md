---
title: メソッドを要求します。
ms.date: 01/16/2019
api.name:
- DacpGetModuleAddress::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpGetModuleAddress::Request Method
helpviewer.keywords:
- DacpGetModuleAddress::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4dbe6a2c295e5afae1b6761f0c7b695fdb906428
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102908"
---
# <a name="dacpgetmoduleaddressrequest-method"></a>メソッドを要求します。

指定されたランタイム構造体から構造体を設定する要求を実行します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文

```cpp
HRESULT Request(
    [in] IXCLRDataModule* pDataModule
);
```

## <a name="parameters"></a>パラメーター

`pDataModule`\
[in]シード データ モジュールへのポインター。

## <a name="remarks"></a>解説

この構造体はランタイム内に存在し、ヘッダーやライブラリ ファイルを通じて公開されません。 これを使用するには、実装を模倣するのが最も簡単な方法です。

- 次のパラメーターを使用して、`Request`パラメーターのメソッド`IXCLRDataModule*`を呼び出した結果取得した値を返します。`((uint32) 0xf0000000, 0, 0, (uint32) sizeof(*this), (uint8*) this)`

## <a name="requirements"></a>必要条件

**プラットフォーム:**[「システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。\
**ヘッダー:** なし\
**ライブラリ:** なし\
**.NET フレームワークのバージョン:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [構造体](dacpgetmoduleaddress-structure.md)
