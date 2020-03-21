---
title: ICLRStrongName::StrongNameTokenFromPublicKey メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey
helpviewer_keywords:
- ICLRStrongName::StrongNameTokenFromPublicKey method [.NET Framework hosting]
- StrongNameTokenFromPublicKey method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: 7962ce88-7e86-4a6f-8298-621b01ffc3c2
topic_type:
- apiref
ms.openlocfilehash: 919c1321f18ca163481d27fa204c78f38af1e456
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176319"
---
# <a name="iclrstrongnamestrongnametokenfrompublickey-method"></a>ICLRStrongName::StrongNameTokenFromPublicKey メソッド
公開キーを表すトークンを取得します。 厳密な名前トークンは、公開キーの短縮形です。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StrongNameTokenFromPublicKey (
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pbPublicKeyBlob`  
 [in]厳密な名前の署名を生成するために使用されるキー ペアのパブリック部分を含む[、型の PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)の構造体。  
  
 `cbPublicKeyBlob`  
 [in]のサイズ (バイト単位)`pbPublicKeyBlob`です。  
  
 `ppbStrongNameToken`  
 [アウト]渡されたキーに対応する厳密な名前トークン`pbPublicKeyBlob`。 共通言語ランタイムは、トークンを返すメモリを割り当てます。 呼び出し元は、メソッドを使用してこのメモリ[を](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)解放する必要があります。  
  
 `pcbStrongNameToken`  
 [アウト]返された厳密な名前トークンのサイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  
 `S_OK`メソッドが正常に完了した場合。それ以外の場合は、失敗を示す HRESULT 値です (リストの[HRESULT の共通値](/windows/win32/seccrypto/common-hresult-values)を参照)。  
  
## <a name="remarks"></a>解説  
 厳密な名前トークンは、メタデータにキー情報を格納するときに領域を節約するために使用される公開キーの短縮形です。 特に、厳密な名前トークンは、依存アセンブリを参照するためにアセンブリ参照で使用されます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト.h  
  
 **ライブラリ:** mscoree.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameGetPublicKey メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob 構造体](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
