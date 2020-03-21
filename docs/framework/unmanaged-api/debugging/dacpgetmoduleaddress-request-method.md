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
ms.openlocfilehash: 6850dc256a70e0c0343104b3904e9eda62d11e7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179208"
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

**:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
**ヘッダー:** なし**ライブラリ:** なし  
**.NET Framework のバージョン:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [インターフェイス](dacpgetmoduleaddress-structure.md)
