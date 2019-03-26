---
title: ICLRGCManager インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 27899994a048c7000746a2e92516776fd23f8e2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/23/2019
ms.locfileid: "54624393"
---
# <a name="iclrgcmanager-interface"></a>ICLRGCManager インターフェイス
ホストが共通言語ランタイムのガベージ コレクション システムと対話できるようにするメソッドを提供します。  
  
> [!NOTE]
>  以降では、 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]、使用することができます、 [iclrgcmanager 2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)ガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズ値に設定する大きいメソッド`DWORD`はによって課される制限、 [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)メソッド。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Collect メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|指定したジェネレーションのガベージ コレクションを強制します。|  
|[GetStats メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|ガベージ コレクション システムに関する現在の統計情報のセットを取得します。|  
|[SetGCStartupLimits メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|ガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズを設定します。|  
  
## <a name="remarks"></a>Remarks  
 共通言語ランタイム (CLR) で、管理対象のガベージ コレクションのメカニズムを実装する<xref:System.GC>型。 ガベージ コレクションのシステムの詳細については、[ガベージ コレクション](../../../../docs/standard/garbage-collection/index.md)を参照してください。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [自動メモリ管理](../../../../docs/standard/automatic-memory-management.md)
- [COR_GC_STATS 構造体](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [CLR ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [ホスティング](../../../../docs/framework/unmanaged-api/hosting/index.md)
