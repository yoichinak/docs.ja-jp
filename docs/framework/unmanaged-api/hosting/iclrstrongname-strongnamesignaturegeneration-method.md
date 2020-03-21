---
title: ICLRStrongName::StrongNameSignatureGeneration メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGeneration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureGeneration method [.NET Framework hosting]
ms.assetid: 4cdb1284-947a-4ed4-94c1-c5ff5cdfce56
topic_type:
- apiref
ms.openlocfilehash: e58ac181c4e472c469076b880ff71e0c6afa30fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178050"
---
# <a name="iclrstrongnamestrongnamesignaturegeneration-method"></a>ICLRStrongName::StrongNameSignatureGeneration メソッド
指定したアセンブリに対して厳密な名前の署名が生成されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StrongNameSignatureGeneration (
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 [in]厳密な名前の署名が生成されるアセンブリのマニフェストを含むファイルへのパス。  
  
 `wszKeyContainer`  
 [in]公開キーと秘密キーのペアを含むキー コンテナーの名前。  
  
 null`pbKeyBlob`の場合`wszKeyContainer`は、暗号化サービス プロバイダー (CSP) 内で有効なコンテナーを指定する必要があります。 この場合、コンテナーに格納されているキーペアを使用してファイルに署名します。  
  
 null`pbKeyBlob`でない場合、キー ペアは、キー のバイナリ ラージ オブジェクト (BLOB) に含まれていると見なされます。  
  
 キーは、1024 ビットのリベスト シャミール-アドレマン (RSA) 署名キーである必要があります。 現時点では、他の種類のキーはサポートされていません。  
  
 `pbKeyBlob`  
 [in]公開キーと秘密キーのペアへのポインター。 このペアは、Win32`CryptExportKey`関数によって作成された形式です。 null`pbKeyBlob`の場合、指定されたキー`wszKeyContainer`コンテナーにはキー ペアが含まれるものと見なされます。  
  
 `cbKeyBlob`  
 [in]のサイズ (バイト単位)`pbKeyBlob`です。  
  
 `ppbSignatureBlob`  
 [アウト]共通言語ランタイムが署名を返す場所へのポインター。 null`ppbSignatureBlob`の場合、ランタイムは、 で指定されたファイルに`wszFilePath`署名を格納します。  
  
 null`ppbSignatureBlob`でない場合、共通言語ランタイムは、署名を返す領域を割り当てます。 呼び出し元は、メソッドを使用してこの領域[を解放](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)する必要があります。  
  
 `pcbSignatureBlob`  
 [アウト]返されたシグネチャのサイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  
 `S_OK`メソッドが正常に完了した場合。それ以外の場合は、失敗を示す HRESULT 値です (リストの[HRESULT の共通値](/windows/win32/seccrypto/common-hresult-values)を参照)。  
  
## <a name="remarks"></a>解説  
 署名を`wszFilePath`作成せずに署名のサイズを計算するには、 に null を指定します。  
  
 署名は、ファイルに直接格納するか、または呼び出し元に返すことができます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureGenerationEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
