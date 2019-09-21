---
title: GetHashFromBlob 関数
ms.date: 03/30/2017
api_name:
- GetHashFromBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetHashFromBlob
helpviewer_keywords:
- GetHashFromBlob function [.NET Framework strong naming]
ms.assetid: b712d862-f2d0-4b55-87d4-65bbeadef982
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 59b4df08157ce14a58393e54b671e8f41b8998ed
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799235"
---
# <a name="gethashfromblob-function"></a>GetHashFromBlob 関数

指定したハッシュ アルゴリズムを使用して、指定したメモリ アドレスにあるアセンブリのハッシュが取得されます。

この関数は非推奨とされます。 代わりに[ICLRStrongName:: GetHashFromBlob](../hosting/iclrstrongname-gethashfromblob-method.md)メソッドを使用してください。

## <a name="syntax"></a>構文

```cpp
HRESULT GetHashFromBlob (
    [in]  BYTE    *pbBlob,
    [in]  DWORD   cchBlob,
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE    *pbHash,
    [in]  DWORD   cchHash,
    [out] DWORD   *pchHash
);
```

## <a name="parameters"></a>パラメーター

`pbBlob`\
からハッシュされるメモリブロックのアドレスへのポインター。

`cchBlob`\
からメモリブロックの長さ (バイト単位)。

`piHashAlg`\
[入力、出力]ハッシュアルゴリズムを指定する定数。 既定のアルゴリズムには0を使用します。

`pbHash`\
入出力返されたハッシュバッファー。

`cchHash`\
から要求された最大`pbHash`サイズ。

`pchHash`\
入出力返さ`pbHash`れたのサイズ (バイト単位)。

## <a name="requirements"></a>必要条件

**・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** StrongName

**ライブラリ**Mscoree.dll にリソースとして含まれています

**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>関連項目

- [GetHashFromBlob メソッド](../hosting/iclrstrongname-gethashfromblob-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
