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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d335a62545f06a66d4044b59aa9499d3f7ede515
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59208476"
---
# <a name="corgcstats-structure"></a>COR_GC_STATS 構造体
共通言語ランタイム (CLR) のガベージ コレクションのメカニズムについての統計情報を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
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
|`Flags`|フィールドの値を計算し、返される必要がありますを示します。|  
|`ExplicitGCCount`|外部要求によって強制的に実行されたガベージ コレクションの数を示します。|  
|`GenCollectionsTaken`|生成されるたびに実行されたガベージ コレクションの数を示します。|  
|`CommittedKBytes`|すべてのヒープでコミットされたキロバイト単位の合計数。|  
|`ReservedKBytes`|すべてのヒープで予約されているキロバイト数の合計。|  
|`Gen0HeapSizeKBytes`|ジェネレーション 0 ヒープのサイズ。|  
|`Gen1HeapSizeKBytes`|ジェネレーション 1 のヒープのサイズ。|  
|`Gen2HeapSizeKBytes`|ジェネレーション 2 のヒープのサイズ。|  
|`LargeObjectHeapSizeKBytes`|大きなオブジェクト ヒープのサイズ。|  
|`KBytesPromotedFromGen0`|ジェネレーション 0 からジェネレーション 1 に昇格したオブジェクトのサイズ。|  
|`KBytesPromotedFromGen1`|ジェネレーション 1 からジェネレーション 2 に昇格したオブジェクトのサイズ。|  
  
## <a name="remarks"></a>Remarks  
 [Iclrgcmanager::getstats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)メソッドが必要です、`Flags`のフィールド、`COR_GC_STATS`構造体の 1 つまたは複数の値に設定する、 [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)を指定する列挙型統計情報では、設定します。  
  
 次の表は、2 つに、この構造体によって提供される統計[COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)列挙値、`COR_GC_COUNTS`と`COR_GC_MEMORYUSAGE`します。  
  
|COR_GC_COUNTS で指定されました。|COR_GC_MEMORYUSAGE で指定されました。|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 使用状況の例は次のとおりです。  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** GCHost.idl  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト構造体](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Automatic Memory Management](../../../../docs/standard/automatic-memory-management.md)
- [ガベージ コレクション](../../../../docs/standard/garbage-collection/index.md)
