---
title: ICeeGen::GetMethodBuffer メソッド
ms.date: 03/30/2017
api_name:
- ICeeGen.GetMethodBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::GetMethodBuffer
helpviewer_keywords:
- ICeeGen::GetMethodBuffer method [.NET Framework metadata]
- GetMethodBuffer method [.NET Framework metadata]
ms.assetid: c7c5b39a-d4ac-41f1-9d1e-44163f563a49
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d8ccaa1b03ae1afc87eb7b0a66dd517bba8fcf8a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497471"
---
# <a name="iceegengetmethodbuffer-method"></a>ICeeGen::GetMethodBuffer メソッド
指定の相対仮想アドレスにあるメソッドの適切なサイズのバッファーを取得します。  
  
 このメソッドは廃止され、使用する必要があります。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMethodBuffer (  
    [in]  ULONG       RVA,  
    [out] UCHAR       **lpBuffer  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `RVA`  
 [in]バッファーを返す対象のメソッドの相対仮想アドレス。  
  
 `lpBuffer`  
 [out]返されたバッファーへのポインター。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICeeGen インターフェイス](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
