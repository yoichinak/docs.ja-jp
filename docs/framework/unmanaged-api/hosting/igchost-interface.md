---
title: IGCHost インターフェイス
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d3f588bfc9799ed4591114b28d081ab417678b1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914797"
---
# <a name="igchost-interface"></a>IGCHost インターフェイス
ガベージコレクションシステムに関する情報を取得し、ガベージコレクションのいくつかの側面を制御するためのメソッドを提供します。  
  
> [!NOTE]
> .NET Framework 4.5 以降では、 [IGCHost2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)メソッドを使用してガベージコレクションセグメントのサイズを設定できます。ガベージコレクションシステムのジェネレーション0の最大サイズは、 `DWORD`[SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)メソッドによって課される制限。  
  
> [!NOTE]
> このインターフェイスは、専門家による使用のみを目的としています。 不適切に使用した場合、アプリケーションのパフォーマンスに影響を与える可能性があります。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Collect メソッド](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|現在のガベージコレクションの状態に関係なく、指定したジェネレーションに対して強制的にコレクションを実行します。|  
|[GetStats メソッド](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|ガベージコレクションシステムの現在の状態の統計を取得します。|  
|[GetThreadStats メソッド](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|ガベージコレクションのスレッドごとの統計を取得します。|  
|[SetGCStartupLimits メソッド](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|ジェネレーション0のセグメントサイズと最大サイズを設定します。|  
|[SetVirtualMemLimit メソッド](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|ランタイムの仮想メモリの最大サイズを設定します。|  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** GCHost、GCHost  
  
 **ライブラリ**Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost コクラス](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
