---
title: ICorConfiguration インターフェイス
ms.date: 03/30/2017
api_name:
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b24e278b3449d0e17377495cef0f445c1ebed734
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149813"
---
# <a name="icorconfiguration-interface"></a>ICorConfiguration インターフェイス
共通言語ランタイム (CLR) を構成するためのメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[AddDebuggerSpecialThread メソッド](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|デバッグ サービスを特定のスレッドがデバッガーがマネージまたはアンマネージ デバッグ シナリオ中に停止したアプリケーションの実行を続行できることを示します。|  
|[SetDebuggerThreadControl メソッド](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|デバッグ サービスは CLR のスレッドをブロックまたはブロック解除されたデバッグときに呼び出すコールバック インターフェイスを設定します。|  
|[SetGCHostControl メソッド](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|仮想メモリの制限を変更するホストに要求、ガベージ コレクターで使用されるコールバック インターフェイスを設定します。|  
|[SetGCThreadControl メソッド](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|それ以外の場合、ガベージ コレクションのブロックされる非ランタイム タスクのスレッドをスケジュールするためのコールバック インターフェイスを設定します。|  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CorRuntimeHost コクラス](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
