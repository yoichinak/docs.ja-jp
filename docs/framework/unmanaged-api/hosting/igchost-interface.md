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
ms.openlocfilehash: 9d6c9d22f4e50c21e2f41b7efd402907ff5843db
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805213"
---
# <a name="igchost-interface"></a>IGCHost インターフェイス
ガベージコレクションシステムに関する情報を取得し、ガベージコレクションのいくつかの側面を制御するためのメソッドを提供します。  
  
> [!NOTE]
> .NET Framework 4.5 以降では、 [IGCHost2:: SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)メソッドを使用して、ガベージコレクションセグメントのサイズと、ガベージコレクションシステムのジェネレーション0の最大サイズを、 `DWORD` [SetGCStartupLimits](igchost-setgcstartuplimits-method.md)メソッドによって設定された制限を超える値に設定できます。  
  
> [!NOTE]
> このインターフェイスは、専門家による使用のみを目的としています。 不適切に使用した場合、アプリケーションのパフォーマンスに影響を与える可能性があります。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Collect メソッド](igchost-collect-method.md)|現在のガベージコレクションの状態に関係なく、指定したジェネレーションに対して強制的にコレクションを実行します。|  
|[GetStats メソッド](igchost-getstats-method.md)|ガベージコレクションシステムの現在の状態の統計を取得します。|  
|[GetThreadStats メソッド](igchost-getthreadstats-method.md)|ガベージコレクションのスレッドごとの統計を取得します。|  
|[SetGCStartupLimits メソッド](igchost-setgcstartuplimits-method.md)|ジェネレーション0のセグメントサイズと最大サイズを設定します。|  
|[SetVirtualMemLimit メソッド](igchost-setvirtualmemlimit-method.md)|ランタイムの仮想メモリの最大サイズを設定します。|  
  
## <a name="requirements"></a>要件  
 **:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** GCHost、GCHost  
  
 **ライブラリ:** Mscoree.dll にリソースとして含まれています  
  
 **.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](hosting-interfaces.md)
- [CorRuntimeHost コクラス](corruntimehost-coclass.md)
