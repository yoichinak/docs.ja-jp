---
title: ICLRStrongName::StrongNameGetBlobFromImage メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlobFromImage
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlobFromImage
helpviewer_keywords:
- StrongNameGetBlobFromImage method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameGetBlobFromImage method [.NET Framework hosting]
ms.assetid: 0f5a2ec8-e776-4fd8-bda6-937b6834575a
topic_type:
- apiref
ms.openlocfilehash: ad3b151165eb233bd3a4a78d8f4d612a696b7e93
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73135093"
---
# <a name="iclrstrongnamestrongnamegetblobfromimage-method"></a>ICLRStrongName::StrongNameGetBlobFromImage メソッド
指定したメモリ アドレスにあるアセンブリ イメージのバイナリ表現が取得されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StrongNameGetBlobFromImage (  
    [in]  BYTE        *pbBase,  
    [in]  DWORD       dwLength,  
    [in]  BYTE        *pbBlob,  
    [in, out] DWORD   *pcbBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pbBase`  
 からマップされたアセンブリマニフェストのメモリアドレス。  
  
 `dwLength`  
 から`pbBase`にあるイメージのサイズ (バイト単位)。  
  
 `pbBlob`  
 からイメージのバイナリ表現を格納するバッファー。  
  
 `pcbBlob`  
 [入力、出力]`pbBlob`の要求された最大サイズ (バイト単位)。 返されたときに、`pbBlob`の実際のサイズ (バイト単位)。  
  
## <a name="return-value"></a>戻り値  
 メソッドが正常に完了した場合は `S_OK`。それ以外の場合は、失敗を示す HRESULT 値 (「リストの[一般的な Hresult 値](https://go.microsoft.com/fwlink/?LinkId=213878)」を参照してください)。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameGetBlob メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
