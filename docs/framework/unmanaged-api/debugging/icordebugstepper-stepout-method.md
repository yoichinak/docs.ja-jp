---
title: ICorDebugStepper::StepOut メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36a33b74a692761d772a888ce918aa28a2d92678
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760558"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut メソッド
Icordebugstepper シングル ステップ実行し、その格納のスレッドでは、現在のフレームが呼び出し元のフレームにコントロールを返されるときに完了するを表示します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Remarks  
 A`StepOut`呼び出し元のフレームに、現在のフレームから正常に戻った後操作が完了します。  
  
 場合`StepOut`時に呼び出される、現在のフレームがそれを呼び出したマネージ コードに返されるときに、アンマネージ コードでの手順を行います。  
  
 .NET Framework version 2.0 では使用しません`StepOut`STOP_UNMANAGED フラグ セット失敗します。 (使用[icordebugstepper::setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)ステップ実行するためのフラグを設定します)。デバッガーの相互運用する必要があります ステップ アウトをネイティブ コードに自体。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
