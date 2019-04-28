---
title: ICLRStrongName::StrongNameSignatureVerificationEx メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx method, ICLRStrongName interface [.NET Framework hosting]
- ICLRStrongName::StrongNameSignatureVerificationEx method [.NET Framework hosting]
ms.assetid: dbd2f662-208b-4174-b301-5c99af91040f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b36e1d34b874f47f1edb0e1ffe3dc2fe2d87ddcc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787934"
---
# <a name="iclrstrongnamestrongnamesignatureverificationex-method"></a>ICLRStrongName::StrongNameSignatureVerificationEx メソッド
指定されたパスにあるアセンブリ マニフェストが厳密な名前の署名を含むかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 [in]検証するアセンブリのポータブル実行可能 (.exe または .dll) ファイルへのパス。  
  
 `fForceVerification`  
 [in]`true` 。 それ以外のレジストリ設定を上書きする必要がある場合でも、検証を実行する`false`します。  
  
 `pfWasVerified`  
 [out]`true` 、厳密な名前の署名が確認済み。 それ以外の場合`false`します。 `pfWasVerified` 設定されても`false`検証がレジストリ設定により成功した場合。  
  
## <a name="return-value"></a>戻り値  
 `S_OK` 検証が成功した場合それ以外の場合、エラーを示す HRESULT 値 (を参照してください[の共通 HRESULT 値](https://go.microsoft.com/fwlink/?LinkId=213878)一覧については)。  
  
## <a name="remarks"></a>Remarks  
 [Iclrstrongname::strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)メソッドと似た機能を提供する、 [iclrstrongname::strongnamesignatureverification](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)メソッド。 2 番目の入力パラメーターと出力パラメーター、 [iclrstrongname::strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)型`BOOLEAN`の代わりに`DWORD`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureVerification メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
