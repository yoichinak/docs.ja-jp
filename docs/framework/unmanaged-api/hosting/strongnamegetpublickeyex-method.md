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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7cb1f55e1d8643feb2750e8ea468f608dc3d5d40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984257"
---
# <a name="strongnamegetpublickeyex-method"></a>StrongNameGetPublicKeyEx メソッド
公開/秘密キーのペアから公開キーを取得し、ハッシュ アルゴリズムおよび署名アルゴリズムを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
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
 [in]公開/秘密キー ペアを格納するキー コンテナーの名前。 場合`pbKeyBlob`が null、`szKeyContainer`暗号化サービス プロバイダー (CSP) 内で有効なコンテナーを指定する必要があります。 ここで、`StrongNameGetPublicKeyEx`メソッドは、コンテナーに格納されているキーのペアから公開キーを抽出します。  
  
 場合`pbKeyBlob`が null でないと見なされます、キーのペア キー バイナリ ラージ オブジェクト (BLOB) に格納します。  
  
 キーは、1024 ビット Rivest-Shamir-Adleman (RSA) 署名キーである必要があります。 この時点でその他の種類のキーがサポートされていません。  
  
 `pbKeyBlob`  
 [in]公開/秘密キーのペアへのポインター。 このペアは、Win32 によって作成された形式で、`CryptExportKey`関数。 場合`pbKeyBlob`が null で指定されたキー コンテナー`szKeyContainer`キー ペアを格納すると見なされます。  
  
 `cbKeyBlob`  
 [in]サイズ (バイト単位) の`pbKeyBlob`します。  
  
 `ppbPublicKeyBlob`  
 [out]返される公開キー BLOB。 `ppbPublicKeyBlob`パラメーターは、共通言語ランタイムによって割り当てられ、呼び出し元に返されます。 呼び出し元を使用して、メモリを解放する必要があります、 [iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)メソッド。  
  
 `pcbPublicKeyBlob`  
 [out]返される公開キー BLOB のサイズ。  
  
 `uHashAlgId`  
 [in]アセンブリ ハッシュ アルゴリズム。 指定できる値の一覧については、「解説」を参照してください。  
  
 `uReserved`  
 [in]今後使用するために予約されていますnull を既定値です。  
  
## <a name="return-value"></a>戻り値  
 `S_OK` メソッドが正常に完了した場合それ以外の場合、エラーを示す HRESULT 値 (を参照してください[の共通 HRESULT 値](https://go.microsoft.com/fwlink/?LinkId=213878)一覧については)。  
  
## <a name="remarks"></a>Remarks  
 公開キーが含まれている、 [PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)構造体。  
  
## <a name="remarks"></a>Remarks  
 次の表に、許容される値のセット、`uHashAlgId`パラメーター。  
  
|名前|[値]|  
|----------|-----------|  
|なし|0|  
|SHA-1|0x8004|  
|SHA-256|0x800c|  
|SHA-384|0x800d|  
|SHA-512|0x800e|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameTokenFromPublicKey メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [PublicKeyBlob 構造体](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
- [StrongNameGetPublicKey メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
