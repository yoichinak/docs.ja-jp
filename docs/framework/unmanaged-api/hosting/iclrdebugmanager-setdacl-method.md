---
title: ICLRDebugManager::SetDacl メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetDacl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetDacl
helpviewer_keywords:
- SetDacl method [.NET Framework hosting]
- ICLRDebugManager::SetDacl method [.NET Framework hosting]
ms.assetid: 52f4af3f-e02b-4c20-9fd9-e8e4f4d6fc31
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: abe9a7b617e5fec0f25765dc5eb94d57ead1ffcc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61984831"
---
# <a name="iclrdebugmanagersetdacl-method"></a>ICLRDebugManager::SetDacl メソッド
このメソッドは実装されていません。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetDacl (  
    [in] PACL pacl  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pacl`  
 [in]アクセス制御リスト (ACL) へのポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|E_NOTIMPL|メソッドが実装されていません。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRDebugManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
- [GetDacl メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)
- [IHostControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
