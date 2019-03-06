---
title: StrongNameSignatureVerificationEx 関数
ms.date: 03/30/2017
api_name:
- StrongNameSignatureVerificationEx
api_location:
- mscoree.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameSignatureVerificationEx
helpviewer_keywords:
- StrongNameSignatureVerificationEx function [.NET Framework strong naming]
ms.assetid: cfe4b634-18bf-44b8-9773-d94fb7e8a480
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d3f9dbbdf7ff560f292fed327a2ca1dd26c29a19
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57491894"
---
# <a name="strongnamesignatureverificationex-function"></a>StrongNameSignatureVerificationEx 関数
指定したパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値が取得されます。  
  
 この関数は非推奨とされました。 使用して、 [iclrstrongname::strongnamesignatureverificationex](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)メソッド代わりにします。  
  
## <a name="syntax"></a>構文  
  
```  
BOOLEAN StrongNameSignatureVerificationEx (  
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
 `true` 検証が成功した場合それ以外の場合、`false`します。  
  
## <a name="remarks"></a>Remarks  
 `StrongNameSignatureVerificationEx` ような機能を提供します、 [StrongNameSignatureVerification](../../../../docs/framework/unmanaged-api/strong-naming/strongnamesignatureverification-function.md)関数。 2 番目の入力パラメーターと出力パラメーター、`StrongNameSignatureVerificationEx`型`BOOLEAN`の代わりに`DWORD`します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** StrongName.h  
  
 **ライブラリ:** Mscoree.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [StrongNameSignatureVerificationEx メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverificationex-method.md)
- [StrongNameSignatureVerification メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamesignatureverification-method.md)
- [ICLRStrongName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
