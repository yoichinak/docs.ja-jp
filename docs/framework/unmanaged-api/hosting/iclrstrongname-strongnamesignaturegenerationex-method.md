---
title: ICLRStrongName::StrongNameSignatureGenerationEx メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx
helpviewer_keywords:
- ICLRStrongName::StrongNameSignatureGenerationEx method [.NET Framework hosting]
- StrongNameSignatureGenerationEx method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: c3f34584-c6e2-41fd-bb44-e44da8546309
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5d2539bc732cdc41c7514fd5d81c449ed8f17a2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59193045"
---
# <a name="iclrstrongnamestrongnamesignaturegenerationex-method"></a>ICLRStrongName::StrongNameSignatureGenerationEx メソッド
指定したフラグに基づいて、指定されたアセンブリの厳密な名前の署名を生成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT StrongNameSignatureGenerationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  LPCWSTR   wszKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbSignatureBlob,  
    [out] ULONG     *pcbSignatureBlob,  
    [in]  DWORD     dwFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 [in]厳密な名前の署名を生成するアセンブリのマニフェストを含むファイルへのパス。  
  
 `wszKeyContainer`  
 [in]公開/秘密キー ペアを格納するキー コンテナーの名前。  
  
 場合`pbKeyBlob`が null、`wszKeyContainer`暗号化サービス プロバイダー (CSP) 内で有効なコンテナーを指定する必要があります。 ここでは、コンテナーに格納されているキーのペアは、ファイルの署名に使用します。  
  
 場合`pbKeyBlob`が null でないと見なされます、キーのペア キー バイナリ ラージ オブジェクト (BLOB) に格納します。  
  
 `pbKeyBlob`  
 [in]公開/秘密キーのペアへのポインター。 このペアは、Win32 によって作成された形式で、`CryptExportKey`関数。 場合`pbKeyBlob`が null で指定されたキー コンテナー`wszKeyContainer`キー ペアを格納すると見なされます。  
  
 `cbKeyBlob`  
 [in]サイズ (バイト単位) の`pbKeyBlob`します。  
  
 `ppbSignatureBlob`  
 [out]共通言語ランタイムには、署名を返す位置へのポインター。 場合`ppbSignatureBlob`が null の場合、ランタイム、シグネチャ ファイルに格納で指定された`wszFilePath`します。  
  
 場合`ppbSignatureBlob`が null でない共通言語ランタイム割り当て領域が、署名を返します。 呼び出し元が使用して、この領域を解放する必要があります、 [iclrstrongname::strongnamefreebuffer](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamefreebuffer-method.md)メソッド。  
  
 `pcbSignatureBlob`  
 [out]返される署名のバイト単位のサイズ。  
  
 `dwFlags`  
 [in]1 つ以上の次の値。  
  
-   `SN_SIGN_ALL_FILES` (0x00000001) - リンクされたモジュールのすべてのハッシュを再計算します。  
  
-   `SN_TEST_SIGN` (0x00000002) - テスト アセンブリに署名します。  
  
## <a name="return-value"></a>戻り値  
 `S_OK` メソッドが正常に完了した場合それ以外の場合、エラーを示す HRESULT 値 (を参照してください[の共通 HRESULT 値](https://go.microsoft.com/fwlink/?LinkId=213878)一覧については)。  
  
## <a name="remarks"></a>Remarks  
 Null を指定`wszFilePath`署名を作成することがなく、署名のサイズを計算します。  
  
 署名は、いずれか、ファイルに直接格納または呼び出し元に返されます。  
  
 場合`SN_SIGN_ALL_FILES`が指定されてが公開キーは含まれません (両方`pbKeyBlob`と`wszFilePath`が null の場合)、リンクされたモジュールのハッシュが再計算されますが、アセンブリは、再署名することはありません。  
  
 場合`SN_TEST_SIGN`を指定すると、共通言語ランタイム ヘッダーは、アセンブリが厳密な名前で署名されているかを示すには変更されません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureGeneration メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
