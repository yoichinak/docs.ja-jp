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
ms.openlocfilehash: 6c1d7db8aacaf81d47abd4a9cd972b44f56a3bb1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137521"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut メソッド
この ICorDebugStepper は、それを含むスレッドを1ステップずつ実行し、現在のフレームが呼び出し元のフレームに制御を返すときに完了します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Remarks  
 `StepOut` 操作は、現在のフレームから呼び出し元のフレームに正常に戻った後に完了します。  
  
 アンマネージコード内で `StepOut` が呼び出された場合、現在のフレームがそれを呼び出したマネージコードに戻ると、手順が完了します。  
  
 .NET Framework バージョン2.0 では、STOP_UNMANAGED フラグが設定された `StepOut` を使用しないでください。失敗します。 (ステップ実行のフラグを設定するには、 [ICorDebugStepper:: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)を使用します。)相互運用デバッガーは、ネイティブコード自体にステップアウトする必要があります。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
