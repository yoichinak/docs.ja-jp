---
title: COR_GC_STATS 構造体
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
ms.openlocfilehash: 2ab0c38645a8e5fbd9e71b3c1787e88bfe2c0604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176527"
---
# <a name="cor_gc_stats-structure"></a>COR_GC_STATS 構造体
共通言語ランタイム (CLR) のガベージ コレクション機構に関する統計を提供します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`Flags`|計算および返されるフィールド値を示します。|  
|`ExplicitGCCount`|外部要求によって強制されたガベージ コレクションの数を示します。|  
|`GenCollectionsTaken`|各ジェネレーションに対して実行されたガベージ コレクションの数を示します。|  
|`CommittedKBytes`|すべてのヒープでコミットされた合計キロバイト数。|  
|`ReservedKBytes`|すべてのヒープで予約された合計キロバイト数。|  
|`Gen0HeapSizeKBytes`|ジェネレーション ゼロ ヒープのサイズ (KB 単位)。|  
|`Gen1HeapSizeKBytes`|ジェネレーション 1 ヒープのサイズ (KB 単位)。|  
|`Gen2HeapSizeKBytes`|ジェネレーション 2 ヒープのサイズ (KB 単位)。|  
|`LargeObjectHeapSizeKBytes`|ラージ オブジェクト ヒープのサイズ (KB 単位)。|  
|`KBytesPromotedFromGen0`|ジェネレーション 0 からジェネレーション 1 に昇格したオブジェクトのサイズ (KB 単位)。|  
|`KBytesPromotedFromGen1`|ジェネレーション 1 からジェネレーション 2 に昇格したオブジェクトのサイズ (KB 単位)。|  
  
## <a name="remarks"></a>解説  
 [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)メソッドでは、`Flags``COR_GC_STATS`どの統計を設定するかを指定するために[、構造体](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)のフィールドをCOR_GC_STAT_TYPES列挙体の 1 つ以上の値に設定する必要があります。  
  
 次の表は、この構造体によって提供される統計を[、2](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)つのCOR_GC_STAT_TYPES列挙`COR_GC_COUNTS`値`COR_GC_MEMORYUSAGE`と にマップします。  
  
|COR_GC_COUNTSで指定|COR_GC_MEMORYUSAGEで指定|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 使用例は次のとおりです。  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** を行う  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト構造体](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [自動メモリ管理](../../../standard/automatic-memory-management.md)
- [ガベージ コレクション](../../../standard/garbage-collection/index.md)
