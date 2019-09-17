---
title: ICorDebugEval インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval
helpviewer_keywords:
- ICorDebugEval interface [.NET Framework debugging]
ms.assetid: 3a5c9815-832d-47e1-b7f7-bbba135d7cf1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cfd29067f819ba69305f7ae8620729cd443915a0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931942"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval インターフェイス

デバッガーが、デバッグ中のコードのコンテキスト内でコードを実行できるメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Abort メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|この`ICorDebugEval`オブジェクトが現在実行している計算を中止します。|  
|[CallFunction メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|指定された関数の呼び出しを設定します。 (.NET Framework バージョン2.0 で廃止されました。代わりに[ICorDebugEval2:: CallParameterizedFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)を使用してください。)|  
|[CreateValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|初期値0または null を指定して、指定した型の "ICorDebugValue" オブジェクトへのインターフェイスポインターを取得します。 (.NET Framework 2.0 で廃止されました。代わりに[ICorDebugEval2:: CreateValueForType](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)を使用してください。)|  
|[GetResult メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|評価の結果を格納し`ICorDebugValue`ているへのインターフェイスポインターを取得します。|  
|[GetThread メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|この評価が実行されているか実行される "表示スレッド" へのインターフェイスポインターを取得します。|  
|[IsActive メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|この`ICorDebugEval`オブジェクトが現在実行中かどうかを示す値を取得します。|  
|[NewArray メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|指定した要素の型と次元の新しい配列を割り当てます。 (.NET Framework 2.0 で廃止されました。代わりに[ICorDebugEval2:: NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)を使用してください。)|  
|[NewObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|新しいオブジェクトインスタンスを割り当て、指定したコンストラクターメソッドを呼び出します。 (.NET Framework 2.0 で廃止されました。代わりに[ICorDebugEval2:: NewParameterizedObject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)を使用してください。)|  
|[NewObjectNoConstructor メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|コンストラクターメソッドを呼び出さずに、指定した型の新しいオブジェクトインスタンスを割り当てます。 (.NET Framework 2.0 で廃止されました。代わりに[ICorDebugEval2:: NewParameterizedObjectNoConstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)を使用してください。)|  
|[NewString メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|指定された内容を持つ新しい文字列オブジェクトを割り当てます。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugEval`オブジェクトは、評価を実行するために使用される特定のスレッドのコンテキストで作成されます。 特定の評価で使用されるすべてのオブジェクトと型は、同じアプリケーションドメイン内に存在する必要があります。 このアプリケーションドメインは、スレッドの現在のアプリケーションドメインと同じである必要はありません。 評価は入れ子にすることができます。  
  
 評価の操作が完了しないのは、デバッガーが "を実行してい[ます:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)" というメッセージを呼び出し、次に、"は、" は、"は、" のようなコール[バック](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)を受け取ります。 他のスレッドの実行を許可せずに評価機能を使用する必要がある場合は、[ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) を呼び出す前に [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) または [ICorDebugController::Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md) のいずれかを使用してスレッドを中断します。  
  
 評価の進行中にユーザーコードが実行されているので、クラスの読み込みやブレークポイントなどのデバッグイベントが発生する可能性があります。 デバッガーは、これらのイベントに対して通常どおりコールバックを受け取ります。 評価の状態は、通常のプログラムの状態の検査の一部として表示されます。 スタックチェーンはチェーンに`CHAIN_FUNC_EVAL`なります ("cordebugstepreason" 列挙型と、「の場合は、" [: getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) " メソッドを参照してください)。 完全なデバッガー API は通常どおりに動作します。  
  
 デッドロックまたは無限ループの状態が発生した場合、ユーザーコードが完全に完了することはありません。 このような場合は、プログラムを再開する前に、「いいね! [: Abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md) 」を呼び出す必要があります。  
  
> [!NOTE]
> このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **・** [システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug .idl、CorDebug. h  
  
 **ライブラリ**CorGuids .lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
