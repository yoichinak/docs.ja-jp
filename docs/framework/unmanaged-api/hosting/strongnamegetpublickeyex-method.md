---
title: StrongNameGetPublicKeyEx メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameGetPublicKeyEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameGetPublicKeyEx
helpviewer_keywords:
- StrongNameGetPublicKeyEx method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameGetPublicKeyEx method [.NET Framework hosting]
ms.assetid: 63d8260c-fb32-4f8f-a357-768afd570f68
topic_type:
- apiref
ms.openlocfilehash: 93afe1afd9ea9637d039a8b4a4e81267d49c08b6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176228"
---
# <a name="strongnamegetpublickeyex-method"></a>StrongNameGetPublicKeyEx メソッド
公開キーと秘密キーのペアから公開キーを取得し、ハッシュ アルゴリズムと署名アルゴリズムを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StrongNameGetPublicKey (
    [in]  LPCWSTR   pwzKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
    [in]  ULONG     uHashAlgId,  
    [in]  ULONG     uReserved,  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pwzKeyContainer`  
 [in]公開キーと秘密キーのペアを含むキー コンテナーの名前。 null`pbKeyBlob`の場合`szKeyContainer`は、暗号化サービス プロバイダー (CSP) 内で有効なコンテナーを指定する必要があります。 この場合、メソッドは`StrongNameGetPublicKeyEx`、コンテナーに格納されているキーペアから公開キーを抽出します。  
  
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
  
 `uHashAlgId`  
 [in]アセンブリ ハッシュ アルゴリズム。 受け入れられる値の一覧については、「解説」を参照してください。  
  
 `uReserved`  
 [in]将来の使用のために予約されています。デフォルトは null です。  
  
## <a name="return-value"></a>戻り値  
 `S_OK`メソッドが正常に完了した場合。それ以外の場合は、失敗を示す HRESULT 値です (リストの[HRESULT の共通値](/windows/win32/seccrypto/common-hresult-values)を参照)。  
  
## <a name="remarks"></a>解説  
 公開キーは[、パブリックキー Blob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)構造体に含まれています。  
  
## <a name="remarks"></a>解説  
 次の表は、パラメーターに使用できる値の`uHashAlgId`セットを示しています。  
  
|名前|Value|  
|----------|-----------|  
|なし|0|  
|SHA-1|0x8004|  
|SHA-256|0x800c|  
|SHA-384|0x800d|  
|SHA-512|0x800e|  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameTokenFromPublicKey メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob 構造体](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [StrongNameGetPublicKey メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
