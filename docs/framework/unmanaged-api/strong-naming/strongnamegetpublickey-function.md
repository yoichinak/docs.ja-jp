---
title: StrongNameGetPublicKey 関数
ms.date: 03/30/2017
api_name:
- StrongNameGetPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetPublicKey
helpviewer_keywords:
- StrongNameGetPublicKey function [.NET Framework strong naming]
ms.assetid: 5b58c87f-3f72-40df-9b9a-291076931cc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ae87ebd0b8225f14ca029fac80528d47f5a866cf
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/07/2019
ms.locfileid: "70799063"
---
# <a name="strongnamegetpublickey-function"></a>StrongNameGetPublicKey 関数
秘密/公開キーの組から公開キーが取得されます。 キーペアは、暗号化サービスプロバイダー (CSP) 内のキーコンテナー名として、またはバイトの未加工コレクションとして指定できます。  
  
 この関数は非推奨とされます。 代わりに[ICLRStrongName:: StrongNameGetPublicKey](../hosting/iclrstrongname-strongnamegetpublickey-method.md)メソッドを使用してください。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEAN StrongNameGetPublicKey (   
    [in]  LPCWSTR   szKeyContainer,  
    [in]  BYTE      *pbKeyBlob,  
    [in]  ULONG     cbKeyBlob,  
    [out] BYTE      **ppbPublicKeyBlob,  
    [out] ULONG     *pcbPublicKeyBlob  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `szKeyContainer`  
 から公開キーと秘密キーのペアを格納するキーコンテナーの名前。 が`pbKeyBlob` null の場合`szKeyContainer` 、は CSP 内の有効なコンテナーを指定する必要があります。 この場合、は`StrongNameGetPublicKey` 、コンテナーに格納されているキーペアから公開キーを抽出します。  
  
 が`pbKeyBlob` null でない場合、キーペアは、バイナリラージオブジェクト (BLOB) に格納されていると見なされます。  
  
 キーは 1024-Rivest-shamir-adleman-Rivest-shamir-adleman (RSA) 署名キーである必要があります。 この時点では、他の種類のキーはサポートされていません。  
  
 `pbKeyBlob`  
 から公開/秘密キーのペアへのポインター。 このペアは、Win32 `CryptExportKey`関数によって作成される形式です。 が`pbKeyBlob` null の場合、によって指定`szKeyContainer`されたキーコンテナーには、キーのペアが含まれていると見なされます。  
  
 `cbKeyBlob`  
 からの`pbKeyBlob`サイズ (バイト単位)。  
  
 `ppbPublicKeyBlob`  
 入出力返された公開キー BLOB。 `ppbPublicKeyBlob`パラメーターは、共通言語ランタイムによって割り当てられ、呼び出し元に返されます。 呼び出し元は、 [StrongNameFreeBuffer](strongnamefreebuffer-function.md)関数を使用してメモリを解放する必要があります。  
  
 `pcbPublicKeyBlob`  
 入出力返される公開キー BLOB のサイズ。  
  
## <a name="return-value"></a>戻り値  
 `true`正常に完了した場合は。それ以外`false`の場合は。  
  
## <a name="remarks"></a>Remarks  
 公開キーは[Publickeyblob](publickeyblob-structure.md)構造に含まれています。  
  
 関数が正常に完了しない場合は、[StrongNameErrorInfo](strongnameerrorinfo-function.md) 関数を呼び出して、最後に生成されたエラーを取得します。`StrongNameGetPublicKey`  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameGetPublicKey メソッド](../hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [StrongNameTokenFromPublicKey メソッド](../hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [ICLRStrongName インターフェイス](../hosting/iclrstrongname-interface.md)
- [PublicKeyBlob 構造体](publickeyblob-structure.md)
