---
title: ICorConfiguration::AddDebuggerSpecialThread メソッド
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 067765fbf500b2d20d84273d8df70c8e05a6ddc4
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485901"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a>ICorConfiguration::AddDebuggerSpecialThread メソッド
デバッグ サービスを特定のスレッドがデバッガーがマネージまたはアンマネージ デバッグ シナリオ中に停止したアプリケーションの実行を続行できることを示します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwSpecialThreadId`  
 [in]実行の継続を許可するかのスレッドの ID。  
  
## <a name="remarks"></a>Remarks  
 指定したスレッドをマネージ コードを実行したり任意の方法でランタイムに許可されていません。 このようなスレッドの例は、従来のスクリプト デバッガーをサポートするために、プロセスのスレッドになります。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll でリソースとして含まれます  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目
- [ICorConfiguration インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
