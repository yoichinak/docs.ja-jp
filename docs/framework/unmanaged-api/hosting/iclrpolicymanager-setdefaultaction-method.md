---
title: ICLRPolicyManager::SetDefaultAction メソッド
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetDefaultAction
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetDefaultAction
helpviewer_keywords:
- SetDefaultAction method [.NET Framework hosting]
- ICLRPolicyManager::SetDefaultAction method [.NET Framework hosting]
ms.assetid: f9411e7a-27df-451f-9f6c-d643d6a7a7ce
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d339fbadc3260d20fac848ad7f1a9031c3443aa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2019
ms.locfileid: "59154662"
---
# <a name="iclrpolicymanagersetdefaultaction-method"></a>ICLRPolicyManager::SetDefaultAction メソッド
共通言語ランタイム (CLR) が、指定された操作が発生したときに実行する必要がありますポリシーのアクションを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetDefaultAction (  
    [in] EClrOperation operation,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `operation`  
 [in]1 つ、 [EClrOperation](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md) CLR の動作をカスタマイズする必要がありますの操作を示す値。  
  
 `action`  
 [in]1 つ、 [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)ポリシー アクション、CLR には、ときに実行する必要がありますを示す値`operation`に発生します。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`SetDefaultAction` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|プロセスに CLR が読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返された、後に、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
|E_INVALIDARG|無効な`action`が指定されました、`operation`の無効な値が指定されているまたは`operation`します。|  
  
## <a name="remarks"></a>Remarks  
 すべてのポリシーのアクション値は、CLR 操作では既定の動作として指定できます。 `SetDefaultAction` エスカレーションの動作だけに通常使用できます。 たとえば、ホストにルード スレッドの中止するになっていることを指定することができますが、スレッドの中止、その逆を指定することはできません。 次の表は、有効な説明`action`可能性のある各値`operation`値。  
  
|値 `operation`|有効な値 `action`|  
|---------------------------|-------------------------------|  
|OPR_ThreadAbort|-   eAbortThread<br />-   eRudeAbortThread<br />-eUnloadAppDomain<br />-   eRudeUnloadAppDomain<br />-eExitProcess<br />-eFastExitProcess<br />-   eRudeExitProcess<br />-   eDisableRuntime|  
|OPR_ThreadRudeAbortInNonCriticalRegion<br /><br /> OPR_ThreadRudeAbortInCriticalRegion|-   eRudeAbortThread<br />-eUnloadAppDomain<br />-   eRudeUnloadAppDomain<br />-eExitProcess<br />-eFastExitProcess<br />-   eRudeExitProcess<br />-   eDisableRuntime|  
|OPR_AppDomainUnload|-eUnloadAppDomain<br />-   eRudeUnloadAppDomain<br />-eExitProcess<br />-eFastExitProcess<br />-   eRudeExitProcess<br />-   eDisableRuntime|  
|OPR_AppDomainRudeUnload|-   eRudeUnloadAppDomain<br />-eExitProcess<br />-eFastExitProcess<br />-   eRudeExitProcess<br />-   eDisableRuntime|  
|OPR_ProcessExit|-eExitProcess<br />-eFastExitProcess<br />-   eRudeExitProcess<br />-   eDisableRuntime|  
|OPR_FinalizerRun|-eNoAction<br />-   eAbortThread<br />-   eRudeAbortThread<br />-eUnloadAppDomain<br />-   eRudeUnloadAppDomain<br />-eExitProcess<br />-eFastExitProcess<br />-   eRudeExitProcess<br />-   eDisableRuntime|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [EClrOperation 列挙型](../../../../docs/framework/unmanaged-api/hosting/eclroperation-enumeration.md)
- [EPolicyAction 列挙型](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
