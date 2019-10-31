---
title: ICorDebugController::Stop メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugController.Stop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Stop
helpviewer_keywords:
- Stop method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Stop method [.NET Framework debugging]
ms.assetid: c34e79be-a7fb-479e-8dec-d126a4c330e5
topic_type:
- apiref
ms.openlocfilehash: c8c6b40f7a9c63a577140209eed65436040addcb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125384"
---
# <a name="icordebugcontrollerstop-method"></a>ICorDebugController::Stop メソッド
プロセスでマネージコードを実行しているすべてのスレッドで協調停止を実行します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
HRESULT Stop (  
    [in] DWORD dwTimeoutIgnored  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `dwTimeoutIgnored`  
 使用しません。  
  
## <a name="remarks"></a>Remarks  
 `Stop` は、プロセスでマネージコードを実行しているすべてのスレッドで協調停止を実行します。 マネージ専用のデバッグセッションでは、アンマネージスレッドは引き続き実行できます (ただし、マネージコードを呼び出そうとするとブロックされます)。 相互運用機能デバッグセッションでは、アンマネージスレッドも停止します。 現在、`dwTimeoutIgnored` の値は無視され、無限 (-1) として扱われます。 デッドロックが原因で協調停止が失敗した場合、すべてのスレッドが中断され、E_TIMEOUT が返されます。  
  
> [!NOTE]
> `Stop` は、デバッグ API で唯一の同期メソッドです。 `Stop` が S_OK を返した場合、プロセスは停止されます。 リスナーに停止を通知するためのコールバックが付与されていません。 デバッガーは、このプロセスを再開できるようにするために、を[実行](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md)する必要があります。  
  
 デバッガーは停止カウンターを保持します。 カウンターが0になると、コントローラーが再開されます。 `Stop` またはディスパッチされた各コールバックの各呼び出しは、カウンターをインクリメントします。 `ICorDebugController::Continue` を呼び出すたびに、カウンターがデクリメントされます。  
  
## <a name="requirements"></a>［要件］  
 **:** 「[システム要件](../../../../docs/framework/get-started/system-requirements.md)」を参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目
