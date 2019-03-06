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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4166b63e0bb0ae276c48abb961e381809cc9792
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471421"
---
# <a name="icordebugstepperisactive-method"></a>ICorDebugStepper::IsActive メソッド
この ICorDebugStepper が現在の手順を実行中かどうかを示す値を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `pbActive`  
 [out]返します`true`ステッパでは、ステップ; 現在実行している場合を返しますそれ以外の場合、`false`します。  
  
## <a name="remarks"></a>Remarks  
 デバッガーが受信するまで、すべてのステップ アクションがアクティブなまま、 [icordebugmanagedcallback::stepcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md)呼び出すには、ステッパを自動的に非アクティブ化します。 ステッパ可能性がありますも非アクティブ化処理の途中で呼び出すことによって[icordebugstepper::deactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)状態に達すると、コールバックの前にします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
