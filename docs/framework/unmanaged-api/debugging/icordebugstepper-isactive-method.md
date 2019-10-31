---
title: ICorDebugStepper::IsActive メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
ms.openlocfilehash: a242764710d92e81e8089bc2919734bfac4bcdb2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137571"
---
# <a name="icordebugstepperisactive-method"></a>ICorDebugStepper::IsActive メソッド
この ICorDebugStepper が現在ステップを実行しているかどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pbActive`  
 入出力ステッパが現在ステップを実行している場合は `true` を返します。それ以外の場合は `false`を返します。  
  
## <a name="remarks"></a>Remarks  
 すべてのステップアクションは、デバッガーが完了していない場合は、次のように[実行](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)されます。この呼び出しは、ステッパを自動的に非アクティブ化します。 [ICorDebugStepper::D eactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)を呼び出してコールバック条件に到達する前に、ステッパを途中で非アクティブにすることもできます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
