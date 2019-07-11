---
title: ICorDebugStepper::StepRange メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7e1ace501bf5de741ea110fe4d3bb4bc44843bf8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760526"
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange メソッド
Icordebugstepper シングル ステップ実行し、その格納のスレッドでは、指定した範囲の最後のタスクを超えるコードに達した場合に返されるを表示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `bStepIn`  
 [in]設定`true`スレッド内で呼び出される関数にステップ インします。 設定`false`をステップ オーバー関数。  
  
 `ranges`  
 [in]COR_DEBUG_STEP_RANGE 構造体の範囲を指定の配列。  
  
 `cRangeCount`  
 [in] `ranges` 配列のサイズ。  
  
## <a name="remarks"></a>Remarks  
 `StepRange`のような方法は、機能、 [icordebugstepper::step](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)メソッドが特定の範囲外のコードまでに完了しないこと以外に到達します。  
  
 これは、一度に 1 つの命令をステップ実行するよりも効率的で指定できます。 範囲は、ステッパのフレームの先頭からのオフセットのペアのリストとして指定します。  
  
 範囲では、メソッドの Microsoft intermediate language (MSIL) コードに対して相対的です。 呼び出す[icordebugstepper::setrangeil](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)で`false`メソッドのネイティブ コードの基準とした範囲にします。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
