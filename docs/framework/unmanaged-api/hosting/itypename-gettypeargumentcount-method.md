---
title: ITypeName::GetTypeArgumentCount メソッド
ms.date: 03/30/2017
api_name:
- ITypeName.GetTypeArgumentCount
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetTypeArgumentCount
helpviewer_keywords:
- GetTypeArgumentCount method [.NET Framework hosting]
- ITypeName::GetTypeArgumentCount method [.NET Framework hosting]
ms.assetid: ecb5480c-761a-4b02-83e0-b79abc67fd08
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07deb2c1b7100362b7dbce41e25db53308de809c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59159862"
---
# <a name="itypenamegettypeargumentcount-method"></a>ITypeName::GetTypeArgumentCount メソッド
このメソッドは、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetTypeArgumentCount (  
    [out, retval] DWORD* pCount  
);  
```  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
