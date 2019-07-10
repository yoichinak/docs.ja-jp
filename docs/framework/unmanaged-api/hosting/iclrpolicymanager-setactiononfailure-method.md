---
title: ICLRPolicyManager::SetActionOnFailure メソッド
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager.SetActionOnFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager::SetActionOnFailure
helpviewer_keywords:
- SetActionOnFailure method [.NET Framework hosting]
- ICLRPolicyManager::SetActionOnFailure method [.NET Framework hosting]
ms.assetid: 4664033f-db97-4388-b988-2ec470796e58
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 76f064d1683615ef8f665cf1facaa31d61b294a5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759598"
---
# <a name="iclrpolicymanagersetactiononfailure-method"></a>ICLRPolicyManager::SetActionOnFailure メソッド
共通言語ランタイム (CLR) が指定したエラーが発生したときに実行する必要がありますポリシーのアクションを指定します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT SetActionOnFailure (  
    [in] EClrFailure   failure,  
    [in] EPolicyAction action  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `failure`  
 [in]1 つ、 [EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)アクションを実行する対象のエラーの種類を示す値。  
  
 `action`  
 [in]1 つ、 [EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)障害が発生したときに実行されるアクションを示す値。 サポートされている値の一覧は、「解説」を参照してください。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`SetActionOnFailure` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|プロセスに CLR が読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返された、後に、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
|E_INVALIDARG|指定された操作のポリシーのアクションを設定することはできませんまたは操作に無効なポリシー アクションが指定されました。|  
  
## <a name="remarks"></a>Remarks  
 既定では、CLR は、メモリなどのリソースの割り当てに失敗した場合に例外をスローします。 `SetActionOnFailure` により、ホストは、障害発生時に実行するポリシーのアクションを指定することでこの動作をオーバーライドします。 次の表は、組み合わせの[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)と[EPolicyAction](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)サポートされている値。 (から FAIL_ プレフィックスを省略すると[EClrFailure](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)値)。  
  
||NonCriticalResource|CriticalResource|FatalRuntime|OrphanedLock|StackOverflow|AccessViolation|CodeContract|  
|-|-------------------------|----------------------|------------------|------------------|-------------------|---------------------|------------------|  
|`eNoAction`|x|x||||N/A||  
|eThrowException|x|x||||N/A||  
|`eAbortThread`|x|x||||N/A|x|  
|`eRudeAbortThread`|X|x||||N/A|x|  
|`eUnloadAppDomain`|X|X||x||N/A|x|  
|`eRudeUnloadAppDomain`|X|X||X|x|N/A|x|  
|`eExitProcess`|X|X||X|x|N/A|x|  
|eFastExitProcess|x|X||X|x|N/A||  
|`eRudeExitProcess`|x|X|X|X|x|N/A||  
|`eDisableRuntime`|x|X|X|X|x|N/A||  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [EClrFailure 列挙型](../../../../docs/framework/unmanaged-api/hosting/eclrfailure-enumeration.md)
- [EPolicyAction 列挙型](../../../../docs/framework/unmanaged-api/hosting/epolicyaction-enumeration.md)
- [ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)
