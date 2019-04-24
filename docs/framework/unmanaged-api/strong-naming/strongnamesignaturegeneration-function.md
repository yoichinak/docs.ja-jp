---
title: StrongNameSignatureGeneration 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGeneration
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGeneration
helpviewer_keywords:
- StrongNameSignatureGeneration function [.NET Framework strong naming]
ms.assetid: 839b765c-3e41-44ce-bf1b-dc10453db18e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e7df65c28fad6fa79ec7a18d8511955330b2817
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227744"
---
# <a name="strongnamesignaturegeneration-function"></a>StrongNameSignatureGeneration 関数
指定したアセンブリに対して厳密な名前の署名が生成されます。  
  
 この関数は非推奨とされました。 使用して、 [iclrstrongname::strongnamesignaturegeneration](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameSignatureGeneration (   
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
 [in]厳密な名前の署名を生成するアセンブリのマニフェストを含むファイルへのパス。  
  
 `wszKeyContainer`  
 [in]公開/秘密キー ペアを格納するキー コンテナーの名前。  
  
 場合`pbKeyBlob`が null、`wszKeyContainer`暗号化サービス プロバイダー (CSP) 内で有効なコンテナーを指定する必要があります。 ここでは、コンテナーに格納されているキーのペアは、ファイルの署名に使用します。  
  
 場合`pbKeyBlob`が null でないと見なされます、キーのペア キー バイナリ ラージ オブジェクト (BLOB) に格納します。  
  
 キーは、1024 ビット Rivest-Shamir-Adleman (RSA) 署名キーである必要があります。 この時点でその他の種類のキーがサポートされていません。  
  
 `pbKeyBlob`  
 [in]公開/秘密キーのペアへのポインター。 このペアは、Win32 によって作成された形式で、`CryptExportKey`関数。 場合`pbKeyBlob`が null で指定されたキー コンテナー`wszKeyContainer`キー ペアを格納すると見なされます。  
  
 `cbKeyBlob`  
 [in]サイズ (バイト単位) の`pbKeyBlob`します。  
  
 `ppbSignatureBlob`  
 [out]共通言語ランタイムには、署名を返す位置へのポインター。 場合`ppbSignatureBlob`が null の場合、ランタイム、シグネチャ ファイルに格納で指定された`wszFilePath`します。  
  
 場合`ppbSignatureBlob`が null でない共通言語ランタイム割り当て領域が、署名を返します。 呼び出し元が使用して、この領域を解放する必要があります、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)関数。  
  
 `pcbSignatureBlob`  
 [out]返される署名のバイト単位のサイズ。  
  
## <a name="return-value"></a>戻り値  
 `true` 正常に終了します。それ以外の場合、`false`します。  
  
## <a name="remarks"></a>Remarks  
 Null を指定`wszFilePath`署名を作成することがなく、署名のサイズを計算します。  
  
 署名は、ファイルに直接格納または呼び出し元に返されます。  
  
 場合、`StrongNameSignatureGeneration`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureGeneration メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [StrongNameSignatureGenerationEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
