---
title: ICorDebugThread::CreateEval メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2016795e7b2c0588e2bd69e764fb96f7f90b24d0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994072"
---
# <a name="icordebugthreadcreateeval-method"></a>ICorDebugThread::CreateEval メソッド
ICorDebugEval を収集し、この ICorDebugThread の機能を公開するオブジェクトを作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a>パラメーター  
 `ppEval`  
 [out]アドレスへのポインター、`ICorDebugEval`を収集し、このスレッドの機能を公開するオブジェクト。  
  
## <a name="remarks"></a>Remarks  
 評価のオブジェクトは、計算を実行する前に、スレッドで新しいチェーンにプッシュされます。 これは、現在実行中のスレッドで評価が完了するまで計算を中断します。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**[システム要件](../../../../docs/framework/get-started/system-requirements.md)に関するページを参照してください。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET Framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
