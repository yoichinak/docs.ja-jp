---
title: ICLRStrongName::StrongNameGetPublicKey メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetPublicKey method [.NET Framework hosting]
ms.assetid: a31dcaa9-a404-4c1d-8cc7-081827c52935
topic_type:
- apiref
ms.openlocfilehash: cb96c7e17627205db0573e56fc8c2a29e7717434
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181933"
---
# <a name="iclrstrongnamestrongnamegetpublickey-method"></a>ICLRStrongName::StrongNameGetPublicKey メソッド
公開キーと秘密キーのペアから公開キーを取得します。 キー ペアは、暗号化サービス プロバイダー (CSP) 内のキー コンテナー名またはバイトの生のコレクションとして提供できます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szKeyContainer`  
 [in]公開キーと秘密キーのペアを含むキー コンテナーの名前。 null`pbKeyBlob`の場合`szKeyContainer`は、CSP 内で有効なコンテナーを指定する必要があります。 この場合[、ICLRStrongName::StrongNameGetPublicKey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)メソッドは、コンテナーに格納されているキーペアから公開キーを抽出します。  
  
 null`pbKeyBlob`でない場合、キー ペアは、キー のバイナリ ラージ オブジェクト (BLOB) に含まれていると見なされます。  
  
 キーは、1024 ビットのリベスト シャミール-アドレマン (RSA) 署名キーである必要があります。 現時点では、他の種類のキーはサポートされていません。  
  
 `pbKeyBlob`  
 [in]公開キーと秘密キーのペアへのポインター。 このペアは、Win32`CryptExportKey`関数によって作成された形式です。 null`pbKeyBlob`の場合、指定されたキー`szKeyContainer`コンテナーにはキー ペアが含まれるものと見なされます。  
  
 `cbKeyBlob`  
 [in]のサイズ (バイト単位)`pbKeyBlob`です。  
  
 `ppbPublicKeyBlob`  
 [アウト]返された公開キー BLOB。 パラメーター`ppbPublicKeyBlob`は、共通言語ランタイムによって割り当てられ、呼び出し元に返されます。 呼び出し元は、メソッドを使用してメモリ[を](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)解放する必要があります。  
  
 `pcbPublicKeyBlob`  
 [アウト]返される公開キー BLOB のサイズ。  
  
## <a name="return-value"></a>戻り値  
 `S_OK`メソッドが正常に完了した場合。それ以外の場合は、失敗を示す HRESULT 値です (リストの[HRESULT の共通値](/windows/win32/seccrypto/common-hresult-values)を参照)。  
  
## <a name="remarks"></a>解説  
 公開キーは[、パブリックキー Blob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)構造体に含まれています。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameTokenFromPublicKey メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob 構造体](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
