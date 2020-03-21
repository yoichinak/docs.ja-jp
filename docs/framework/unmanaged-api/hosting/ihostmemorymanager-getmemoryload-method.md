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
ms.openlocfilehash: 88acd50c83eb1ff4d59aa50d677db2383912659a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176280"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a>IHostMemoryManager::GetMemoryLoad メソッド
ホストによって報告された、現在使用中であり、したがって利用できない物理メモリの量を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pMemoryLoad`  
 [アウト]現在使用中の物理メモリの合計に対する概算のパーセンテージへのポインター。  
  
 `pAvailableBytes`  
 [アウト]共通言語ランタイム (CLR) で使用できるバイト数へのポインター。  
  
## <a name="return-value"></a>戻り値  
  
|HRESULT|説明|  
|-------------|-----------------|  
|S_OK|`GetMemoryLoad`正常に返されました。|  
|HOST_E_CLRNOTAVAILABLE|CLR がプロセスに読み込まれていないか、CLR がマネージ コードを実行できない状態または呼び出しを正常に処理できない状態にあります。|  
|HOST_E_TIMEOUT|通話がタイムアウトしました。|  
|HOST_E_NOT_OWNER|呼び出し元がロックを所有していません。|  
|HOST_E_ABANDONED|ブロックされたスレッドまたはファイバが待機しているときにイベントがキャンセルされました。|  
|E_FAIL|不明な致命的なエラーが発生しました。 メソッドがE_FAILを返すと、CLR はプロセス内で使用できなくなります。 ホスト メソッドへの後続の呼び出しは、HOST_E_CLRNOTAVAILABLEを返します。|  
  
## <a name="remarks"></a>解説  
 `GetMemoryLoad`Win32`GlobalMemoryStatus`関数をラップします。 の値`pMemoryLoad`は、 から`dwMemoryLoad``MEMORYSTATUS``GlobalMemoryStatus`返される構造体のフィールドと同じです。  
  
 ランタイムは、ガベージ コレクターのヒューリスティックとして戻り値を使用します。 たとえば、ホストがメモリの大部分が使用中であると報告した場合、ガベージ コレクターは、使用可能になる可能性のあるメモリの量を増やすために、複数の世代から収集することを選択できます。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** msCorEE.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- <xref:System.GC?displayProperty=nameWithType>
- [IHostMemoryManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
