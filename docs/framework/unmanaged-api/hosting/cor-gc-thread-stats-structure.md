---
title: COR_GC_THREAD_STATS 構造体
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 64e0c466edcd8863244e6ed184c18422b5f66875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178265"
---
# <a name="cor_gc_thread_stats-structure"></a>COR_GC_THREAD_STATS 構造体
ガベージ コレクションに関連するスレッドごとの統計情報を格納します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`PerThreadAllocation`|現在`COR_GC_THREAD_STATS`のインスタンスに関連付けられているスレッドに割り当てられたメモリのバイト数。 この数値は、ジェネレーション ゼロ ガベージ コレクションが発生するたびに 0 にクリアされます。|  
|`Flags`|最新のガベージ コレクションで上位のジェネレーションに昇格されたバイト数。|  
  
## <a name="remarks"></a>解説  
 [型](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md)の出力パラメーターを受け取ります`COR_GC_THREAD_STATS`。  
  
## <a name="requirements"></a>必要条件  
 **:**「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** を行う  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれる  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト構造体](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
