---
title: StrongNameSignatureVerificationFromImage 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationFromImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationFromImage
helpviewer_keywords:
- StrongnameSignatureVerificationFromImage function [.NET Framework strong naming]
ms.assetid: 9fb144d2-07e0-4a0e-8e05-907bbb6c9e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54b1d35d1c40289bad465978750ba738acf28c90
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212441"
---
# <a name="strongnamesignatureverificationfromimage-function"></a>StrongNameSignatureVerificationFromImage 関数
メモリに既にマップされているアセンブリが、関連付けられている公開キーに対して有効であるかどうかが確認されます。  
  
 この関数は非推奨とされました。 使用して、 [ICLRStrongName::StrongNameVerificationFromImage](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameSignatureVerificationFromImage (  
    [in]  BYTE    *pbBase,  
    [in]  DWORD   dwLength,  
    [in]  DWORD   dwInFlags,  
    [out] DWORD   *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pbBase`  
 [in]マップされているアセンブリ マニフェストの相対仮想アドレス。  
  
 `dwLength`  
 [in]マップされたイメージのバイト単位のサイズ。  
  
 `dwInFlags`  
 [in]検証の動作に影響するフラグ。 次の値がサポートされています。  
  
-   `SN_INFLAG_FORCE_VER` (0x00000001) - レジストリ設定を上書きする必要がある場合でも、強制的に検証します。  
  
-   `SN_INFLAG_INSTALL` (0x00000002) - これはこのイメージ上で実行される最初の認証であることを指定します。  
  
-   `SN_INFLAG_ADMIN_ACCESS` (0x00000004) のキャッシュで管理者特権を持つユーザーにのみアクセスを許可することを指定します。  
  
-   `SN_INFLAG_USER_ACCESS` (0x00000008) のアセンブリが現在のユーザーのみがアクセスできることを指定します。  
  
-   `SN_INFLAG_ALL_ACCESS` (0x00000010) - キャッシュはしないことを指定のアクセス制限を保証します。  
  
-   `SN_INFLAG_RUNTIME` (0x80000000) - 内部デバッグのために予約されています。  
  
 `pdwOutFlags`  
 [out]追加の出力情報用のフラグです。 次の値がサポートされています。  
  
-   `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - この値に設定が`false`レジストリ設定のために、検証が成功したことを指定します。  
  
## <a name="return-value"></a>戻り値  
 `true` 正常に終了します。それ以外の場合、`false`します。  
  
## <a name="remarks"></a>Remarks  
 場合、`StrongNameSignatureVerificationFromImage`関数が正常に完了、呼び出すしていない、 [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md)最後に生成されたエラーを取得します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** Mscoree.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureVerificationFromImage メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationfromimage-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
