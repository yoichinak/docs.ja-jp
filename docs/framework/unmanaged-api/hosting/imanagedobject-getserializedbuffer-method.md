---
title: IManagedObject::GetSerializedBuffer メソッド
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7930e993640e1ae88ce65b6c2025a5b62a0d0999
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502463"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a>IManagedObject::GetSerializedBuffer メソッド
この管理対象のオブジェクトの文字列表現を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pBSTR`  
 [out]シリアル化されたオブジェクトを表す文字列へのポインター。  
  
## <a name="remarks"></a>Remarks  
 `GetSerializedBuffer`メソッドは、クライアントにマーシャ リングできるように、オブジェクトをシリアル化します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [IManagedObject インターフェイス](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
