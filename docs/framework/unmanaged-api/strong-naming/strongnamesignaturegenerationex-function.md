---
title: StrongNameSignatureGenerationEx 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureGenerationEx
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureGenerationEx
helpviewer_keywords:
- StrongNameSignatureGenerationEx function [.NET Framework strong naming]
ms.assetid: 9a75469e-aa49-4e32-ad48-3bafd5202f09
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e5d60b9a9ae566b5bd686b27b2e09861a8414979
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190016"
---
# <a name="strongnamesignaturegenerationex-function"></a>StrongNameSignatureGenerationEx 関数
指定したフラグに基づいて、指定されたアセンブリの厳密な名前の署名を生成します。  
  
 この関数は非推奨とされました。 使用して、 [iclrstrongname::strongnamesignaturegenerationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameSignatureGenerationEx (  
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
  
 場合`ppbSignatureBlob`が null でない共通言語ランタイム割り当て領域が、署名を返します。 呼び出し元が使用して、この領域を解放する必要があります、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)関数。  
  
 `pcbSignatureBlob`  
 [out]返される署名のバイト単位のサイズ。  
  
 `dwFlags`  
 [in]1 つ以上の次の値。  
  
-   `SN_SIGN_ALL_FILES` (0x00000001) - リンクされたモジュールのすべてのハッシュを再計算します。  
  
-   `SN_TEST_SIGN` (0x00000002) - テスト アセンブリに署名します。  
  
## <a name="return-value"></a>戻り値  
 `true` 正常に終了します。それ以外の場合、`false`します。  
  
## <a name="remarks"></a>Remarks  
 Null を指定`wszFilePath`署名を作成することがなく、署名のサイズを計算します。  
  
 署名は、いずれか、ファイルに直接格納または呼び出し元に返されます。  
  
 場合`SN_SIGN_ALL_FILES`が指定されてが公開キーは含まれません (両方`pbKeyBlob`と`wszFilePath`が null の場合)、リンクされたモジュールのハッシュが再計算されますが、アセンブリは、再署名することはありません。  
  
 場合`SN_TEST_SIGN`を指定すると、共通言語ランタイム ヘッダーは、アセンブリが厳密な名前で署名されているかを示すには変更されません。  
  
 場合、`StrongNameSignatureGenerationEx`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureGenerationEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [StrongNameSignatureGeneration メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
