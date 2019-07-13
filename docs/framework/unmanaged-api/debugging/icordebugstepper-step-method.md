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
ms.openlocfilehash: 9d0f601c4b454b55edc5fa25eb2ee33d491009b9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760571"
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step メソッド
この icordebugstepper その格納のスレッドと、必要に応じてをシングル ステップ実行するスレッド内で呼び出される関数をシングル ステップ実行を続行します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
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
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
