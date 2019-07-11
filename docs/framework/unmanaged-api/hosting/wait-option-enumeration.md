---
title: WAIT_OPTION 列挙型
ms.date: 03/30/2017
api_name:
- WAIT_OPTION
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- WAIT_OPTION
helpviewer_keywords:
- WAIT_OPTION enumeration [.NET Framework hosting]
ms.assetid: 962fc293-8ded-4b3b-90ce-2c21a4f1b244
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eda866c1a1f1f69f0d042ccfde3dfad293df9b37
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776510"
---
# <a name="waitoption-enumeration"></a>WAIT_OPTION 列挙型
ホストのアクションは、共通言語ランタイム (CLR) ブロックによって要求された操作を実行する必要がありますかを示す値が含まれています。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef enum {  
    WAIT_MSGPUMP       = 0x1,  
    WAIT_ALERTABLE     = 0x2,  
    WAIT_NOTINDEADLOCK = 0x4,  
} WAIT_OPTION;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`WAIT_ALERTABLE`|CLR を呼び出す場合に、タスクが起動されることをホストに通知、 [ihosttask::alert](../../../../docs/framework/unmanaged-api/hosting/ihosttask-alert-method.md)メソッド。|  
|`WAIT_MSGPUMP`|スレッドがブロックされた場合に、現在の OS スレッドでメッセージをポンプする必要があります、ホストに通知します。 ランタイムでのみこの値を指定します、<xref:System.Threading.ApartmentState.STA>スレッド。|  
|`WAIT_NOTINDEADLOCK`|ホストによって指定された同期要求を分けることのできないことをホストに通知します。 つまり、ホストを返すことができない`HOST_E_DEADLOCK`します。|  
  
## <a name="remarks"></a>Remarks  
 [Ihosttaskmanager::sleep](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-sleep-method.md)と[ihosttaskmanager::switchtotask](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-switchtotask-method.md)両方のメソッドは、この型のパラメーターを受け取ります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
