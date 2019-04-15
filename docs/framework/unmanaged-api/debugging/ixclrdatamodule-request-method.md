---
title: IXCLRDataModule::Request メソッド
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::Request Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::Request Method
helpviewer.keywords:
- IXCLRDataModule::Request Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a02a60668ae6caaad1940395822758331b93f550
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119796"
---
# <a name="ixclrdatamodulerequest-method"></a>IXCLRDataModule::Request メソッド

要求をモジュールのデータで指定されたバッファーを設定します。

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a>構文
```
HRESULT Request([in] ULONG32 reqCode,
    [in] ULONG32 inBufferSize,
    [in, size_is(inBufferSize)] BYTE* inBuffer,
    [in] ULONG32 outBufferSize,
    [out, size_is(outBufferSize)] BYTE* outBuffer);
```

## <a name="parameters"></a>パラメーター

`reqCode`\
[in]要求の種類を送信します。

`inBufferSize`\
[in] で渡される入力バッファーのサイズ。

`inBuffer`\
[in、size_is(inBufferSize)]要求で送信される生データのバッファー ポインター。

`outBufferSize`\
[in]出力バッファーのサイズ。

`outBuffer`\
[out, size_is(outBufferSize)]要求の応答を格納するために使用するバッファーのポインター。

## <a name="remarks"></a>Remarks

指定されたメソッドは、`IXCLRDataModule`インターフェイスし、仮想メソッド テーブルの 36th スロットに対応しています。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
**ヘッダー:** なし   
**ライブラリ:** なし  
**.NET Framework のバージョン: ** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>関連項目

- [デバッグ](index.md)
- [IXCLRDataModule インターフェイス](ixclrdatamodule-interface.md)