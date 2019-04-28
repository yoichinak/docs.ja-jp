---
title: CloseEnum メソッド
ms.date: 03/30/2017
api_name:
- CloseEnum
- IALink.CloseEnum
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- CloseEnum
helpviewer_keywords:
- CloseEnum method
ms.assetid: aa4a091e-13fe-4264-91de-e12f1c767c87
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fd7d63596690e2a5d0bc26448884ec09ecd63231
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790079"
---
# <a name="closeenum-method"></a>CloseEnum メソッド
指定の列挙体を終了し、関連付けられているリソースを解放します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CloseEnum(  
    HALINKENUM hEnum  
) PURE;  
```  
  
## <a name="parameters"></a>パラメーター  
 `hEnum`  
 終了する列挙体のハンドル。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は、S_OK を返します。  
  
## <a name="requirements"></a>必要条件  
 Alink.h が必要です。  
  
## <a name="see-also"></a>関連項目

- [IALink インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [IALink2 インターフェイス](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [ALink API](../../../../docs/framework/unmanaged-api/alink/index.md)
