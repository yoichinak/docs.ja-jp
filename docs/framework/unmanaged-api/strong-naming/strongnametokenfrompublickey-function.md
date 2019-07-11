---
title: StrongNameTokenFromPublicKey 関数
ms.date: 03/30/2017
api_name:
- StrongNameTokenFromPublicKey
api_location:
- mscoree.dll
- mscorsn.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- COM
f1_keywords:
- StrongNameTokenFromPublicKey
helpviewer_keywords:
- StrongNameTokenFromPublicKey function [.NET Framework strong naming]
ms.assetid: 997e9e57-abb2-4217-bf20-1df621a75add
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68be16c559431de871dc9ddb1963897b0927d49a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67783165"
---
# <a name="strongnametokenfrompublickey-function"></a>StrongNameTokenFromPublicKey 関数
公開キーを表すトークンが取得されます。 厳密な名前トークンは、公開キーの短縮形です。  
  
 この関数は非推奨とされました。 使用して、 [iclrstrongname::strongnametokenfrompublickey](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```cpp  
BOOLEANStrongNameTokenFromPublicKey (   
    [in]  BYTE    *pbPublicKeyBlob,  
    [in]  ULONG   cbPublicKeyBlob,  
    [out] BYTE    **ppbStrongNameToken,  
    [out] ULONG   *pcbStrongNameToken  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pbPublicKeyBlob`  
 [in]型の構造体[PublicKeyBlob](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)厳密な名前の署名を生成するためのキー ペアの公開部分を格納しています。  
  
 `cbPublicKeyBlob`  
 [in]サイズ (バイト単位) の`pbPublicKeyBlob`します。  
  
 `ppbStrongNameToken`  
 [out]渡されたキーに対応する厳密な名前トークン`pbPublicKeyBlob`します。 共通言語ランタイムでは、トークンが返されるメモリを割り当てます。 呼び出し元を使用してこのメモリを解放する必要があります、 [StrongNameFreeBuffer](../../../../docs/framework/unmanaged-api/strong-naming/strongnamefreebuffer-function.md)関数。  
  
 `pcbStrongNameToken`  
 [out]厳密な名前が返されたトークンのバイト単位のサイズ。  
  
## <a name="return-value"></a>戻り値  
 `true` 正常に終了します。それ以外の場合、`false`します。  
  
## <a name="remarks"></a>Remarks  
 厳密な名前トークンは、メタデータにキー情報を格納する場合は、スペースを節約するために使用する公開キーの短縮形です。 具体的には、厳密な名前トークンは、依存アセンブリを参照するアセンブリ参照で使用されます。  
  
 場合、`StrongNameTokenFromPublicKey`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** Mscoree.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameTokenFromPublicKey メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnametokenfrompublickey-method.md)
- [StrongNameGetPublicKey メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetpublickey-method.md)
- [PublicKeyBlob 構造体](../../../../docs/framework/unmanaged-api/strong-naming/publickeyblob-structure.md)
