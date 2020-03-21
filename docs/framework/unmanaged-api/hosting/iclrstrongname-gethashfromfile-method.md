---
title: ICLRStrongName::GetHashFromFile メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.GetHashFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::GetHashFromFile
helpviewer_keywords:
- ICLRStrongName::GetHashFromFile method [.NET Framework hosting]
- GetHashFromFile method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 9e50480a-8ada-4044-b2a5-97bb14ed3525
topic_type:
- apiref
ms.openlocfilehash: ed735c3d7830551581df35793f3f6fdc4953dc8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178074"
---
# <a name="iclrstrongnamegethashfromfile-method"></a>ICLRStrongName::GetHashFromFile メソッド
指定したファイルの内容に対してハッシュが生成されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetHashFromFile (  
    [in]  LPCSTR   szFilePath,  
    [in, out] unsigned int   *piHashAlg,
    [out] BYTE     *pbHash,
    [in]  DWORD    cchHash,
    [out] DWORD    *pchHash  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szFilePath`  
 [in]ハッシュするファイルの名前。  
  
 `piHashAlg`  
 [イン、アウト]ハッシュを生成するときに使用するアルゴリズム。 有効なアルゴリズムは、Win32 CryptoAPI によって定義されるアルゴリズムです。 0`piHashAlg`に設定すると、デフォルトのアルゴリズム CALG_SHA-1 が使用されます。  
  
 `pbHash`  
 [アウト]生成されたハッシュを含むバイト配列。  
  
 `cchHash`  
 [in]指す`pbHash`バッファーの最大サイズ。  
  
 `pchHash`  
 [アウト]返された`pbHash`のサイズ (バイト単位)  
  
## <a name="return-value"></a>戻り値  
 `S_OK`メソッドが正常に完了した場合。それ以外の場合は、失敗を示す HRESULT 値です (リストの[HRESULT の共通値](/windows/win32/seccrypto/common-hresult-values)を参照)。  
  
## <a name="remarks"></a>解説  
 このメソッドは、ファイル名の指定が Unicode ではなく ANSI であることを除いて[、ICLRStrongName::GetHashFromFileW](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)メソッドと同じです。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [GetHashFromFileW メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-gethashfromfilew-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
