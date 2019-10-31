---
title: ICorDebugFunction3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: fc50fd7180aaf5c1cff2147268d34921eec39e8f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137764"
---
# <a name="icordebugfunction3-interface"></a>ICorDebugFunction3 インターフェイス
[.NET Framework 4.5.2 以降のバージョンでのみでサポート]  
  
 により、再 Jit 要求からコードへのアクセスを提供するために、の関数インターフェイスを論理的に拡張します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[GetActiveReJitRequestILCode メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|アクティブな ReJIT 要求から IL を含む、[コード](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)へのインターフェイスポインターを取得します。|  
  
## <a name="remarks"></a>Remarks  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
- [ReJIT: ハウツーガイド](https://blogs.msdn.microsoft.com/davbr/2011/10/12/rejit-a-how-to-guide/)
