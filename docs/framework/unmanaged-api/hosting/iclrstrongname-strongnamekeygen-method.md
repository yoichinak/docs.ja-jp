---
title: ICLRStrongName::StrongNameKeyGen メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameKeyGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameKeyGen
helpviewer_keywords:
- StrongNameKeyGen method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameKeyGen method [.NET Framework hosting]
ms.assetid: ac5c1245-9acf-4271-9c08-3d9b7c670df3
topic_type:
- apiref
ms.openlocfilehash: db5c0dbe57607c7a3bf8b97cee734415aa934336
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2020
ms.locfileid: "83763086"
---
# <a name="iclrstrongnamestrongnamekeygen-method"></a>ICLRStrongName::StrongNameKeyGen メソッド
厳密な名前を使用するために新しい公開/秘密キーの組が作成されます。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StrongNameKeyGen (  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  DWORD     dwFlags,  
    [out] BYTE      **ppbKeyBlob,  
    [out] ULONG     *pcbKeyBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszKeyContainer`  
 から要求されたキーコンテナー名。 `wszKeyContainer`は、空でない文字列であるか、または一時名を生成するために null である必要があります。  
  
 `dwFlags`  
 からキーを登録したままにするかどうかを示す値です。 次の値がサポートされています。  
  
- 0x00000000- `wszKeyContainer` が null の場合に、一時キーコンテナー名を生成するために使用されます。  
  
- 0x00000001 ( `SN_LEAVE_KEY` )-キーを登録したままにすることを指定します。  
  
 `ppbKeyBlob`  
 入出力返された公開/秘密キーのペア。  
  
 `pcbKeyBlob`  
 入出力のサイズ (バイト単位) `ppbKeyBlob` 。  
  
## <a name="return-value"></a>戻り値  
 `S_OK`メソッドが正常に完了した場合は。それ以外の場合は、失敗を示す HRESULT 値 (「リストの[一般的な Hresult 値](/windows/win32/seccrypto/common-hresult-values)」を参照してください)。  
  
## <a name="remarks"></a>解説  
 [ICLRStrongName:: StrongNameKeyGen](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamekeygen-method.md)メソッドは、1024ビットのキーを作成します。 キーを取得した後、 [ICLRStrongName:: StrongNameFreeBuffer](iclrstrongname-strongnamefreebuffer-method.md)メソッドを呼び出して、割り当てられたメモリを解放する必要があります。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** メタホスト .h  
  
 **ライブラリ:** Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameKeyGenEx メソッド](iclrstrongname-strongnamekeygenex-method.md)
- [ICLRStrongName インターフェイス](iclrstrongname-interface.md)
