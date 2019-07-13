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
ms.openlocfilehash: 6ba049723710b378a90d17c67735a05e8a09d05d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "65636857"
---
# <a name="gethashfromblob-function"></a>GetHashFromBlob 関数

指定したハッシュ アルゴリズムを使用して、指定したメモリ アドレスにあるアセンブリのハッシュが取得されます。

この関数は非推奨とされました。 使用して、 [iclrstrongname::gethashfromblob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromblob-method.md)メソッド代わりにします。

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
[in]ハッシュされるメモリ ブロックのアドレスへのポインター。

`cchBlob`\
[in]メモリ ブロックの長さ、(バイト単位)。

`piHashAlg`\
[入力、出力]ハッシュ アルゴリズムを指定する定数。 既定のアルゴリズムに 0 を使用します。

`pbHash`\
[out]返されたハッシュ バッファー。

`cchHash`\
[in]要求の最大サイズの`pbHash`します。

`pchHash`\
[out]サイズ (バイト単位)、返された`pbHash`します。

## <a name="requirements"></a>必要条件

**プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。

**ヘッダー:** StrongName.h

**ライブラリ:** MsCorEE.dll でリソースとして含まれます

**.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]

## <a name="see-also"></a>関連項目

- [GetHashFromBlob メソッド](../hosting/iclrstrongname-gethashfromblob-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
