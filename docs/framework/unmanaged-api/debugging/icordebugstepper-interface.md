---
title: ICorDebugStepper インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper
helpviewer_keywords:
- ICorDebugStepper interface [.NET Framework debugging]
ms.assetid: ed8364eb-f01b-46f6-b5e3-5dda9cae2dfe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f83b9796bb692ce234a03c596387960bd879ebf3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763738"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper インターフェイス
デバッガーが実行するコード実行内のステップを表します。コマンドの発行から完了までの間は識別子として機能します。これを使用するとステップをキャンセルできます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Deactivate メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|この原因`ICorDebugStepper`を受信した最後の手順のコマンドをキャンセルします。|  
|[IsActive メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|示す値を取得するかどうかこの`ICorDebugStepper`ステップが現在実行します。|  
|[SetInterceptMask メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|ステップ インはコードの種類を示す CorDebugIntercept 値を設定します。|  
|[SetRangeIL メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|示す値を設定するかどうかを呼び出す[icordebugstepper::steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)またはスルーされるメソッドの Microsoft intermediate language (MSIL) コードにネイティブ コードへの相対引数の値を渡します。|  
|[SetUnmappedStopMask メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|マップされていないコードが実行を中断の種類を示す CorDebugUnmappedStop 値を設定します。|  
|[Step メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|この原因`ICorDebugStepper`その格納のスレッドと、必要に応じてをシングル ステップ実行するスレッド内で呼び出される関数をシングル ステップ実行を続行します。|  
|[StepOut メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|この原因`ICorDebugStepper`その格納のスレッドをシングル ステップ実行して、完了時に、現在のフレームが呼び出し元のフレームにコントロールを返します。|  
|[StepRange メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|この原因`ICorDebugStepper`シングル ステップの場合に返されるとその格納のスレッドを指定した範囲の最後のタスクを超えるコードに到達します。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugStepper`インターフェイスは、次の目的で機能します。  
  
- ステップ コマンドが発行されますが、そのコマンドの完了の間で識別子として機能します。  
  
- 実行できるすべてのステップ実行をカプセル化する中央のインターフェイスを提供します。  
  
- ステップ実行操作の途中でキャンセルする方法を提供します。  
  
 スレッドごとの 1 つ以上のステッパことができます。 たとえば、ステップ オーバー関数の場合、中に、ブレークポイントにヒットする可能性があり、ユーザーが関数の内部での新しいステップ実行操作を開始することがあります。 この状況に対処する方法については、デバッガーの責任です。 デバッガーは元のステップ実行操作をキャンセルするか、2 つの操作を入れ子にします。 `ICorDebugStepper`インターフェイスは、2 つの選択肢をサポートしています。  
  
 共通言語ランタイム (CLR) が、マーシャ リングされたクロス シングル スレッドの呼び出しを行った場合、ステッパをスレッド間で移行可能性があります。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
