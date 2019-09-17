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
ms.openlocfilehash: 89398c221dcf9d6f89027f15da4062bc7ed67e3f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798984"
---
# <a name="strongnamesignaturegenerationex-function"></a>StrongNameSignatureGenerationEx 関数
指定したフラグに従って、指定したアセンブリの厳密な名前の署名を生成します。  
  
 この関数は非推奨とされます。 代わりに[ICLRStrongName:: StrongNameSignatureGenerationEx](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 から厳密な名前の署名が生成されるアセンブリのマニフェストを含むファイルへのパス。  
  
 `wszKeyContainer`  
 から公開キーと秘密キーのペアを格納するキーコンテナーの名前。  
  
 が`pbKeyBlob` null の場合`wszKeyContainer` 、では、暗号化サービスプロバイダー (CSP) 内の有効なコンテナーを指定する必要があります。 この場合、コンテナーに格納されているキーペアがファイルの署名に使用されます。  
  
 が`pbKeyBlob` null でない場合、キーペアは、バイナリラージオブジェクト (BLOB) に格納されていると見なされます。  
  
 `pbKeyBlob`  
 から公開/秘密キーのペアへのポインター。 このペアは、Win32 `CryptExportKey`関数によって作成される形式です。 が`pbKeyBlob` null の場合、によって指定`wszKeyContainer`されたキーコンテナーには、キーのペアが含まれていると見なされます。  
  
 `cbKeyBlob`  
 からの`pbKeyBlob`サイズ (バイト単位)。  
  
 `ppbSignatureBlob`  
 入出力共通言語ランタイムが署名を返す場所へのポインター。 が`ppbSignatureBlob` null の場合、ランタイムはによって`wszFilePath`指定されたファイルに署名を格納します。  
  
 が`ppbSignatureBlob` null でない場合は、共通言語ランタイムによって、署名を返す領域が割り当てられます。 呼び出し元は、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md)関数を使用してこの領域を解放する必要があります。  
  
 `pcbSignatureBlob`  
 入出力返されたシグネチャのサイズ (バイト単位)。  
  
 `dwFlags`  
 から次の値の1つまたは複数です。  
  
- `SN_SIGN_ALL_FILES`(0x00000001)-リンクされたモジュールのすべてのハッシュを再計算します。  
  
- `SN_TEST_SIGN`(0x00000002)-アセンブリに対してテストを行います。  
  
## <a name="return-value"></a>戻り値  
 `true`正常に完了した場合は。それ以外`false`の場合は。  
  
## <a name="remarks"></a>Remarks  
 署名を作成`wszFilePath`せずに署名のサイズを計算するには、に null を指定します。  
  
 署名は、ファイルに直接格納するか、呼び出し元に返すことができます。  
  
 が`SN_SIGN_ALL_FILES`指定されていても、公開キーが`pbKeyBlob`含ま`wszFilePath`れていない場合 (との両方が null の場合)、リンクされたモジュールのハッシュは再計算されますが、アセンブリは再署名されません。  
  
 が`SN_TEST_SIGN`指定されている場合、共通言語ランタイムヘッダーは、アセンブリが厳密な名前で署名されていることを示すために変更されません。  
  
 関数が正常に完了しない場合は、[StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。`StrongNameSignatureGenerationEx`  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureGenerationEx メソッド](../hosting/iclrstrongname-strongnamesignaturegenerationex-method.md)
- [StrongNameSignatureGeneration メソッド](../hosting/iclrstrongname-strongnamesignaturegeneration-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
