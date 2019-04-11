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
ms.openlocfilehash: 745917af176de47999737c87833c23df9c75ea7b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080866"
---
# <a name="icordebugeval-interface"></a>ICorDebugEval インターフェイス

デバッガーが、デバッグ中のコードのコンテキスト内でコードを実行できるメソッドを提供します。  
  
## <a name="methods"></a>メソッド  
  
|メソッド|説明|  
|------------|-----------------|  
|[Abort メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)|この計算を中止`ICorDebugEval`オブジェクトが現在実行しています。|  
|[CallFunction メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-callfunction-method.md)|指定した関数の呼び出しを設定します。 (.NET Framework version 2.0 で廃止された; を使用して、 [icordebugeval 2::callparameterizedfunction](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-callparameterizedfunction-method.md)代わりにします)。|  
|[CreateValue メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md)|初期値が 0 または null の"ICorDebugValue"指定した型のオブジェクトへのインターフェイス ポインターを取得します。 (.NET Framework 2.0 で廃止された; を使用して、 [icordebugeval 2::createvaluefortype](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)代わりにします)。|  
|[GetResult メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getresult-method.md)|インターフェイス ポインターを取得、`ICorDebugValue`評価の結果を格納しています。|  
|[GetThread メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-getthread-method.md)|"ICorDebugThread"この評価が実行か、またはそのを実行するには、インターフェイス ポインターを取得します。|  
|[IsActive メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-isactive-method.md)|示す値を取得するかどうかこの`ICorDebugEval`オブジェクトが現在実行中です。|  
|[NewArray メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newarray-method.md)|指定した要素型とディメンションの新しい配列を割り当てます。 (.NET Framework 2.0 で廃止された; を使用して、 [icordebugeval 2::newparameterizedarray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md)代わりにします)。|  
|[NewObject メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobject-method.md)|オブジェクトの新しいインスタンスの割り当てし、指定したコンス トラクター メソッドを呼び出します。 (.NET Framework 2.0 で廃止された; を使用して、 [icordebugeval 2::newparameterizedobject](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobject-method.md)代わりにします)。|  
|[NewObjectNoConstructor メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newobjectnoconstructor-method.md)|コンス トラクター メソッドを呼び出そうとすると、指定した型の新しいオブジェクト インスタンスを割り当てます。 (.NET Framework 2.0 で廃止された; を使用して、 [icordebugeval 2::newparameterizedobjectnoconstructor](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedobjectnoconstructor-method.md)代わりにします)。|  
|[NewString メソッド](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-newstring-method.md)|指定した内容を含む新しい文字列オブジェクトを割り当てます。|  
  
## <a name="remarks"></a>Remarks  
 `ICorDebugEval`評価を実行するために使用する特定のスレッドのコンテキストでオブジェクトを作成します。 すべてのオブジェクトと特定の評価で使用される型は、同じアプリケーション ドメイン内に存在する必要があります。 そのアプリケーション ドメインでは、スレッドの現在のアプリケーション ドメインと同じである必要がありません。 評価版ソフトウェアは、入れ子にすることができます。  
  
 デバッガーの呼び出しまでの評価の操作を実行しないで[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)、し、受信、 [icordebugmanagedcallback::evalcomplete](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-evalcomplete-method.md)コールバック。 他のスレッドの実行を許可せず、評価の機能を使用する必要がある場合は、いずれかを使用して、スレッドを中断[icordebugcontroller::setallthreadsdebugstate](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md)または[icordebugcontroller::stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md)呼び出す前に[icordebugcontroller::continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)します。  
  
 評価が進行中の場合は、ユーザー コードが実行されて、ため、クラスの読み込みやブレークポイントなどのデバッグ イベントは発生します。 デバッガーは、コールバックは、これらのイベントは、通常どおりに表示されます。 評価の状態は、通常のプログラムの状態の検査の一部として表示されます。 スタックのチェーンを`CHAIN_FUNC_EVAL`チェーン ("CorDebugStepReason"列挙型を参照してください、 [icordebugchain::getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)メソッド)。 完全なデバッガー API は引き続き通常どおりに動作します。  
  
 デッドロック状態または無限ループの状況が発生した場合、ユーザー コードが完了しない可能性があります。 このような場合は、呼び出す必要がある[icordebugeval::abort](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-abort-method.md)プログラムを再開する前にします。  
  
> [!NOTE]
>  このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン: ** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目

- [デバッグのインターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
