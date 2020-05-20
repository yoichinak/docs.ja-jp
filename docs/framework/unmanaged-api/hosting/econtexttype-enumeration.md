---
title: EContextType 列挙型
ms.date: 03/30/2017
api_name:
- EContextType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EContextType
helpviewer_keywords:
- EContextType enumeration [.NET Framework hosting]
ms.assetid: 92b926a9-b87e-408a-9036-df7b752c9492
topic_type:
- apiref
ms.openlocfilehash: ceb68410e808bf7843149e3f05a39c7a98d0c000
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616295"
---
# <a name="econtexttype-enumeration"></a>EContextType 列挙型
現在実行中のスレッドのセキュリティコンテキストを記述します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    eCurrentContext    = 0x00,  
    eRestrictedContext = 0x01  
} EContextType;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`eCurrentContext`|共通言語ランタイム (CLR) が[IHostSecurityManager:: GetSecurityContext](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-getsecuritycontext-method.md)メソッドを呼び出す時点での現在のスレッドのコンテキスト、または[IHostSecurityManager:: SetSecurityContext](ihostsecuritymanager-setsecuritycontext-method.md)メソッドの呼び出しで CLR によって要求されたコンテキストを示します。|  
|`eRestrictedContext`|ホストが低い特権 (ガベージコレクター、クラスまたはモジュールコンストラクターなど) を持つコンテキストを示します。|  
  
## <a name="remarks"></a>解説  
 CLR は、 `EContextType` メソッドとメソッドの呼び出しで、値の1つをパラメーター値として提供し `IHostSecurityManager::GetSecurityContext` `IHostSecurityManager::SetSecurityContext` ます。  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** Mscoree.dll  
  
 **ライブラリ:** Mscoree.dll  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [IHostSecurityContext インターフェイス](ihostsecuritycontext-interface.md)
- [IHostSecurityManager インターフェイス](ihostsecuritymanager-interface.md)
- [ホスティングの列挙体](hosting-enumerations.md)
