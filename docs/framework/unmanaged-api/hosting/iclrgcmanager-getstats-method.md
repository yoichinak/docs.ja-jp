---
title: ICLRGCManager::GetStats メソッド
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 768d16a05bbe139c3fe02677526bc28809a93be0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779714"
---
# <a name="iclrgcmanagergetstats-method"></a>ICLRGCManager::GetStats メソッド
共通言語ランタイムのガベージ コレクション システムに関する現在の統計情報のセットを取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pStats`  
 [入力、出力]A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)要求の統計情報を格納しているインスタンス。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`GetStats` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|共通言語ランタイム (CLR) は、プロセスに読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返された、後に、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>Remarks  
 CLR を計算しで指定されている統計情報のみを返す、`Flags`フィールド`pStats`します。  
  
 設定、`Flags`フィールドの 1 つまたは複数の値を[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)で統計情報を指定する列挙体、 [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)は、構造体を設定します。  
  
 使用状況の例は次のとおりです。  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [自動メモリ管理](../../../../docs/standard/automatic-memory-management.md)
- [COR_GC_STATS 構造体](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [COR_GC_STAT_TYPES 列挙型](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)
- [ガベージ コレクション](../../../../docs/standard/garbage-collection/index.md)
- [ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICLRGCManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [CLR ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
