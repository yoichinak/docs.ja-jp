---
title: ICLRControl::GetCLRManager メソッド
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 33c790bf2721f09b263494e845356ef6b6712f99
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59177139"
---
# <a name="iclrcontrolgetclrmanager-method"></a>ICLRControl::GetCLRManager メソッド
ホストは、共通言語ランタイム (CLR) の構成に使用できる、マネージャーの種類のいずれかのインスタンスへのインターフェイス ポインターを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `riid`  
 [in]`IID`のマネージャーの種類を返します。 次`IID`値がサポートされています。  
  
-   IID_ICLRDebugManager:指定します`ppObject`型[ICLRDebugManager](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)します。  
  
-   IID_ICLRErrorReportingManager:指定します`ppObject`型[ICLRErrorReportingManager](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)します。  
  
-   IID_ICLRGCManager:指定します`ppObject`型[ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)します。  
  
-   IID_ICLRHostProtectionManager:指定します`ppObject`型[ICLRHostProtectionManager](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)します。  
  
-   IID_ICLROnEventManager:指定します`ppObject`型[ICLROnEventManager](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)します。  
  
-   IID_ICLRPolicyManager:指定します`ppObject`型[ICLRPolicyManager](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)します。  
  
-   IID_ICLRTaskManager: speciries を`ppObject`型[ICLRTaskManager](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)します。  
  
 `ppObject`  
 [out]要求マネージャーは、または null の場合、無効なマネージャーの種類が要求された場合にインターフェイス ポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|メソッドが正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|プロセスに CLR が読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返された、後に、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
|E_NOINTERFACE|インターフェイスの種類がサポートされていません。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [IHostControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
