---
title: IHostFilter::MarkToken メソッド
ms.date: 03/30/2017
api_name:
- IHostFilter.MarkToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostFilter::MarkToken
helpviewer_keywords:
- MarkToken method, IHostFilter interface [.NET Framework metadata]
- IHostFilter::MarkToken method [.NET Framework metadata]
ms.assetid: d7061343-d0a3-4fd5-b312-61974f98bd62
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96f0b1648c8182b4d075a479f9bd376dbe33ef61
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57487904"
---
# <a name="ihostfiltermarktoken-method"></a>IHostFilter::MarkToken メソッド
指定したメタデータ トークンを処理することを示します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT MarkToken (  
    [in]  mdToken         tk  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `tk`  
 [in]処理するメタデータ トークンです。  
  
## <a name="remarks"></a>Remarks  
 通常、メタデータ スコープ内にある場合、処理するためのトークンが必要です。 `MarkToken`メソッドが使用してメタデータ エンジンに渡される、 [imetadataemit::sethandler](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-sethandler-method.md)メソッド。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして使用  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [メタデータ インターフェイス](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IHostFilter インターフェイス](../../../../docs/framework/unmanaged-api/metadata/ihostfilter-interface.md)
