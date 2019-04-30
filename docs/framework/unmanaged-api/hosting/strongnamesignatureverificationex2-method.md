---
title: StrongNameSignatureVerificationEx2 メソッド
ms.date: 03/30/2017
api_name:
- ICLRStrongName2.StrongNameSignatureVerificationEx2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StrongNameSignatureVerificationEx2
helpviewer_keywords:
- StrongNameSignatureVerificationEx2 method, ICLRStrongName2 interface [.NET Framework hosting]
- ICLRStrongName2::StrongNameSignatureVerificationEx2 method [.NET Framework hosting]
ms.assetid: dfd4133f-a074-4db3-a7ee-4f250fe9ad3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aab3b697a0bb2f58258816ce4f8133009b26f54a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043408"
---
# <a name="strongnamesignatureverificationex2-method"></a>StrongNameSignatureVerificationEx2 メソッド
厳密な名前付きのアセンブリの署名を検証し、ECMA キーから実際のキーへのマッピングを提供します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT StrongNameSignatureVerificationEx (  
    [in]  LPCWSTR   wszFilePath,  
    [in]  BOOLEAN   fForceVerification,    [in]  BYTE      *pbEcmaPublicKey,  
    [in]  DWORD     cbEcmaPublicKey,  
    [out] BOOLEAN   *pfWasVerified  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `wszFilePath`  
 [in]検証するアセンブリのポータブル実行可能 (.exe または .dll) ファイルへのパス。  
  
 `fForceVerification`  
 [in]`true` 。 それ以外のレジストリ設定を上書きする必要がある場合でも、検証を実行する`false`します。  
  
 `pbEcmaPublicKey`  
 [in]実際のキーを ECMA の公開キーからのマッピングへのポインターの検証に使用します。  
  
 `cbEcmaPublicKey`  
 [in]ECMA の実際の公開キーの長さ。  
  
 `pfWasVerified`  
 [out]`true` 、厳密な名前の署名が確認済み。 それ以外の場合`false`します。 このパラメーターに設定されても`false`検証がレジストリ設定により成功した場合。  
  
## <a name="return-value"></a>戻り値  
 `S_OK` 検証が成功した場合それ以外の場合、エラーを示す HRESULT 値 (を参照してください[の共通 HRESULT 値](https://go.microsoft.com/fwlink/?LinkId=213878)一覧については)。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MetaHost.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [StrongNameSignatureVerification メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [StrongNameSignatureVerificationEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
