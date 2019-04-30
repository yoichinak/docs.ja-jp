---
title: _AxlPublicKeyBlobToPublicKeyToken 関数
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1b2535441da173ee13653c68f25039fd1431261a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948955"
---
# <a name="axlpublickeyblobtopublickeytoken-function"></a>_AxlPublicKeyBlobToPublicKeyToken 関数
CSP PUBLICKEYBLOB 形式から厳密な名前の公開キー トークンを算出します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pCspPublicKeyBlob`  
 [in] CSP 公開キー BLOB。  
  
 `ppwszPublicKeyHash`  
 [out] 16 進エンコードされた公開キー ハッシュを受け取るための WCHAR * へのポインター。  
  
## <a name="return-value"></a>戻り値  
 関数が成功した場合は `S_OK`、それ以外の場合は `S_FALSE`。  
  
## <a name="see-also"></a>関連項目

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
