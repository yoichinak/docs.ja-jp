---
title: StrongNameSignatureVerification 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerification
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerification
helpviewer_keywords:
- StrongNameSignatureVerification function [.NET Framework strong naming]
ms.assetid: 933758dd-231e-4382-8819-242c0a13a4b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3cd118c302723a7079adbc0dd446d17c8afe9cb6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496769"
---
# <a name="strongnamesignatureverification-function"></a>StrongNameSignatureVerification 関数
指定したパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値が取得されます。これは指定したフラグに従って確認されます。  
  
 この関数は非推奨とされました。 使用して、 [iclrstrongname::strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameSignatureVerification (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  DWORD     dwInFlags,  
    [out] DWORD     *pdwOutFlags  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 [in]確認するアセンブリのポータブル実行可能ファイル (.dll または .exe) ファイルへのパス。  
  
 `dwInFlags`  
 [in]検証動作を変更するフラグを設定します。 次の値がサポートされています。  
  
-   `SN_INFLAG_FORCE_VER` (0x00000001) - レジストリ設定を上書きする必要がある場合でも、強制的に検証します。  
  
-   `SN_INFLAG_INSTALL` (0x00000002) - これが初めてマニフェストの検証であることを指定します。  
  
-   `SN_INFLAG_ADMIN_ACCESS` (0x00000004) のキャッシュで管理者特権を持つユーザーにのみアクセスを許可することを指定します。  
  
-   `SN_INFLAG_USER_ACCESS` (0x00000008) のアセンブリが現在のユーザーのみがアクセスできることを指定します。  
  
-   `SN_INFLAG_ALL_ACCESS` (0x00000010) - キャッシュはしないことを指定のアクセス制限を保証します。  
  
-   `SN_INFLAG_RUNTIME` (0x80000000) - 内部デバッグのために予約されています。  
  
 `pdwOutFlags`  
 [out]厳密な名前の署名が検証されたかどうかを示すフラグです。 次の値がサポートされています。  
  
-   `SN_OUTFLAG_WAS_VERIFIED` (0x00000001) - この値に設定が`false`レジストリ設定のために、検証が成功したことを指定します。  
  
## <a name="return-value"></a>戻り値  
 `true` 検証が成功した場合それ以外の場合、`false`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** MsCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [StrongNameSignatureVerification メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
