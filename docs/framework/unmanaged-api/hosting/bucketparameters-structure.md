---
title: BucketParameters 構造体
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
ms.openlocfilehash: 4d9de489bdeb0ab506f56ff08f4afb4cf6d0ab4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178286"
---
# <a name="bucketparameters-structure"></a>BucketParameters 構造体
イベントの型名と、イベントに関連付けられている現在の例外のパラメーターを格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`fInited`|`true`この構造体の残りの部分が有効な場合は、この構造体を参照します。それ以外`false`の場合は、 .|  
|`pszEventTypeName`|イベントの種類の名前。|  
|`pszParams`|イベントに関連付けられている現在の例外のパラメーターを指定する文字列の配列。|  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** MSCorEE.idl  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト構造体](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
