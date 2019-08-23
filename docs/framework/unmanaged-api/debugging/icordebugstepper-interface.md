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
ms.openlocfilehash: c57b13b05522614ff066b93cb9f6a437cb340576
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962694"
---
# <a name="icordebugstepper-interface"></a>ICorDebugStepper インターフェイス
デバッガーが実行するコード実行内のステップを表します。コマンドの発行から完了までの間は識別子として機能します。これを使用するとステップをキャンセルできます。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Deactivate メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md)|これ`ICorDebugStepper`により、受信した最後のステップコマンドがキャンセルされます。|  
|[IsActive メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-isactive-method.md)|この`ICorDebugStepper`が現在ステップを実行しているかどうかを示す値を取得します。|  
|[SetInterceptMask メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setinterceptmask-method.md)|ステップインするコードの種類を指定する CorDebugIntercept 値を設定します。|  
|[SetRangeIL メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md)|[ICorDebugStepper:: StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)を呼び出すかどうかを示す値を設定します。これは、ネイティブコードまたはステップスルー中のメソッドの Microsoft 中間言語 (MSIL) コードを基準として、引数の値を渡します。|  
|[SetUnmappedStopMask メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md)|実行が停止するマップされていないコードの種類を指定する CorDebugUnmappedStop 値を設定します。|  
|[Step メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md)|これに`ICorDebugStepper`より、このが格納しているスレッドを1ステップずつ実行します。また、必要に応じて、スレッド内で呼び出される関数を使用したシングルステップ実行を継続します。|  
|[StepOut メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-stepout-method.md)|これに`ICorDebugStepper`より、このが格納しているスレッドを1ステップずつ実行し、現在のフレームが呼び出し元のフレームに制御を返すときに完了します。|  
|[StepRange メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)|これに`ICorDebugStepper`より、このが格納しているスレッドを1ステップずつ実行し、指定した範囲の最後のコードに到達したときにを返します。|  
  
## <a name="remarks"></a>Remarks  
 この`ICorDebugStepper`インターフェイスは、次の目的で機能します。  
  
- 発行されたステップコマンドとそのコマンドの完了の間の識別子として機能します。  
  
- これは、実行可能なすべてのステップをカプセル化するための中心的なインターフェイスを提供します。  
  
- これにより、ステップ実行操作を途中で取り消すことができます。  
  
 スレッドごとに複数のステッパが存在する場合があります。 たとえば、関数をステップオーバーしている間にブレークポイントがヒットし、ユーザーがその関数内で新しいステップ実行操作を開始する場合があります。 この状況をどのように処理するかは、デバッガーによって決定されます。 デバッガーでは、元のステップ実行操作をキャンセルするか、2つの操作を入れ子にすることができます。 インターフェイス`ICorDebugStepper`では、両方の選択肢がサポートされています。  
  
 共通言語ランタイム (CLR) がクロススレッドでマーシャリングされた呼び出しを行う場合、ステッパはスレッド間で移行される可能性があります。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
