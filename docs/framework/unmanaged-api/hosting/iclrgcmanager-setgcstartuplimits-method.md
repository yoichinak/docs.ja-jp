---
title: ICLRGCManager::SetGCStartupLimits メソッド
ms.date: 03/30/2017
api_name:
- ICLRGCManager.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: 1c8d9959-95b5-4131-be4a-556d97774014
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3292fae0ca78615faee4cb5208aa711fea9a0a24
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57490009"
---
# <a name="iclrgcmanagersetgcstartuplimits-method"></a>ICLRGCManager::SetGCStartupLimits メソッド
ガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズを設定します。  
  
> [!IMPORTANT]
>  以降では、[!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]セグメントのサイズを設定して、サイズの最大のジェネレーション 0 の値より大きい、`DWORD`を使用して、 [iclrgcmanager 2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)メソッド。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,   
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `SegmentSize`  
 [in]ガベージ コレクション セグメントの指定されたサイズ。  
  
 セグメントの最小サイズは、4 MB です。 セグメントには、1 MB 単位で増加以上を指定できます。  
  
 `MaxGen0Size`  
 [in]ジェネレーション 0 の指定した最大サイズ。  
  
 ジェネレーション 0 の最小サイズは、64 KB です。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`SetGCStartupLimits` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) は、プロセスに読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返された、後に、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>Remarks  
 値を`SetGCStartupLimits`セットは 1 回だけ指定できます。 後で呼び出し`SetGCStartupLimits`は無視されます。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [自動メモリ管理](../../../../docs/standard/automatic-memory-management.md)
- [ガベージ コレクション](../../../../docs/standard/garbage-collection/index.md)
- [ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRGCManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
