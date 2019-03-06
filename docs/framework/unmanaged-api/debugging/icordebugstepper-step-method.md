---
title: ICorDebugStepper::Step メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 444390622ca68244661b91dc85814b05556b12a2
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493025"
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step メソッド
この icordebugstepper その格納のスレッドと、必要に応じてをシングル ステップ実行するスレッド内で呼び出される関数をシングル ステップ実行を続行します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `bStepIn`  
 [in]設定`true`スレッド内で呼び出される関数にステップ インします。 設定`false`をステップ オーバー関数。  
  
## <a name="remarks"></a>Remarks  
 共通言語ランタイムがこのステッパのフレーム内に次のマネージ命令を実行するときに、手順を完了します。 場合`Step`は、ステッパに対して呼び出すと、マネージ コードのではない、スレッドがマネージ コードの次の命令が実行されたときに、手順は完了します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
