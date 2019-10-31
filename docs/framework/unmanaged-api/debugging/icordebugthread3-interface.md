---
title: ICorDebugThread3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
ms.openlocfilehash: 7cddf860f044e8493a0fdf6023b2853ac16c5b14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137503"
---
# <a name="icordebugthread3-interface"></a>ICorDebugThread3 インターフェイス
とそれに対応するインターフェイス[へのエントリ](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)ポイントを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[CreateStackWalk メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|スタックをアンワインドするスレッドに対し[て、このオブジェクトを](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)作成します。|  
|[GetActiveInternalFrames メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|スタック上の内部フレーム ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) の配列を返します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugThread3` は、のように、のような論理上の拡張機能です。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [デバッグ](../../../../docs/framework/unmanaged-api/debugging/index.md)
