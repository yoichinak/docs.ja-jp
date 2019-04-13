---
title: CertFreeAuthenticodeSignerInfo 関数
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bdb764417b757cd7388c49d7e5cac9a960074820
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142403"
---
# <a name="certfreeauthenticodesignerinfo-function"></a>CertFreeAuthenticodeSignerInfo 関数
割り当てられているリソース、 [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)構造体。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pSignerInfo`  
 [in, out] リリースされる署名者情報。 参照してください、 [AXL_AUTHENTICODE_SIGNER_INFO](../../../../docs/framework/unmanaged-api/authenticode/axl-authenticode-signer-info-structure.md)構造体。  
  
## <a name="return-value"></a>戻り値  
 `S_OK` 関数が成功するとします。 それ以外の場合はエラー コードを返します。  
  
## <a name="see-also"></a>関連項目

- [Authenticode](../../../../docs/framework/unmanaged-api/authenticode/index.md)
