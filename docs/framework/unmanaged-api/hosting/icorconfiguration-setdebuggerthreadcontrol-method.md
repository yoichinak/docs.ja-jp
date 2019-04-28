---
title: ICorConfiguration::SetDebuggerThreadControl メソッド
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fc141cbebe08f8d0974788409d5aef0f68d2878
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763257"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a>ICorConfiguration::SetDebuggerThreadControl メソッド
デバッグ サービスが共通言語ランタイム (CLR) スレッドがブロックまたはブロック解除されたデバッグときに呼び出すコールバック インターフェイスを設定します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pDebuggerThreadControl`  
 [in]ポインター、 [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)ブロックおよびブロック解除スレッドのデバッグ サービスでのホストに通知するオブジェクト。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [ICorConfiguration インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
