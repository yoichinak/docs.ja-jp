---
title: IHostMemoryManager::GetMemoryLoad メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 53001d6dfef2813df86dc4bb4f9647900143aae7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469067"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a>IHostMemoryManager::GetMemoryLoad メソッド
現在使用中で、したがって使用不可能で、ホストによって報告された、物理メモリの量を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pMemoryLoad`  
 [out]現在使用されている物理メモリの総量のおおよその割合へのポインター。  
  
 `pAvailableBytes`  
 [out]共通言語ランタイム (CLR) に使用できるバイト数へのポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`GetMemoryLoad` 正常に返されます。|  
|HOST_E_CLRNOTAVAILABLE|プロセスに CLR が読み込まれていないか、CLR は状態をマネージ コードを実行または呼び出しを正常に処理ができません。|  
|HOST_E_TIMEOUT|呼び出しがタイムアウトになりました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|イベントがキャンセルされましたブロックされたスレッドまたはファイバーが待機しています。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドには、E_FAIL が返される、ときに、CLR は、プロセス内で使用可能ではなくなりました。 メソッドをホストする後続の呼び出しには、HOST_E_CLRNOTAVAILABLE が返されます。|  
  
## <a name="remarks"></a>Remarks  
 `GetMemoryLoad` Win32 のラップ`GlobalMemoryStatus`関数。 値`pMemoryLoad`相当、`dwMemoryLoad`フィールドに、`MEMORYSTATUS`から返される構造体`GlobalMemoryStatus`します。  
  
 ランタイムは、ガベージ コレクターのヒューリスティックとして戻り値を使用します。 たとえば、ホストは、メモリの大部分が使用されているレポート、ガベージ コレクターが利用できるメモリの量を増やす複数世代から収集することがあります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- <xref:System.GC?displayProperty=nameWithType>
- [IHostMemoryManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
